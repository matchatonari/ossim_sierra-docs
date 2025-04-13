Đọc dữ liệu từ địa chỉ `addr` trong RAM vật lý [[memphy_struct]].
# Tham số
- [[memphy_struct]]* `mp`
- `int addr`
- `BYTE* value` lưu dữ liệu đọc được.
# Quá trình
- Nếu `mp == NULL` thì trả về -1 (lỗi).
- Nếu `mp->rdmflg` thì gán `value` là `mp->storage` (địa chỉ đầu), không thì sẽ dùng [[MEMPHY_seq_read]] để đọc ngẫu nhiên, trả về 0 để kết thúc.