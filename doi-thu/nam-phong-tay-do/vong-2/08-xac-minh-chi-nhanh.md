---
title: "Nam Phong Tây Đô — xác minh 5 chi nhánh có vận hành thật hay không"
description: Kết quả kiểm chứng từng chi nhánh của MST 6300233207 bằng danh sách hành chính, giấy ATTP và dấu vết tuyển dụng địa phương, thay cho phương pháp Google Maps không dùng được.
---

# Xác minh 5 chi nhánh — Nam Phong Tây Đô

## Chốt nhanh

**Chỉ Cần Thơ xác minh được là thật. Bốn chi nhánh còn lại: KHÔNG RÕ — và "không rõ" ở đây phải hiểu đúng nghĩa.**

Hầu hết cổng hành chính cần tra đều **không kết nối được** (ECONNREFUSED, lỗi cert). Nghĩa là mình chưa mở được danh sách để xem có tên họ hay không, chứ không phải đã mở ra và thấy trống. Hai chuyện đó khác nhau hoàn toàn, và lẫn chúng lại sẽ dẫn tới kết luận "chi nhánh ma" hoàn toàn sai.

## Bảng xác minh từng chi nhánh

| MST | Địa bàn | Có trong danh sách hành chính? | Dấu vết vận hành khác | Kết luận |
|---|---|---|---|---|
| **-001** | **Cần Thơ** | Không tra được danh sách Sở Công Thương | **5 nguồn tuyển dụng độc lập**, nhiều năm, cùng địa chỉ 345 Nguyễn Văn Cừ + cùng SĐT 02923744012. Tin *"Quản Lý Căn TIN + Siêu Thị MINI"* đăng nhiều đợt (27/06/2022 và các tin hạn 2026) | ✅ **THẬT** `[VERIFIED]` |
| **-002** | **Bà Rịa – Vũng Tàu** | Cổng chính thức BR-VT **ECONNREFUSED** — chưa mở được | **Không** tin tuyển dụng, **không** tin tức, kể cả khi tra thẳng địa chỉ đăng ký | ❓ **KHÔNG RÕ** `[UNVERIFIED]` |
| **-003** | **Đồng Tháp** | Cổng Đồng Tháp có bài *"Danh sách Siêu thị, TTTM tỉnh Đồng Tháp 2025"* kèm file `.xlsx` — **ECONNREFUSED**, chưa đọc được | — | Đã chấm dứt MST (theo vòng 1) — lane này **không tự verify lại được** |
| **-004** | **Bình Dương** (Dĩ An) | Không tìm ra link danh sách Sở CT | **Không** tin tuyển dụng nào. Tra riêng "Nam Phong" + KTX khu B Dĩ An: 0 kết quả | ❓ **KHÔNG RÕ** `[UNVERIFIED]` |
| **-005** | **Cầu Giấy, Hà Nội** | Sở CT Hà Nội công bố tổng *"8.321 điểm bán hàng thiết yếu"* nhưng **không có danh sách chi tiết** để tra tên | **Không** tin tuyển dụng nào tại Hà Nội/Cầu Giấy (tra TopCV, JobsGO, CareerViet — 0 kết quả) | ❓ **KHÔNG RÕ** `[UNVERIFIED]` |

## Kết quả phủ định CÓ giá trị — phân biệt rạch ròi

Đây là phần quan trọng nhất của báo cáo. Không phải mọi "không tìm thấy" đều ngang nhau.

### Đã tra được, và KHÔNG có tên → có giá trị

| Nguồn | Đã tra gì |
|---|---|
| TopCV, JobsGO, Muaban.net, CareerViet, Vieclam24h | "Nam Phong tuyển dụng" + **từng tỉnh** (BR-VT / Bình Dương / Hà Nội) — **0 kết quả** ở cả ba |
| yellowpages.vn, trangvangvietnam.com | Danh sách siêu thị Cần Thơ / BR-VT / Bình Dương — không có tên Nam Phong |

> Riêng danh bạ thương mại tư nhân (yellowpages, trang vàng) thì **giá trị phủ định thấp** — doanh nghiệp không đăng ký thì không có tên, chuyện bình thường. Còn việc **không có một tin tuyển dụng nào** ở ba tỉnh trong khi Cần Thơ tuyển liên tục thì đáng chú ý hơn. `[INFERRED]`

### KHÔNG tra được → không kết luận gì

| Nguồn | Lỗi kỹ thuật |
|---|---|
| `ittpa.baria-vungtau.gov.vn` — danh sách siêu thị/TTTM/chợ BR-VT | **ECONNREFUSED** 210.2.73.22:443 |
| `dongthap.gov.vn` — danh sách ST/TTTM Đồng Tháp 2025 + file Excel | **ECONNREFUSED** 123.30.141.6:443 |
| `ccatvstpcantho.com` — cơ sở tự công bố sản phẩm ATTP Cần Thơ | **ECONNREFUSED** |
| `baobariavungtau.com.vn` — bài về kinh doanh căn tin tại BV Vũng Tàu | Lỗi certificate mismatch (domain trỏ nhầm sang cert của `nghean.gov.vn` — lỗi hạ tầng phía họ) |
| `vfa.gov.vn` — tra cứu ATTP | Là hệ thống **form nhập liệu**, không tra được qua fetch |
| `masothue.com` trang con `-002`/`-003`/`-004`/`-005` | HTTP 404 — chỉ trang công ty mẹ fetch được, slug từng chi nhánh không đoán đúng |
| `dauthau.net` | 403 |

