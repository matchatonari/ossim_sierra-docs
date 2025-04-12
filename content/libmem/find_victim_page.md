Khi bộ nhớ RAM đầy, hàm sẽ chọn một trang để đẩy ra khỏi RAM nhằm nhường chỗ cho trang mới.
# Tham số
- [[mm_struct]]* `mm`
- `int* retpgn`: số của trang sẽ bị xóa
# Quá trình
- Khai báo danh sách đơn [[pgn_t]]* `pg = mm->fifo_pgn`.
- ...
- Giải phóng `pg` và trả về 0 để kết thúc.