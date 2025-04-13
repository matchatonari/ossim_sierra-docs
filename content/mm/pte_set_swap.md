Đánh dấu một trang nằm trong swap.
# Tham số
- `uint32_t* pte`: page table entry.
- `int swptyp`: swap type.
- `int swpoff`: offset của trang này trong swap.
# Quá trình
- Bật bit present và bit swap.
- Đưa swap type và swap offset vào bằng hàm [[SETVAL]].
- Trả về 0 để kết thúc.