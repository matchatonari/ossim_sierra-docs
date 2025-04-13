Khởi tạo phân trang trên bộ nhớ.
# Tham số
- [[memphy_struct]]* `mp`.
- `int pagesz`: dung lượng mỗi trang.
# Quá trình
- số khung trang = số trang `numfp = mp->maxsz / pagesz`. Nếu số trang âm thì trả về -1 (thất bại).
- Tạo mới danh sách liên kết đơn [[framephy_struct]]* và gán vào `mp->free_fp_list`. Lần lượt cấp phát bộ nhớ, gán cho các khung trang `fpn` bằng biến đếm, gán các liên kết `next` và trả về 0 để kết thúc.