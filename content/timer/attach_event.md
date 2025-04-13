Tạo timer mới.
# Quá trình
- Tạo event mới. Nếu đang ở giữa tick thì không chấp nhận, hủy bỏ thao tác
- Ngược lại thì khởi tạo [[timer_id_t]] mới, các mutex lock và condition.
- Cuối cùng là thêm vào danh sách `dev_list` (toàn cục) (theo kiểu LIFO - stack). Trả về chính timer.