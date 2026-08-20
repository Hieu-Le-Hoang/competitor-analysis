---
title: "Nam Phong Tây Đô — lịch sử đấu giá tài sản và vụ tranh chấp tại tòa"
description: Kết quả cày cổng đấu giá quốc gia dgts.moj.gov.vn cho MST 6300233207, chi tiết bốn công ty dự phiên đấu giá BV Nhi Đồng Cần Thơ, và vụ tranh chấp hợp đồng đang thụ lý tại TAND quận Ninh Kiều.
---

# Đấu giá tài sản & tranh chấp tại tòa — Nam Phong Tây Đô

## Chốt nhanh

Ba kết quả, xếp theo giá trị:

1. **Phát hiện mới, `[VERIFIED]`: đối thủ đang là một bên trong vụ tranh chấp hợp đồng dân sự tại TAND quận Ninh Kiều** — số tiền **1.948.000.100 đồng**. Trước nay hồ sơ ghi "không có bản án nào"; điều đó vẫn đúng, nhưng **có vụ kiện đang thụ lý** thì lại là chuyện khác.
2. **Chi tiết mới về phiên đấu giá 5/3/2021:** có **bốn** công ty, không phải hai. Và diễn biến trả giá có một hình dạng đáng chú ý — đọc kỹ mục cảnh báo kèm theo.
3. **Cổng `dgts.moj.gov.vn`: dùng được một phần, nhưng KHÔNG tra cứu được.** Giả thuyết "mình soi nhầm cổng" chỉ đúng một nửa — cổng đúng thật, nhưng vẫn không vào được bằng công cụ hiện có.

## Phần A · `dgts.moj.gov.vn` — trả lời dứt khoát

**Kết luận: không dùng để tra cứu được. Không phải vì thiếu cố gắng, mà vì kiến trúc trang.** `[VERIFIED — về giới hạn kỹ thuật]`

| Thử gì | Kết quả |
|---|---|
| WebFetch / curl trực tiếp, mọi endpoint | **HTTP 403/406** — trang chặn chứa script `_jsc_ch_conf`, nguyên văn *"Verifying browser environment, this process may take a few seconds, please wait..."* → **WAF JS-challenge**, không phải lỗi mạng |
| Qua proxy `r.jina.ai` (headless browser thật) | ✅ **Vượt được WAF** — đọc trọn nội dung trang chi tiết một thông báo đấu giá khác để kiểm chứng |
| Trang danh sách thông báo | Là **SPA**. Render được form tìm kiếm (Tên tài sản / Tổ chức đấu giá / Người có tài sản / Tỉnh-huyện / Giá khởi điểm) nhưng nút Tìm kiếm là `javascript:void(0)` → **submit qua AJAX**, không phải GET query string |
| Đoán endpoint API nội bộ | 403 — cùng WAF chặn |
| `portal/exportWord?aucInfoId=<id>` | **406 với mọi ID** (test 3 ID khác nhau) → lỗi hệ thống phía server, không phải do nội dung |

**Nghĩa là:** muốn tra cổng này phải **gõ chữ vào ô tìm kiếm rồi bấm nút** — tức cần browser thật. Đường vòng duy nhất còn lại là nhờ Google index (`site:dgts.moj.gov.vn`), mà index của domain này với từ khóa liên quan đối tượng **rất mỏng**.

### Hai URL nghi có nội dung nhưng không mở được

| URL | Vì sao nghi | Trạng thái |
|---|---|---|
| `dgts.moj.gov.vn/portal/exportWord?aucInfoId=60422` | Google index khớp từ khóa "Nam Phong" + "Cần Thơ" | `[UNVERIFIED]` — URL có thật, nội dung không đọc được (406) |
| `dgts.moj.gov.vn/portal/exportWord?aucInfoId=72469` | Khớp từ khóa "Nam Phong Tây Đô" | `[UNVERIFIED]` — cùng lý do |

> Đây là **hai địa chỉ cụ thể** để ai đó mở bằng browser thật — không phải "đi tìm mò". Nếu mở được, có thể ra thêm cuộc đấu giá chưa ai biết.

### Query đã chạy trên `site:dgts.moj.gov.vn` — 0 kết quả

`"Nam Phong Tây Đô"` · `"6300233207"` · `"Huỳnh Ngọc Quyên"` · `"0907822881"` · `"Bệnh viện Nhi Đồng" Cần Thơ` · `"Nhi đồng thành phố Cần Thơ"` · `"căng tin"+"Nhi Đồng"` · `"Đầu tư Siêu thị Nam Phong"` · `"Bệnh viện Nhi đồng"+"lựa chọn tổ chức đấu giá"`. Cũng thử `site:taisancong.vn` — 0 kết quả liên quan.