> ⚠️ Một chi tiết đáng lưu: bài `baobariavungtau.com.vn` về **"kinh doanh căn tin tại Bệnh viện Vũng Tàu"** — đúng mô hình của đối thủ, đúng địa bàn có chi nhánh -002. Không đọc được vì lỗi cert phía báo. **Đây là đầu mối cụ thể đáng mở lại bằng browser thật.**

## Cổng Sở Công Thương — 1/5 vào được

Hướng "danh sách siêu thị của Sở Công Thương" là mũi chính của lane này. Kết quả: **gần như không khả thi bằng công cụ hiện có.**

| Tỉnh | Vào được? | Chi tiết |
|---|---|---|
| **Cần Thơ** | ✅ | `socongthuong.cantho.gov.vn` load được. Nhưng **chưa tìm ra trang con danh sách siêu thị/cửa hàng tiện lợi** — chỉ vào được trang *"Công bố TTHC An toàn thực phẩm"*, mà trang này chỉ liệt kê **tiêu đề** các đợt công bố, không phải danh sách cơ sở |
| Bà Rịa – Vũng Tàu | ❌ | `ittpa.baria-vungtau.gov.vn` — `ECONNREFUSED`, thử lại **3 lần** vẫn vậy |
| Bình Dương | ❌ | `socongthuong.binhduong.gov.vn` — `ENOTFOUND` (DNS không resolve), dù domain xuất hiện bình thường trong kết quả Google |
| Hà Nội | ❌ | `sct.hanoi.gov.vn` → `ENOTFOUND`; `congthuong.hanoi.gov.vn` → lỗi certificate |
| Đồng Tháp | ❌ | `dongthap.gov.vn` — lỗi kết nối cả 2 lần |

> **Đọc đúng kết quả Cần Thơ:** không thấy chữ "Nam Phong" trong các **tiêu đề** đợt công bố — nhưng đây là tín hiệu **rất yếu**, vì tên cơ sở nằm trong nội dung từng bài chứ không nằm ở tiêu đề. `[UNVERIFIED]`

## Quan sát đáng chú ý: 3 chi nhánh "không rõ" đều lệch mô hình

Lane này chỉ ra một điểm mà các vòng trước bỏ sót:

| Chi nhánh | Vị trí | Khớp mô hình "trong bệnh viện"? |
|---|---|---|
| Cần Thơ `-001` | 345 Nguyễn Văn Cừ — **trong khuôn viên BV Nhi Đồng** | ✅ Khớp |
| Đồng Tháp `-003` | Trong khuôn viên bệnh viện (theo mô hình cũ) — **đã đóng** | ✅ Khớp |
| BR-VT `-002` · Bình Dương `-004` · Cầu Giấy `-005` | 133 Lê Hồng Phong · tầng trệt KTX khu B Dĩ An · ngõ 199 Trần Quốc Hoàn | ❌ **Không khớp** |

**Hai chi nhánh xác minh được hoạt động thật đều nằm trong bệnh viện. Ba chi nhánh không xác minh được thì không cái nào nằm trong bệnh viện.** `[INFERRED]`

> Đây không phải bằng chứng chúng là "vỏ". Nhưng nó gợi ý ba chi nhánh kia **không phải điểm bán theo mô hình cốt lõi của họ** — có thể là kho, văn phòng đại diện, hoặc địa điểm đăng ký để giữ tư cách địa bàn. Nếu HSMT đòi **năng lực hiện diện tại địa bàn**, đây là chỗ đáng yêu cầu làm rõ: hợp đồng thuê mặt bằng, hóa đơn điện nước, ảnh chụp biển hiệu.

### Riêng BR-VT: đã tra và không có

Phân biệt cho rõ, vì đây là chi nhánh từng được đánh giá cao nhất trong nhóm chưa xác minh:

- Search `"133 Lê Hồng Phong"` + `"Nam Phong"`, và `"Nam Phong"` + siêu thị/căn tin + bệnh viện Bà Rịa/Vũng Tàu → **0 kết quả**. Đây là **ĐÃ TRA và KHÔNG CÓ**, không phải không tra được.
- Tuyển dụng "Nam Phong" tại Vũng Tàu trên TopCV, JobsGO, Muaban.net, CareerViet, Vieclam24h → **0 tin**, trong khi công ty vẫn đăng tuyển liên tục tại Cần Thơ **cùng giai đoạn**.

→ **Không nâng BR-VT lên "THẬT" chỉ vì nằm trên trục đường chính.** Vắng dấu vết sau khi đã tra nhiều hướng là một tín hiệu — dù vẫn chưa phải bằng chứng vắng mặt.

