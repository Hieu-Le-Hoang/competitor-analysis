---
title: "Nam Phong Tây Đô — vốn điều lệ và bản đồ pháp nhân quanh người đại diện"
description: Kết quả truy vốn điều lệ MST 6300233207 qua 19 nguồn công khai, và bản đồ các pháp nhân gắn tên Huỳnh Ngọc Quyên sau khi lọc trùng tên.
---

# Vốn điều lệ & bản đồ pháp nhân — Nam Phong Tây Đô

## Chốt nhanh

**Vốn điều lệ: KHÔNG lấy được bằng nguồn công khai miễn phí.** Đã cày 19 nguồn, không nguồn nào lộ con số. Đây không phải "chưa tìm kỹ" — đây là **kết luận đóng**: mọi site có khả năng chứa dữ liệu này đều chặn bằng Cloudflare hoặc login-wall, kể cả khi đi qua proxy.

Bù lại lane này chốt được **địa chỉ đầy đủ của cả 5 chi nhánh** (trước chỉ có tên tỉnh) và lọc sạch nhiễu trùng tên quanh người đại diện.

## Phần A · Vốn điều lệ — đóng hồ sơ

### Đã thử gì, hỏng thế nào

| Nguồn | Cách thử | Kết quả |
|---|---|---|
| masothue.com | WebFetch trực tiếp | ✅ Trang load được, đủ MST/người đại diện/địa chỉ/ngành nghề — **nhưng không có mục vốn điều lệ** |
| thuvienphapluat.vn/ma-so-thue | Trực tiếp + proxy `r.jina.ai` | 403 Cloudflare **cả hai cách** |
| dauthau.asia | Trực tiếp + proxy | 403; qua proxy lộ login-wall *"This function is for members only"* |
| dauthau.net | Trực tiếp + proxy | 403 cả hai cách |
| thongtindoanhnghiep.co | Trực tiếp + proxy | 403; qua proxy dính bot-check/CAPTCHA |
| hosocongty.vn | Trực tiếp | 403 |
| infodoanhnghiep.com | Trực tiếp + `site:` | 404; search không ra trang chi tiết |
| bizc.vn | Proxy | *"Error establishing a database connection"* — site hỏng |
| mst.vn · tracuudoanhnghiep.vn · masocongty.vn · doanhnghiepmoi.vn | Proxy | HTTP 422 (cả 4) |
| tratencongty.com | Proxy | Load được nhưng không có trang riêng cho 6300233207 |
| vietnamcredit.com.vn | `site:` search | Không có kết quả khớp |
| opencorporates.com | Search | **Không có record** công ty này trong index |
| congtyviet.vn · dulieuphapluat.vn | — | Không tìm ra URL pattern hợp lệ để thử |
| dangkykinhdoanh.gov.vn | (không thử lại) | Đã biết là SPA JS-render — cần browser thật |

### Kết luận phải rút ra

**Vốn điều lệ chỉ còn ba đường lấy, cả ba đều nằm ngoài tầm AI:** `[VERIFIED — về giới hạn kỹ thuật]`

1. Mở `dangkykinhdoanh.gov.vn` bằng **browser thật**, tra MST — ~5 phút, miễn phí. **Đường rẻ nhất.**
2. Mua tài khoản dauthau.info hoặc báo cáo VietnamCredit/CIC — mất tiền.
3. Đòi thẳng trong HSDT: bản sao **Giấy chứng nhận ĐKKD** + **BCTC 3 năm** theo tiêu chí năng lực tài chính (HSMT lập theo Nghị định 24/2024/NĐ-CP). **Đường chắc nhất** — số họ tự nộp, có giá trị pháp lý, không phải số scrape.

> Nói thẳng: đường 3 tốt hơn cả hai đường kia. Vốn điều lệ trên giấy đăng ký không nói lên năng lực thật; BCTC kiểm toán mới nói. Nếu HSMT có tiêu chí tài chính, mình không cần biết trước — mình chỉ cần tiêu chí đủ chặt.

### Quy mô nhân sự vẫn `[CONFLICT]`, chưa phân xử được

| Nguồn | Con số |
|---|---|
| TopCV (đọc qua proxy, nguyên văn *"Company Size: 25-99 nhân viên"*) | **25–99** |
| vieclamcantho.com.vn | **200–500** |

