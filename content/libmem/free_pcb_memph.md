Thu hồi toàn bộ memphy của [[pcb_t]].
# Tham số
- [[pcb_t]]* `caller`: process cần lấy thông tin.
# Quá trình
- Tạo biến `pagenum` để lặp qua các trang, `fpn` để tính số khung trang, `pte` (page table entry) để lấy dữ liệu tạm thời.
- Gọi `PAGING_PAGE_PRESENT(pte)` = `pte & (1 << 31)` = bit 31. Nếu bit này bằng 1 thì trang có trong RAM, không thì trang này đã bị chuyển ra phần RAM swap.
- Nếu trang có trong RAM thì `fpn = PAGING_PTE_FPN(pte) = `[[GETVAL]]`(pte, PAGING_PTE_FPN_MASK, PAGING_PTE_FPN_LOBIT)` = [[GETVAL]](pte, [[GENMASK]](12, 0), 0) = `pte & (0xFFF)`, rồi đặt trang này vào trong `free_fp_list` của [[memphy_struct]] `caller->mram` bằng hàm [[MEMPHY_put_freefp]].
- Nếu trang không có trong RAM thì `fpn = PAGING_PTE_SWP(pte) =` [[GETVAL]](pte, [[GENMASK]](25, 5), 5) = `(pte & 0x1FFFFC0) >> 5` rồi đặt vào `free_fp_list` của [[memphy_struct]] `caller->active_mswp` bằng hàm [[MEMPHY_put_freefp]].