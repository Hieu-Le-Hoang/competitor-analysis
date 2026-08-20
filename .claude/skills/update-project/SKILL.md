---
name: update-project
description: >
  Cập nhật thông tin MỚI từ các nguồn (source) đã khai báo của project đang mở — crawl/refresh
  data từ Google Sheets, GitHub, Dataverse, Azure/GCP billing, HTTP... rồi ghi vào file trong project.
  Nguồn khác nhau theo từng project, khai báo trong sources.yaml (lazy — chưa có thì hỏi user).
  Trigger: "update project", "update-project", "cập nhật project", "refresh data project",
  "crawl data dự án", "kéo data mới", "lấy data mới nhất", "sync nguồn project", "cập nhật billing",
  "cập nhật sheet project", "làm mới dữ liệu project", "pull data project".
  Áp dụng khi: cần refresh dữ liệu từ các nguồn ngoài của project (bất cứ lúc nào), KHÔNG phải để
  viết tài liệu project (đó là docs-project).
---

# Skill: update-project

## Mục tiêu

Kéo thông tin **mới nhất** từ các nguồn của project đang mở về, ghi vào đúng file đích.
Skill là **conductor** — logic điều phối (detect / confirm / report) cố định; *nguồn* thì đọc từ
`sources.yaml` của project (mỗi project một kiểu). Chưa khai nguồn → hỏi user rồi lưu lại.

> Phân biệt: **update-project = refresh DATA từ nguồn ngoài**. `docs-project` = viết PROJECT.md/log.md.
> Hai skill khác nhau, không thay thế nhau.

## How It Works

```
  "update project" (chạy trong project)
        │
   [1] Detect project root ── đứng workspace nào update workspace đó
        │
   [2] Load .claude/skills/update-project/sources.yaml
        ├─ TRỐNG / chưa có ─► HỎI user "project này update từ nguồn nào?"
        │                       -> ghi sources.yaml -> lần sau khỏi hỏi
        └─ CÓ nguồn ─────────► tiếp [3]
        │
   [3] (tùy chọn) lọc nguồn ── user nói "update <tên>" -> chỉ chạy nguồn đó
        │
   [4] Với MỖI source: resolve key (§8) -> dispatch fetcher theo type -> fetch ra temp
        │
   [5] Diff vs file đích -> CONFIRM ghi đè (§4) -> ghi dest (native tool)
        │
   [6] Report bảng: nguồn / trạng thái / dòng ghi / dest
```

## ALWAYS → SUPERCHARGED

```
ALWAYS (không cần MCP/CLI): nguồn type gsheet/github/http/excel — fetch bằng skill read-* /
   WebFetch + input user. Không có key vẫn hỏi user cung cấp locator, không văng lỗi.
──────────────────────────────────────────────────────────────
SUPERCHARGED (có connector): type dataverse (MCP), azure/gcp billing (az/gcloud/bq CLI) —
   kéo được nguồn cloud, output đầy đủ hơn.
```

## sources.yaml — schema

File: `<project>/.claude/skills/update-project/sources.yaml`

```yaml
sources:
  - name: process-catalog     # id ngắn, dùng để lọc "update process-catalog"
    type: gsheet              # chọn fetcher (bảng dưới)
    source: "<gsheet-url>"    # locator: URL / ID / path / query / cmd
    dest: kb/processes/       # ghi vào đâu (relative từ project root)
    mode: overwrite           # overwrite (default) | append
    # auth: <tên-key>         # optional — TÊN key trong settings.json, KHÔNG paste key
```

### Fetcher registry (type -> cách fetch)

| type | Fetcher (tái dùng) | Ghi chú |
|------|--------------------|---------|
| `gsheet` | skill `read-gsheet` | truyền `source` (URL) + `mode` process nếu cần |
| `github` | skill `read-github` | repo/file/issue/PR URL |
| `excel` | skill `read-excel` | file `.xlsx/.csv/.docx` local |
| `http` | `WebFetch` | trang web / API public |
| `dataverse` | MCP `dataverse` | `source` = FetchXML / OData query |
| `script` | `scripts/<file>.ps1` trong project | nguồn cần logic riêng: Azure (`az`), GCP (`gcloud`/`bq`) |

