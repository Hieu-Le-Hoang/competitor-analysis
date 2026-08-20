# CLAUDE.md — Quy tắc hành vi AI · Nghiên cứu Đối thủ

> **Rule chung** (giao tiếp, planning, security, encoding...)
> nằm ở **global rules** (`~/.claude/CLAUDE.md`).
> File này chỉ chứa rule **đặc thù cho project research/tài liệu hóa**.

> Áp dụng cho workspace **tài liệu hóa & phân tích** — không phải code project.
> Project này **không có SSoT tập trung** — nguồn khai theo từng file ở section `## Nguồn` (xem §2).

**Đánh đổi:** Ưu tiên chính xác hơn tốc độ.
Tài liệu sai còn nguy hiểm hơn không có tài liệu.

---

## §1 · Suy nghĩ trước khi viết

**Đừng đoán mò. Đừng giấu sự mơ hồ. Tài liệu AI tạo ra phải traceable.**

Trước khi tạo hoặc chỉnh sửa tài liệu:
- Nêu rõ assumptions. Nếu không chắc — hỏi.
- Nếu có nhiều cách hiểu — trình bày tất cả, đừng tự chọn im lặng.
- Nếu điều gì đó không rõ — dừng lại. Chỉ rõ điểm mơ hồ. Hỏi.
- **Không suy diễn** nội dung nếu chưa đọc source gốc.
- **Không paraphrase** thông tin kỹ thuật quan trọng — quote trực tiếp và link source.

> **Anti-hallucination rule (bắt buộc):** Nếu không tìm được source cho một claim → phải nói rõ:
> *"Không tìm được source xác nhận điều này — cần verify thêm."*
> **KHÔNG** tự tạo nội dung nghe có vẻ đúng để lấp chỗ trống.

---

## §2 · Source Attribution — Truy xuất nguồn gốc

**Với nội dung có nguồn thì nên khai báo rõ để traceable.**

| Trường hợp | `owner:` | `source:` |
|-----------|----------|-----------| 
| Nội dung đọc từ tài liệu bên ngoài | Tên tác giả gốc | Tên file / URL cụ thể |
| AI tổng hợp từ nhiều file | Owner project | Liệt kê các file nguồn |
| Team tự tạo, không từ source nào | Owner project | `internal` |

Nội dung lấy từ nguồn ngoài mà thiếu `source:` → coi như chưa hoàn chỉnh, ghi vào `drift_report.md` để xử lý.

Với claim kỹ thuật quan trọng trong body file:
```markdown
<!-- source: <tên file gốc hoặc URL> · <ngày truy cập/commit> -->
```

---

## §3 · Uncertainty Markers — Mức độ tin cậy của thông tin

**Mọi claim trong tài liệu phải được gắn mức độ tin cậy khi không có source trực tiếp.**

| Marker | Ý nghĩa | Khi dùng |
|--------|---------|----------|
| `[VERIFIED]` | Có source trực tiếp, trích dẫn được | Default — không cần ghi nếu có source link rõ |
| `[INFERRED]` | Suy luận hợp lý từ source, không phải trích dẫn trực tiếp | Khi diễn giải hoặc mở rộng từ source |
| `[UNVERIFIED]` | Chưa tìm được source xác nhận | Bắt buộc dùng, KHÔNG để trống hoặc viết như đã verified |
| `[OUTDATED?]` | Thông tin có thể đã thay đổi theo thời gian | Dữ liệu kỹ thuật, pricing, version number... |
| `[CONFLICT]` | Mâu thuẫn giữa các source | Khi 2+ source nói khác nhau — trình bày cả hai, chờ clarify |

Ví dụ dùng trong body file:
```markdown
Hệ thống hỗ trợ tối đa 10,000 concurrent users. `[UNVERIFIED — cần confirm với infra team]`

Module billing dùng Stripe SDK v3. `[OUTDATED? — spec viết 2024, cần check version hiện tại]`
```

---

## §4 · Thực thi hướng mục tiêu

**Định nghĩa tiêu chí hoàn thành trước khi bắt đầu.**

Với task nhiều bước, trình bày kế hoạch ngắn:

```
1. [Bước] → verify: [điều kiện kiểm tra]
2. [Bước] → verify: [điều kiện kiểm tra]
3. [Bước] → verify: [điều kiện kiểm tra]
```

Tiêu chí rõ ràng → AI tự lặp độc lập đến khi xong.
Tiêu chí mơ hồ → hỏi trước, không đoán.

## §5 · Frontmatter & tra cứu cho file .md

**Frontmatter chỉ có 2 field. Không thêm field mới mà chưa sửa mục này.**

```yaml
---
title: "Tên file — nói rõ nó là cái gì"
description: Một câu mô tả file này dùng để làm gì.
---
```

- **`description` phải PHÂN BIỆT được file** — chứa tên nguồn/chủ đề riêng. Mô tả dùng chung cho nhiều file = vô giá trị, thà bỏ trống.
- **Mô tả MỤC ĐÍCH, không mô tả TRẠNG THÁI.** Hai field này viết một lần lúc tạo file và gần như không ai sửa lại, nên chỉ được chứa thứ bất biến. Con số, kết luận, "đã/chưa" → viết trong **body**, nơi chúng được sửa cùng lúc nội dung đổi.
- **BỎ HẲN, không thêm lại:** `type` · `tags` · `status` · `stale_after` · `sources` · `owner` · `timestamp` · `[[wikilink]]`. File nháp / đã bị thay thế → ghi thẳng một dòng trong body ngay dưới H1.
- Value chứa dấu `: ` **phải quote** — `title: 'Phần A: bối cảnh'`. Không quote sẽ vỡ YAML.
- **Ngoại lệ không cần frontmatter:** `PROJECT.md`, `index.md`, `log.md`, `README.md`.

**Riêng research — section `## Nguồn` cuối file là BẮT BUỘC** (xem §2), để mọi claim traceable:

```markdown
## Nguồn

- [docs/design/auth.md](../../other-repo/docs/design/auth.md)
- <URL nguồn ngoài>
- internal
- external: "Vendor API Spec v1.1.docx" (vendor X)
```

> ⚠️ **Bẫy path.** Link trong body neo từ **chính file đó**, không neo từ project root — số `../` đổi theo độ sâu thư mục. Viết xong verify bằng `ls <path>` hoặc click thử; link chết trong markdown không có gì báo lỗi hộ.

**Tra cứu — thứ tự thực tế:** `index.md` → cây thư mục + tên file → **Grep full-text body** (recall cao nhất, đừng grep `title:`/`description:` trước) → Read.

> ⚠️ **Không đóng dấu metadata hàng loạt bằng script.** Metadata phải derive từ *nội dung file*, không từ *đường dẫn folder* — vá máy chỉ sinh compliance rỗng.

---

**Bộ quy tắc đang hoạt động khi:** mọi file có section `## Nguồn` với link
truy được, claim kỹ thuật có source link, mọi claim đều traceable hoặc gắn
uncertainty marker, và không bịa nội dung để lấp chỗ trống.
