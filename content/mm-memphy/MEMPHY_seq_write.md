Tương tự như [[MEMPHY_seq_read]] nhưng thay vì đọc thì là ghi.
# Tham số
- [[memphy_struct]]* `mp`
- `int addr`
- `BYTE* value`
# Quá trình
- Nếu `mp == NULL` hoặc `mp->rdmflg` thì trả về -1, thất bại.
- Ngược lại ta sẽ di chuyển con trỏ tới `addr` bằng hàm [[MEMPHY_mv_csr]], sau đó lưu `value` vào `mp->storage[addr]`. Trả về 0 để kết thúc.