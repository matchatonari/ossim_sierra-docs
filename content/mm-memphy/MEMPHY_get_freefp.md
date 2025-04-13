Tìm khung trang còn trống trong vùng nhớ ảo của process.
# Tham số
- [[memphy_struct]]* `mp`: không gian vùng nhớ vật lý process đang chiếm giữ.
- `int* retfpn`: mã khung trang trả về.
# Quá trình
- Nếu `free_fp_list` của `mp` NULL thì trả về -1 (thất bại).
- Loại bỏ trang đầu tiên khỏi `free_fp_list` rồi trả về `fpn` của trang này, cuối cùng giải phóng các biến cục bộ và trả về 0 để kết thúc.