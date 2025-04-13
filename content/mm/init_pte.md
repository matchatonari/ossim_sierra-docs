Tạo ra một PTE mới.
# Tham số
- `uint32_t pte`: con trỏ pte (giá trị trả về).
- `int pre` (present): có trong RAM không.
- `int fpn`: số hiệu frame vật lý.
- `int drt`: có dirty không.
- `int swp`: có nằm trong swap không.
- `int swptyp`: swap type, có thể là địa chỉ lưu PTE...
- `int swpoff`: địa chỉ lưu trong swap.
# Quá trình
- Nếu `pre = 0`, không làm gì và trả về 0.
- Nếu `swp == 0`, trang hiện diện trong RAM. Tiếp tục kiểm tra xem có `fpn` chưa, nếu bằng 0 là không hợp lệ, trả về -1, nếu không thì đặt bit present, tắt bit swap, tắt bit dirty, và [[SETVAL]] theo `fpn`.
- Nếu `swp != 0`, đặt bit present, đặt bit swap, xóa bit dirty, và dùng [[SETVAL]] để đưa `swptyp` và `swpoff` vào.
- Cuối cùng trả về 0 để kết thúc.