Lane này **không tìm được nguồn thứ ba** để phân xử. Cả hai đều là doanh nghiệp tự khai trên job site. `[CONFLICT]` — **không dùng con số nào làm căn cứ.** Muốn số thật: lấy từ số lao động đóng BHXH trong HSDT.

## Phần B · Bản đồ pháp nhân — đã lọc sạch nhiễu

### B1. Cụm xác định — địa chỉ 5 chi nhánh nay đã đầy đủ

Trước chỉ biết tên tỉnh, giờ có địa chỉ cụ thể:

| Pháp nhân / chi nhánh | MST | Địa chỉ | Tin cậy |
|---|---|---|---|
| **Nam Phong Tây Đô** (công ty mẹ) | 6300233207 | 155B Mỹ Quới, Hiệp Hưng | `[VERIFIED]` |
| CN Cần Thơ | `-001` | 91/35A Khu biệt thự Hưng Lợi, Ninh Kiều | `[INFERRED]` |
| CN Bà Rịa – Vũng Tàu | `-002` | 133 Lê Hồng Phong, P.9, TP Vũng Tàu | `[INFERRED]` |
| CN Đồng Tháp | `-003` | 144 Mai Văn Khải, xã Mỹ Tân, TP Cao Lãnh — *đã chấm dứt MST* | `[INFERRED]` |
| CN Bình Dương | `-004` | P. Đông Hòa, TP Dĩ An | `[INFERRED]` |
| CN Cầu Giấy | `-005` | Ngõ 199 Trần Quốc Hoàn, Cầu Giấy, Hà Nội | `[INFERRED]` |
| **Hộ kinh doanh Nam Phong** | 8047601522-001 | Bến xe Trung tâm, P. Cái Răng, Cần Thơ — lập 09/08/2023 | `[VERIFIED]` |
| MST cá nhân chủ hộ | 8047601522 | Cư trú **Q. Ô Môn, TP Cần Thơ** | `[VERIFIED]` |

> 🔻 **ĐÍNH CHÍNH — hạ mức tin cậy toàn bộ địa chỉ chi nhánh.** Bản đầu file này gắn `[VERIFIED]` cho cả 5 địa chỉ. **Sai.**
>
> Địa chỉ lấy từ `masothue.com` **qua WebFetch**, mà WebFetch tóm tắt trang bằng một model nhỏ. Lane xác minh chi nhánh phát hiện: trong một lần fetch, địa chỉ CN `-002` trả về là *"Lô C6, Sao Mai Bến Đình"* — verify chéo thì địa chỉ đó **thuộc một MST hoàn toàn khác** (0317676534, người đại diện Trần Thị Huế). Tức khâu tóm tắt **có thể gán nhầm địa chỉ của doanh nghiệp khác**.
>
> Địa chỉ giữ lại là bản lặp nhất quán qua 2 lần tra độc lập, nên vẫn đáng tin ở mức `[INFERRED]` — nhưng **không được dùng làm căn cứ trong hồ sơ thầu** khi chưa đối chiếu `dangkykinhdoanh.gov.vn` bằng browser thật. Chi tiết: [08-xac-minh-chi-nhanh.md](09-xac-minh-chi-nhanh.md).
>
> **Hệ quả kéo theo:** nhận định *"133 Lê Hồng Phong là trục thương mại chính nên chi nhánh BR-VT nhiều khả năng có thật"* — **rút lại**. Nó dựa trên một địa chỉ nay chỉ còn `[INFERRED]`, và lane xác minh chi nhánh không tìm được **bất kỳ** dấu vết vận hành nào tại BR-VT. Chi nhánh này quay về trạng thái **KHÔNG RÕ**.

### B2. Bản ghi trùng lặp — MST kiểu CCCD

Tìm thấy **`092184000555`** — "HỘ KINH DOANH NAM PHONG", **cùng tên, cùng địa chỉ Bến xe Trung tâm P. Cái Răng** với `8047601522-001`.

Định dạng 12 số là **MST cá nhân theo số CCCD** (chính sách hợp nhất MST = CCCD từ giữa 2025). Tiền tố **`092` là mã tỉnh của TP Cần Thơ** trong cấu trúc CCCD — khớp với chủ hộ cư trú Ô Môn, Cần Thơ. `[INFERRED]`

