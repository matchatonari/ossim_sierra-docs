Giải phóng bộ nhớ.
# Tham số
- [[pcb_t]]* `caller`: process xin giải phóng bộ nhớ.
- `int vmaid`: mã vùng nhớ (page) muốn giải phóng.
- `int rgid`: mã vùng nhớ tương đối (trong page) muốn giải phóng.
# Quá trình
- Kiểm tra nếu `rgid` vượt quá số trang hoặc âm thì trả về -1 (thất bại).
- Đưa tất cả các vùng nhớ đã giải phóng vào `freerg_list`.
- Đưa vào danh sách các vùng nhớ "lỗi thời" `enlist_vm_freerg_list()`.
- Trả về 0 (thành công).