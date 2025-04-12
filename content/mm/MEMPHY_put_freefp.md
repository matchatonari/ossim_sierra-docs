# Tham số
- [[memphy_struct]]* `mp`: bộ quản lý RAM vật lý.
- `fpn`: số khung trang.
# Quá trình
- Lấy [[framephy_struct]]* `fp` là `mp->free_fp_list`.
- Tạo node mới kiểu [[framephy_struct]]* `newnode` rồi đặt `fpn` của nó là `fpn`.
- Chèn node này vào đầu `fp`.
- Trả về 0 để kết thúc.