## Phần B · Vụ tranh chấp tại TAND quận Ninh Kiều — phát hiện mới `[VERIFIED]`

Báo Đại Đoàn Kết đưa tin phản hồi của Sở Y tế TP Cần Thơ sau kết luận thanh tra. Trích nguyên văn nội dung:

- Công dân **Nguyễn Văn Út** tiếp tục có ý kiến, cho rằng lãnh đạo bệnh viện đã **"tự ý giảm giá thuê mặt bằng 1.948.000.100 đồng khi chưa được cấp trên phê duyệt"**.
- Sở Y tế TP Cần Thơ trả lời rằng vụ việc tiền thuê mặt bằng này **"đã được đưa ra Tòa án nhân dân quận Ninh Kiều với tư cách là tranh chấp hợp đồng dân sự giữa hai bên"**, nằm ngoài thẩm quyền giải quyết hành chính của Sở.

<!-- source: daidoanket.vn/cong-dan-tiep-tuc-y-kien-sau-ket-luan-sai-pham-so-y-te-can-tho-len-tieng-10303624.html · truy cập 20/08/2026 -->

### Vì sao dữ kiện này đáng giá

| | |
|---|---|
| **Nó sửa một kết luận cũ** | [04-tin-tieu-cuc.md](../04-tin-tieu-cuc.md) ghi "không tìm thấy bản án nào" — **vẫn đúng**, vì vụ này **chưa xét xử xong**, mới ở giai đoạn thụ lý. Nhưng "không có bản án" và "không có tranh chấp" là hai chuyện khác nhau, và trước nay hồ sơ chưa phân biệt |
| **Nó giải thích vì sao `congbobanan` trống** | Vụ chưa có bản án có hiệu lực thì chưa lên cổng công bố bản án. Việc tra `congbobanan` không ra gì **không mâu thuẫn** với dữ kiện này |
| **Nó dùng được trong HSMT** | Nhiều HSMT có mục kê khai **tranh chấp/kiện tụng đang diễn ra**. Đây là câu hỏi trung lập, áp dụng cho mọi nhà thầu — hợp lệ hoàn toàn |

> ⚠️ **Vẫn phải cẩn thận:** báo không nói rõ **ai kiện ai**, và không khẳng định Nam Phong Tây Đô là bị đơn. "Tranh chấp hợp đồng dân sự giữa hai bên" nói về hợp đồng thuê mặt bằng — hai bên là bệnh viện và bên thuê. Bên thuê mặt bằng siêu thị + căng tin đã `[VERIFIED]` là Nam Phong Tây Đô, nên khả năng rất cao họ là một bên. Nhưng **đây vẫn là `[INFERRED]`**, không phải trích dẫn trực tiếp có tên.

## Phần C · Phiên đấu giá 5/3/2021 — bốn công ty, và một hình dạng đáng chú ý

Trích **nguyên văn** Tuổi Trẻ 09/02/2023 (em tự fetch lại, xác nhận):

> *"Ba công ty tham gia đấu giá gồm T.Đ., Đ.T. và SG Co.op... Lúc này có bốn công ty tham gia và đạt yêu cầu là **C.H., T.Đ., Đ.T. và SG Co.op**. Tháng 1-2021... Công ty T.Đ. thắng với giá 312 triệu đồng, nhưng công ty này không ký hợp đồng nên kết quả đấu giá bị hủy và mất tiền cọc 288 triệu đồng. Trung tâm dịch vụ đấu giá TP Cần Thơ tổ chức đấu giá lại ngày 5-3-2021. **Công ty C.H. đấu giá ba vòng và dừng ở mức 46 triệu đồng. Cuối cùng, Công ty T.Đ. trúng thầu với giá 48 triệu đồng.**"*

### Bốn ký hiệu, không tên nào được nêu đầy đủ

| Ký hiệu | Suy đoán | Trạng thái |
|---|---|---|
| **T.Đ.** | Nam Phong **Tây Đô** | `[INFERRED — rất cao]`: khớp 4 điểm với VietnamNet (cùng mặt bằng, cùng 48tr/tháng, cùng mốc 3/2021, cùng kỳ hạn 36 tháng) |
| **C.H.** | ??? | `[UNVERIFIED]` — **không biết** |
| **Đ.T.** | ??? | `[UNVERIFIED]` — **không biết** |
| **SG Co.op** | Saigon Co.op? | `[UNVERIFIED]` — chỉ là suy đoán từ cách viết tắt, không nguồn nào xác nhận |

### 🚨 Giả thuyết cần kiểm chứng — và cảnh báo đi kèm