## Giấy chứng nhận ATTP — không tra được

Cơ sở kinh doanh thực phẩm bắt buộc phải có. Đã thử `vfa.gov.vn` (form nhập liệu, không fetch được) và `ccatvstpcantho.com` (ECONNREFUSED). Search trực tiếp tên công ty + "giấy chứng nhận ATTP" cũng không ra. `[UNVERIFIED]`

## Chi nhánh mới 2025–2026 — không có

Tra `thongtindoanhnghiep.co`, `infodoanhnghiep.com`, `masothue.com`: trang công ty mẹ **chỉ liệt kê đúng 5 chi nhánh** `-001` đến `-005`, không hơn. Không có dấu hiệu mở thêm sau 05/2024. `[UNVERIFIED — chưa loại trừ khả năng có nhưng chưa được index]`

> Ghép với dữ kiện Đồng Tháp đã đóng: **mạng lưới đang co lại hoặc đứng yên, không mở rộng.** Đây là tín hiệu ngược với hình ảnh "chuỗi 5 tỉnh" mà họ có thể trình bày trong HSDT. `[INFERRED]`

## ⚠️ Cảnh báo về độ tin cậy dữ liệu masothue.com

**Lane này phát hiện một lỗi dữ liệu thật, cần ghi lại để cả hồ sơ cảnh giác.**

Địa chỉ chi nhánh lấy từ `masothue.com` qua WebFetch — mà WebFetch tóm tắt trang bằng một model nhỏ. Trong một lần fetch, kết quả trả về địa chỉ chi nhánh `-002` là *"Lô C6, Sao Mai Bến Đình"*. Verify chéo cho thấy địa chỉ đó **thuộc một MST hoàn toàn khác** (0317676534, người đại diện Trần Thị Huế). **Đã loại bỏ.**

Địa chỉ được giữ lại — *133 Lê Hồng Phong, P.9, TP Vũng Tàu* — là địa chỉ **lặp lại nhất quán qua 2 lần tra độc lập**. Nhưng bài học rút ra:

> 🔻 **Địa chỉ 5 chi nhánh ghi ở [09-tai-chinh-phap-nhan.md](09-tai-chinh-phap-nhan.md) phải hạ từ `[VERIFIED]` xuống `[INFERRED]`.** Chúng đến từ tóm tắt tự động, và tóm tắt tự động đã chứng minh là có thể gán nhầm địa chỉ của MST khác. Muốn chắc: tra `dangkykinhdoanh.gov.vn` bằng browser thật.

## Giới hạn cứng của phương pháp

**Không có công cụ Maps.** Nghĩa là hoàn toàn không thể xác nhận trực quan biển hiệu, giờ mở cửa, hay hoạt động thực tế tại địa chỉ đăng ký của 4 chi nhánh còn lại.

> Nhắc lại cho rõ, vì đây là chỗ dễ kết luận ẩu nhất trong cả hồ sơ: **đây là giới hạn của phương pháp, KHÔNG phải bằng chứng công ty "ma".** Bốn chi nhánh kia có thể đang hoạt động bình thường mà mình không thấy, cũng có thể chỉ tồn tại trên giấy. Hiện chưa có cơ sở để nghiêng về bên nào.

## Đã loại vì trùng tên

| Thực thể | Vì sao loại |
|---|---|
| "Chi Nhánh Công Ty TNHH Nam Phong" — 65 Trần Quốc Hoàn, P. Tân Sơn Nhất, TP.HCM | Công ty khác ("Công ty TNHH Nam Phong"), khác tỉnh với chi nhánh -005 ở Cầu Giấy Hà Nội. **Bẫy đặc biệt dễ dính vì cùng tên đường Trần Quốc Hoàn** |
| "Công Ty TNHH Dịch Vụ Vận Tải Và Thương Mại Nam Phong" | Công ty khác, ngành vận tải |

## Nguồn

- [sanvieclamcantho.com — tin "Quản Lý Căn TIN + Siêu Thị MINI"](https://sanvieclamcantho.com/cong-ty-tnhh-dt-st-nam-phong-tuyen-dung-quan-ly-37511.html) — `[VERIFIED]`, bằng chứng vận hành mạnh nhất cho CN Cần Thơ
- [canthoinfo.vn/namphong.asp](https://www.canthoinfo.vn/namphong.asp) — điểm bán 345 Nguyễn Văn Cừ, SĐT 02923744012
- [masothue.com — 6300233207](https://masothue.com/6300233207-cong-ty-tnhh-dau-tu-sieu-thi-nam-phong-tay-do) — nguồn địa chỉ chi nhánh, **đọc kèm cảnh báo độ tin cậy ở trên**
- **Không tiếp cận được:** `ittpa.baria-vungtau.gov.vn` · `dongthap.gov.vn` · `ccatvstpcantho.com` (đều ECONNREFUSED) · `baobariavungtau.com.vn` (lỗi cert) · `vfa.gov.vn` (form nhập liệu) · `dauthau.net` (403) · masothue trang con từng chi nhánh (404)
