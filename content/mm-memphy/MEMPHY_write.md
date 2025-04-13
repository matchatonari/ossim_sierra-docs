Tương tự như [[MEMPHY_read]] nhưng sẽ gán dữ liệu từ biến `data` thay vì đọc.
# Tham số
- [[memphy_struct]]* `mp`
- `int addr`
- `BYTE* value` lưu dữ liệu cần ghi.
# Quá trình
- Nếu `mp == NULL` thì trả về -1 (lỗi).
- Nếu `mp->rdmflg` thì gán `value` là `mp->storage` (địa chỉ đầu), không thì sẽ dùng [[MEMPHY_seq_write]] để ghi ngẫu nhiên, trả về 0 để kết thúc.