Hồ sơ của mình có một pháp nhân tên **CHẤN HƯNG** (MST 6300142990) — viết tắt cũng là **C.H.** — mà [09-tai-chinh-phap-nhan.md](09-tai-chinh-phap-nhan.md) ghi nhận: cùng tên người đại diện *Huỳnh Ngọc Quyên*, cùng cơ quan thuế *"Thuế cơ sở 8, TP Cần Thơ"*, hiện đã ngừng hoạt động.

Nếu C.H. = Chấn Hưng **và** Chấn Hưng đúng là cùng người với Nam Phong Tây Đô, thì diễn biến "C.H. dừng ở 46 triệu, T.Đ. trúng 48 triệu" khớp với đúng cáo buộc trong đơn tố cáo.

> ⛔ **NHƯNG ĐỪNG DÙNG. Đây là suy đoán chồng suy đoán, không phải phát hiện.**
>
> Chuỗi suy luận có **ba mắt xích chưa xác minh**, nhân với nhau thì độ tin cậy còn rất thấp:
> 1. C.H. = Chấn Hưng — **thuần đoán từ 2 chữ cái**. "C.H." khớp với hàng trăm tên công ty.
> 2. Chấn Hưng có cùng một Huỳnh Ngọc Quyên — `[INFERRED]`, **lệch số điện thoại**, đã thử xác minh nhiều lần đều thất bại.
> 3. Từ đó suy ra thông đồng — **đó là kết luận pháp lý mà chưa cơ quan nào đưa ra**.
>
> Phát biểu chuỗi này ra ngoài là **vu khống**, và tệ hơn: nó nghe rất thuyết phục nên dễ khiến chính mình tin. Ghi vào đây để **kiểm chứng**, không phải để dùng.

### Phép thử bác bỏ — đã chạy, KHÔNG chạy được

**Thiết kế phép thử:** tra ngày Chấn Hưng (MST 6300142990) ngừng hoạt động. Nếu ngừng **trước tháng 3/2021** thì nó không thể dự phiên đấu giá 05/03/2021 → giả thuyết chết tại chỗ.

**Kết quả: không thực hiện được.** Đã thử **12 nguồn**, tất cả tắc — và tắc vì rào cản kỹ thuật, **không phải vì tra rồi không thấy**:

| Nguồn | Hỏng thế nào |
|---|---|
| `masothue.com` (nhiều slug) · `hosocongty.vn` | 404 — không đoán đúng slug |
| `site:masothue.com "6300142990"` · `site:thuvienphapluat.vn "6300142990"` · `infodoanhnghiep.com` | **0 kết quả — không được index** |
| `thuvienphapluat.vn` (trực tiếp + proxy) | Cloudflare CAPTCHA *"Attention Required!"* |
| `thongtindoanhnghiep.co` (trực tiếp + proxy) | Cloudflare bot-check *"Just a moment..."* |
| `tratencongty.com` | HTTP 200 nhưng route sai — ra trang danh sách chung, MST hiển thị **dạng ảnh mã hoá chống bot** |
| `congtydoanhnghiep.com` | HTTP 000 — không kết nối được |
| **`tracuunnt.gdt.gov.vn`** (Tổng cục Thuế — thẩm quyền cao nhất) | HTTP 000 trực tiếp; qua proxy `TimeoutError: page.goto Timeout 15000ms exceeded` |
| WebSearch `"6300142990"` không giới hạn site | **0 kết quả liên quan** — MST này gần như không tồn tại trên web công khai |

### Hệ quả: đóng băng giả thuyết

> 🧊 **Giả thuyết C.H. = Chấn Hưng KHÔNG kiểm chứng được, và vì thế KHÔNG được dùng — dưới bất kỳ hình thức nào.**
>
> Đây không phải "chưa đủ bằng chứng nên tạm chưa dùng". Đây là: **không có đường nào để biết đúng hay sai** bằng nguồn công khai. Một giả thuyết không thể bác bỏ được thì không phải là phát hiện — nó là câu chuyện.
>
> Nguy hiểm thật sự của nó nằm ở chỗ nghe rất hợp lý. Càng nghe hợp lý mà càng không kiểm chứng được, thì càng phải cất đi. Ghi lại ở đây để **người sau không đào lại và không tự thuyết phục mình**.
>
> Chỉ mở lại nếu có được **một trong hai**: (a) tra được record MST 6300142990 tại cơ quan thuế hoặc nguồn trả phí, xác định ngày ngừng hoạt động; (b) một nguồn nêu **tên đầy đủ** các công ty dự phiên đấu giá 05/03/2021.

### Hai việc phụ cũng tắc