**Nhiều khả năng đây là cùng một hộ kinh doanh, chỉ là bản ghi MST mới sau khi chuyển sang mã CCCD** — không phải pháp nhân thứ hai. `[UNVERIFIED — chưa fetch được trang chi tiết của mã này để xác nhận]`

> ⚠️ Đừng đếm nó thành một pháp nhân riêng khi lập bản đồ cụm. Đếm trùng sẽ thổi phồng quy mô cụm và dẫn tới kết luận sai về bảo đảm cạnh tranh.

### B3. Chấn Hưng (6300142990) — vẫn treo, không tiến thêm được

Lane này **không xác minh được** Chấn Hưng có cùng một Huỳnh Ngọc Quyên hay không. Mọi lần fetch trang chi tiết masothue của MST này đều fail (404 do sai slug, không tìm ra slug đúng), và **không lấy được số điện thoại của Chấn Hưng để đối chiếu**.

Giữ nguyên ở `[INFERRED — khả năng cao]` như vòng 1: khớp tên người đại diện + khớp cơ quan thuế "Thuế cơ sở 8, TP Cần Thơ", nhưng lệch số điện thoại (0939368789 ≠ 0907822881).

**Đã thử thêm trực tiếp (20/08/2026), vẫn hỏng:**

| Cách | Kết quả |
|---|---|
| `masothue.com/6300142990-cong-ty-tnhh-tu-van-va-dau-tu-chan-hung` | **HTTP 404** — slug đoán sai, không tìm ra slug đúng |
| WebSearch `"6300142990" Chấn Hưng Ngã Bảy` | **0 kết quả** khớp MST. Chỉ ra trang chi cục thuế Ngã Bảy chung chung |

> **Chốt cho hướng này: dừng.** Pháp nhân đã ngừng hoạt động từ lâu, dấu vết web gần như bằng không, và kể cả xác minh được thì **cũng không đổi kết luận gì** — một công ty xây dựng đã chết năm nào đó không ảnh hưởng tới năng lực đấu thầu hiện tại của Nam Phong Tây Đô. Ghi lại để không ai tốn công đào lại. `[UNVERIFIED — đóng hướng]`

### B4. Chủ sở hữu công ty TNHH MTV — câu hỏi mới, chưa có đáp án

Công ty TNHH một thành viên **luôn có chủ sở hữu**, vai trò này khác với Giám đốc/người đại diện pháp luật. **Không nguồn nào phân biệt được hai vai trò này cho MST 6300233207.**

Suy đoán thông thường là chủ sở hữu = Huỳnh Ngọc Quyên luôn, nhưng đó **chỉ là suy luận từ cấu trúc phổ biến, không có source**. `[UNVERIFIED]`

> **Vì sao câu này đáng theo đuổi:** nếu chủ sở hữu là **một pháp nhân khác** hoặc **người khác**, bản đồ cụm phải vẽ lại, và câu chuyện bảo đảm cạnh tranh theo Điều 6 Luật Đấu thầu 22/2023/QH15 có thể đổi hoàn toàn. Chỉ tra được trên Giấy chứng nhận ĐKKD gốc hoặc `dangkykinhdoanh.gov.vn` — **cùng một lần mở browser là lấy được cả cái này lẫn vốn điều lệ.**

### B5. Đã lọc trùng tên — 15+ MST bị loại

Tra "Huỳnh Ngọc Quyên" theo tên người đại diện trên masothue ra **~18 MST toàn quốc**. Tên này phổ biến, phần lớn là nhiễu.

