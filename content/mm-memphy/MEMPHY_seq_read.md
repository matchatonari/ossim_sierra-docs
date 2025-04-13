Đọc địa chỉ ngẫu nhiên của [[memphy_struct]].
# Tham số
- [[memphy_struct]]* `mp`
- `int addr`
- `BYTE* value`
# Quá trình
- Nếu `mp == NULL` hoặc `mp->rdmflg` thì trả về -1, thất bại.
- Ngược lại ta sẽ di chuyển con trỏ tới `addr` bằng hàm [[MEMPHY_mv_csr]], sau đó lưu `mp->storage[addr]` vào `value`. Trả về 0 để kết thúc.