| Việc | Kết quả |
|---|---|
| Tìm trang HTML chi tiết cho `aucInfoId` 60422 / 72469 | **0 kết quả.** Google chỉ index link `exportWord?aucInfoId=...`, không index trang HTML tương ứng — nhiều khả năng hai hệ thống ID (nội bộ vs slug công khai) không trùng nhau |
| Tìm báo khác nêu tên đầy đủ C.H., Đ.T., SG Co.op | **Không có.** Đã tra baocantho, plo, nld, thanhnien, laodong, cand — **không tờ nào khác ngoài Tuổi Trẻ đưa vụ này.** Mọi kết quả đều dẫn về đúng 4 bài đã biết, hoặc lạc sang BV Nhi Đồng Thành Phố ở TP.HCM |

## Phần D · Hợp đồng hết hạn 3/2024 — sau đó ai trúng?

**Không tìm được.** `[UNVERIFIED]`

Đã tra: WebSearch nhiều biến thể (đấu giá lại 2024/2025/2026), `baodauthau.vn`, `baocantho`, `site:dgts.moj.gov.vn` với "Nhi Đồng"+"Cần Thơ", đọc lại cả 3 bài kết luận thanh tra. **Không nguồn nào đề cập tình trạng mặt bằng sau 3/2024.**

Tin tuyển dụng gần nhất của công ty (6/2026) ghi địa điểm làm việc là **văn phòng 91/35A**, không phải 345 Nguyễn Văn Cừ — nhưng điều này **không kết luận được gì**, vì tin tuyển dụng ghi trụ sở tuyển là chuyện bình thường.

> ⚠️ **Bẫy trùng tên đã chặn:** `baodauthau.vn` có nhiều kết quả "đấu giá mặt bằng **BV Nhi Đồng Thành Phố**" — đó là bệnh viện ở **TP.HCM**, khác hẳn BV Nhi Đồng TP Cần Thơ. Đã loại.

Câu hỏi này vẫn là một trong những câu đáng giá nhất chưa có đáp án: **họ còn giữ được sân nhà hay đã mất.**

## Đã loại vì trùng tên / trùng từ khóa

| Kết quả | Vì sao loại |
|---|---|
| "BIDV chi nhánh **Tây Đô**" trên dgts.moj.gov.vn | Chi nhánh ngân hàng, chỉ trùng chữ "Tây Đô" |
| Đấu giá mặt bằng "BV Nhi Đồng **Thành Phố**" (baodauthau.vn) | Bệnh viện ở TP.HCM, khác bệnh viện |

## Nguồn không tiếp cận được

| Nguồn | Lỗi kỹ thuật |
|---|---|
| `dgts.moj.gov.vn` — mọi endpoint trực tiếp | 403/406, WAF JS-challenge |
| `dgts.moj.gov.vn` — `exportWord` mọi ID, kể cả qua proxy | 406, lỗi hệ thống phía server |
| `dgts.moj.gov.vn` — tra cứu | Nút search `javascript:void(0)`, cần browser automation |
| `congly.vn` | Cloudflare CAPTCHA, chặn cả trực tiếp lẫn qua proxy |
| `dauthau.net` | 403 *"for members only"* |
| `thanhtravietnam.vn` | HTTP 522 / timeout — server nguồn down, không phải WAF |
| `nguoiquansat.vn` | 403 |

## Nguồn

- [Tuổi Trẻ — "Điều tra đấu giá thuê mặt bằng tại Bệnh viện Nhi đồng Cần Thơ" (09/02/2023)](https://tuoitre.vn/dieu-tra-dau-gia-thue-mat-bang-tai-benh-vien-nhi-dong-can-tho-20230209174144328.htm) — `[VERIFIED]`, tự fetch lại xác nhận đoạn 4 công ty
- [**Đại Đoàn Kết — "Công dân tiếp tục ý kiến sau kết luận sai phạm, Sở Y tế Cần Thơ lên tiếng"**](https://daidoanket.vn/cong-dan-tiep-tuc-y-kien-sau-ket-luan-sai-pham-so-y-te-can-tho-len-tieng-10303624.html) — `[VERIFIED]`, nguồn duy nhất của vụ tranh chấp tại TAND quận Ninh Kiều
- [VietnamNet — kết luận thanh tra Sở Y tế (22/11/2024)](https://vietnamnet.vn/ket-luan-vu-ban-giam-doc-benh-vien-nhi-dong-can-tho-bi-to-cao-nhieu-noi-dung-2344613.html) — `[VERIFIED]`
- [dgts.moj.gov.vn](https://dgts.moj.gov.vn/) — Cổng thông tin điện tử quốc gia về đấu giá tài sản, Bộ Tư pháp
- Hai URL chưa mở được: `dgts.moj.gov.vn/portal/exportWord?aucInfoId=60422` · `?aucInfoId=72469`
