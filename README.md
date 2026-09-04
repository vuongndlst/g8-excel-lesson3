# Biến thứ ba – Đếm và tính có điều kiện

Website tĩnh dành cho GitHub Pages. Bài 3 của chuỗi Excel & Phân tích dữ liệu, khối 8.

## Đưa lên GitHub Pages
1. Tạo một repository mới trên GitHub.
2. Upload `index.html` vào thư mục gốc của repository.
3. Vào **Settings → Pages**.
4. Chọn **Deploy from a branch**.
5. Chọn nhánh **main** và thư mục **/(root)**.
6. Lưu và chờ GitHub tạo đường dẫn website.

## Điều kiện sử dụng
Học sinh mở lại đúng file của Bài 2: **LSTS_KhaoSat_K8_2026_AnDanh_Cleaned.xlsx**, sheet `Clean_Data`.
Bài 3 dùng chung bộ dữ liệu đó, không có file mới. Vùng dữ liệu vẫn là hàng 3 → hàng 300 (298 phản hồi).

Các cột dùng trong bài: `B` giờ ngủ · `C` giờ thiết bị · `E` giờ tự học · `H` điểm TB lớp 7 ·
`I` phương tiện · `J` mạng xã hội · `K` mức tập trung.

## Nội dung
- Chặng 1: COUNTIF – đếm có điều kiện (điều kiện số và điều kiện chữ)
- Chặng 2: AVERAGEIF – trung bình có điều kiện, ba đối số
- Chặng 3: So sánh nhóm và cỡ mẫu, tỉ lệ phần trăm
- Chặng 4: COUNTIFS và AVERAGEIFS – hai điều kiện, bẫy thứ tự đối số
- Chặng 5: Biến thứ ba – vì sao chưa kết luận được
- Kiểm tra cuối: 10 câu ngẫu nhiên rút từ ngân hàng 20 câu, đạt 8/10 để tải minh chứng PNG/PDF

## Đáp án các chặng (dành cho giáo viên)

Sheet `Clean_Data`, vùng hàng 3 → 300.

| Chặng | Công thức | Kết quả |
|---|---|---|
| 1 | `=COUNTIF(B3:B300;"<6")` | 30 |
| 1 | `=COUNTIF(B3:B300;">=8")` | 72 |
| 1 | `=COUNTIF(J3:J300;"TikTok")` | 100 |
| 1 | `=COUNTIF(I3:I300;"Đi bộ")` | 13 |
| 2 | `=AVERAGEIF(B3:B300;"<6";H3:H300)` | 5.77 · n = 30 |
| 2 | `=AVERAGEIF(B3:B300;">=8";H3:H300)` | 8.36 · n = 69 |
| 2 | `=AVERAGEIF(K3:K300;"Cao";E3:E300)` | 6.21 |
| 3 | `=AVERAGEIF(I3:I300;"Đi bộ";H3:H300)` | 7.82 · n = 13 |
| 3 | `=AVERAGEIF(I3:I300;"Xe máy (người thân chở)";H3:H300)` | 7.17 · n = 103 |
| 3 | `=COUNTIF(B3:B300;"<6")/COUNT(B3:B300)` | 10.2% |
| 4 | `=COUNTIFS(B3:B300;"<6";H3:H300;"<7")` | 26 |
| 4 | `=COUNTIFS(B3:B300;">=8";H3:H300;">=8")` | 45 |
| 4 | `=AVERAGEIFS(H3:H300;B3:B300;">=8";C3:C300;"<2")` | 8.36 · n = 24 |
| 4 | `=AVERAGEIFS(H3:H300;B3:B300;"<6";C3:C300;">=4")` | 5.79 · n = 20 |
| 5 | `=AVERAGEIF(B3:B300;"<6";C3:C300)` | **4.65** giờ thiết bị |
| 5 | `=AVERAGEIF(B3:B300;">=8";C3:C300)` | **2.26** giờ thiết bị |

Chốt của cả bài: nhóm ngủ ít có điểm thấp hơn **2.59 điểm**, nhưng cũng chính là nhóm dùng thiết bị
**nhiều hơn gấp đôi**. Không thể kết luận thiếu ngủ làm điểm thấp.

## Lưu ý kỹ thuật
- Phần nhiệm vụ **không in sẵn công thức**. Học sinh làm sai ô nào thì ô đó tô đỏ và chỉ ô đó hiện gợi ý công thức; câu chọn sai cũng tô đỏ riêng.
- Website không cần backend. Họ tên và lớp lưu trong `localStorage` (khóa `excelCond3Student`).
- PDF tạo từ ảnh minh chứng bằng jsPDF tải từ CDN; nếu mạng chặn CDN, học sinh vẫn tải được bản PNG.
- Ô nhập kết quả chấp nhận cả dấu phẩy và dấu chấm thập phân, có hoặc không có dấu phân cách hàng nghìn.
- Riêng ô tỉ lệ phần trăm chấp nhận cả `10.2` (đã định dạng %) lẫn `0.102` (chưa định dạng).
- Các phương án trong ô chọn được xáo trộn ngẫu nhiên mỗi lần tải trang.