| Nhóm | Xử lý |
|---|---|
| TP.HCM (Bình Tân, Tân Phú, Phú Thạnh, Thủ Đức, Bình Đông), Long An, Tây Ninh, Đà Nẵng, Lạng Sơn, Bình Thuận, Đắk Lắk — gồm cả Trọng Quyên, Khét Premium, Ngọc Đức, H-Queen... | **Đã loại** — khác vùng, không tín hiệu liên kết nào |
| `2200232058` (+`-001`) — Hộ KD cá thể, TP Sóc Trăng, hoạt động từ 2005 | `[NGHI TRÙNG TÊN]` — cơ quan thuế "Sóc Trăng City" ≠ "Thuế cơ sở 8 Cần Thơ". **Chưa loại hẳn** vì Sóc Trăng nay cùng thuộc TP Cần Thơ sau sáp nhập |
| `1801535175` (+`-001`) — 276 Xuân Thủy P. An Bình Cần Thơ / 194 Tôn Đức Thắng Sóc Trăng | `[NGHI TRÙNG TÊN]` — **đã chấm dứt MST** từ 2017, MST cá nhân khác hẳn 8047601522 |
| `094183014776` — cá nhân, 05 đường 3/2, P.1, TP Cần Thơ | `[NGHI TRÙNG TÊN]` — trùng địa chỉ với nhánh của 2200232058, có thể là bản ghi post-sáp nhập của cùng cá nhân đó. Không đủ căn cứ nối với Nam Phong |

> **Kết luận phần này:** ngoài Nam Phong Tây Đô + Hộ KD Nam Phong (đã chắc) và Chấn Hưng (khả năng cao), **không tìm thêm được pháp nhân thứ tư nào** đủ bằng chứng để đưa vào cụm. Ba bản ghi Sóc Trăng/Cần Thơ ở trên treo lại, chưa loại hẳn cũng chưa nhận.

### B6. Tra theo địa chỉ — không có công cụ

Muốn biết còn pháp nhân nào khác đăng ký tại 91/35A Hưng Lợi hoặc 155B Mỹ Quới, nhưng **masothue chỉ hỗ trợ tra theo tên/MST, không tra theo địa chỉ**. `[UNVERIFIED — chưa loại trừ, chỉ là chưa có công cụ]`

## Ba việc gộp chung một lần mở browser

Lane này chốt được một điều thực dụng: **ba câu hỏi lớn còn treo đều nằm trên cùng một trang.**

```
dangkykinhdoanh.gov.vn -> tra MST 6300233207
  ├── vốn điều lệ            (ô trống lớn nhất của hồ sơ)
  ├── chủ sở hữu TNHH MTV    (có thể vẽ lại bản đồ cụm)
  └── ngày thay đổi ĐKKD gần nhất  (mạng lưới đang mở hay co)
```

~5 phút, miễn phí, không cần nghiệp vụ. Đây là việc đáng làm nhất còn lại trong toàn bộ hồ sơ.

## Nguồn

- [masothue.com — 6300233207](https://masothue.com/6300233207-cong-ty-tnhh-dau-tu-sieu-thi-nam-phong-tay-do) — `[VERIFIED]`, nguồn chính của bảng chi nhánh
- [masothue.com — Hộ kinh doanh Nam Phong 8047601522-001](https://masothue.com/8047601522-001-ho-kinh-doanh-nam-phong) — `[VERIFIED]`
- [masothue.com — tra theo tên người đại diện "Huỳnh Ngọc Quyên"](https://masothue.com/Search/?q=HU%E1%BB%B2NH%20NG%E1%BB%8CC%20QUY%C3%8AN&type=legalName) — nguồn của bảng lọc trùng tên
- [TopCV — hồ sơ công ty](https://www.topcv.vn/cong-ty/cong-ty-tnhh-dau-tu-sieu-thi-nam-phong-tay-do/179416.html) — đọc qua proxy `r.jina.ai`, nguyên văn "Company Size: 25-99 nhân viên"
- [Nghị định 24/2024/NĐ-CP — toàn văn](https://vanban.chinhphu.vn/?pageid=27160&docid=209823) — căn cứ tiêu chí năng lực tài chính trong HSMT
- **Không tiếp cận được:** `thuvienphapluat.vn/ma-so-thue`, `dauthau.asia`, `dauthau.net`, `thongtindoanhnghiep.co`, `hosocongty.vn` (403/Cloudflare/login-wall, kể cả qua proxy) · `bizc.vn` (lỗi database) · `mst.vn`, `tracuudoanhnghiep.vn`, `masocongty.vn`, `doanhnghiepmoi.vn` (HTTP 422) · `infodoanhnghiep.com` (404) · `opencorporates.com` (không có record) · `dangkykinhdoanh.gov.vn` (SPA JS-render, cần browser thật)
