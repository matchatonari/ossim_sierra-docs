Lấy frame page number (số khung trang) từ page number (số trang).
# Tham số
- [[mm_struct]]* `mm`: vùng nhớ đang quản lý.
- `int pgn`: index của block trong ô nhớ.
- `int* fpn`: số khung trang.
- [[pcb_t]]* `caller`: process được gọi.
# Quá trình
- Đặt `pte` là dữ liệu của block.
- Nếu các bit PTE được bật (`PAGING_PTE_PRESENT`) thì lấy FPN là `(pte & PAGING_PTE_FPN_MASK) >> PAGING_PTE_FPN_LOBIT` = `pte & 0xFFF` rồi trả về 0, không báo lỗi.