> Nguồn chưa có fetcher chuẩn (Azure/GCP billing...) → dùng `type: script`, `source` trỏ tới script
> trong `<project>/.claude/skills/update-project/scripts/`. Script tự lo auth + ghi dest.

## Output Format

### Khi sources.yaml trống — hỏi scaffold

```
📥 update-project: project này chưa khai nguồn nào.
Cho em biết cần update từ nguồn gì? (mỗi nguồn: loại + locator + ghi vào đâu)
Ví dụ:
  - Google Sheet process  -> ghi kb/processes/
  - Azure billing (az CLI) -> ghi data/azure-billing.json
```

### Report sau khi chạy

```markdown
✅ update-project — <project>
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
| Nguồn            | Type      | Trạng thái | Ghi vào              |
|------------------|-----------|-----------|----------------------|
| process-catalog  | gsheet    | ✅ 128 dòng | kb/processes/        |
| azure-billing    | script    | ✅ cập nhật | data/azure-billing.json |
| gcp-billing      | http      | ⏭️ skip (user hủy) | -             |
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Chạy `docs-project` để log lại phiên nếu cần.
```

## Workflow — Thực hiện tuần tự

### Bước 1 — Detect project root
Đứng workspace nào update workspace đó. Không rõ (session nhiều workspace) → **hỏi**, không đoán.

### Bước 2 — Load sources.yaml
Đọc `<project>/.claude/skills/update-project/sources.yaml`.
- **Chưa có / `sources: []`** → chạy scaffold: hỏi user từng nguồn (name / type / source / dest),
  ghi `sources.yaml` bằng `Write` (native, UTF-8). Xác nhận lại rồi mới fetch.
- **Có nguồn** → sang Bước 3.

### Bước 3 — Lọc nguồn (tùy chọn)
User nói "update <tên>" → chỉ chạy nguồn khớp `name`. Không nêu → chạy hết.

### Bước 4 — Fetch từng nguồn
Với mỗi source:
1. **Resolve auth** theo §8: cần key → tra `~/.claude/settings.json` (`env`) + `~/.claude.json`
   (`mcpServers`). Thiếu → báo user bổ sung, **KHÔNG paste key vào chat/recipe**.
2. **Dispatch fetcher** theo `type` (bảng registry) → fetch ra file temp (scratchpad).
3. **Diff** vs file đích hiện có → tóm tắt thay đổi (bao nhiêu dòng/record mới).

### Bước 5 — Confirm & ghi
- Ghi đè data = thao tác không undo → **confirm trước** (§4):
  *"Anh đồng ý cho em ghi đè [dest] từ nguồn [name] không?"*
- User đồng ý → ghi bằng **native tool** (Write/Edit) cho text; `mode: append` thì nối, không xóa cũ.
- User hủy → skip nguồn đó, đánh dấu ⏭️ trong report.

### Bước 6 — Report
In bảng report (Output Format). Gợi ý chạy `docs-project` nếu phiên cần log.

## Lưu ý quan trọng
- **Security (§4)**: mọi ghi đè phải confirm; key lấy theo §8, không lộ ra chat.
- **Encoding (§7)**: ghi file text tiếng Việt bằng Write/Edit — KHÔNG PowerShell redirect.
- Chỉ làm trong project đang mở; không đụng project khác.
- Nguồn lỗi (URL chết, key thiếu, CLI chưa login) → báo thẳng nguồn nào fail, không giả vờ xong.
- Không tự chạy git — commit/push do user quyết sau khi xem data mới.

## Related Skills
- `read-gsheet` / `read-github` / `read-excel` — fetcher tái dùng cho nguồn tương ứng.
- `docs-project` — sau khi refresh data, log lại phiên / update PROJECT.md.
- `init-project` — chính nó stamp skill này vào project lúc khởi tạo.
