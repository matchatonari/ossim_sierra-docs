Tạo mới một đối tượng [[memphy_struct]] mới.
# Tham số
- [[memphy_struct]]* `mp`: vùng nhớ mới, giá trị trả về.
- `int max_size`: dung lượng tối đa.
- `int randomflg`: cho phép đọc ngẫu nhiên hay không.
# Quá trình
- Cấp phát `max_size` byte cho `mp->storage`, đặt `mp->maxsz = max_size`.
- Khởi tạo toàn bộ `mp->storage` bằng 0.
- Định dạng vùng nhớ bằng hàm [[MEMPHY_format]].
- Gán `mp->rdmflg`. Nếu không thể đọc ngẫu nhiên, gán `mp->cursor = 0`.
- Trả về 0 để kết thúc.