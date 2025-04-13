Đánh dấu page table entry có trong RAM và số hiệu trang trong RAM.
# Tham số
- `uint32_t pte`: số hiệu entry trong bảng trang.
- `int fpn`: số hiệu frame vật lý.
# Quá trình
- Bật bit present, tắt bit swap.
- Đưa địa chỉ `fpn` vào bằng hàm [[SETVAL]] với các tham số `PAGING_PTE_FPN_MASK` và `PAGING_PTE_FPN_LOBIT`.
- Trả về 0 để kết thúc.