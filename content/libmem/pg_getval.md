Đọc giá trị tại offset đã cho.
# Tham số
- `mm` kiểu [[mm_struct]] trỏ đến lớp quản lý vùng nhớ.
- `int addr` lưu địa chỉ cần đọc giá trị.
- `BYTE* data` lưu giá trị đã đọc được.
- [[pcb_t]]* `caller`: process được gọi.
# Quá trình
- Tìm số block của `addr` trong RAM bằng hàm [[PAGING_PGN]].
- Dùng hàm [[pg_getpage]] để lấy dữ liệu về biến `fpn`. Nếu hàm trả về giá trị khác 0 -> truy cập block không hợp lệ -> trả về -1.
- Ngược lại trả về 0.