# Hằng số
- bus width: 22-bit (khoảng 4 MB)
- kích thước mỗi trang RAM là 256B.
- dung lượng RAM ảo là `BIT(21) = 1 << 21` byte = 2MB.
- dung lượng RAM swap là 512MB.
- địa chỉ của trang RAM trong swap bắt đầu từ bit 5 trở đi.
- số trang tối đa hỗ trợ (theo độ rộng của bus địa chỉ) là `1 << 22 / 256` = 16384 trang.
- kích thước bộ nhớ heap ban đầu của mỗi process là 256B (1 trang).
# Thông số bit
## Page table entry (PTE)
- Bit 31: đánh dấu trang có tồn tại, và có một FPN hợp lệ không.
- Bit 30: đánh dấu trang có mặt trong swap hay không.
- Bit 29: dự phòng.
- Bit 28: trang đó có bị thay đổi (dữ liệu chưa lưu chưa?) -> khi swap ra phải ghi lại.
- Bit 15-27: liên quan tới người dùng.
- Bit 14: empty01 - để dành.
- Bit 13: empty02 - để dành.
### Bitmask (để giải mã các thông số khác)
Dùng hàm [[GENMASK]] để sinh bitmask.
- USRNUM (user number): 15-27.
- `FPN` (frame page number): 0-12.
- `SWPTYP` (swap type): 0-4.
- `SWPOFF` (swap offset): 0-25.
## Địa chỉ
### Bitmask
- `ADDR_OFFST` (address offset): 0-7.
- `PGN` (page number): 0-21.
- `FRAME_PHY_NUM` (số khung trang vật lý) 0-7.
- `SWP`: 0-7.

# Thao tác `#define`
## PTE
- [[PAGING_PAGE_ALIGNSZ]]
- `PAGING_PTE_SET_PRESENT(pte)`: đặt bit 31.
- `PAGING_PAGE_PRESENT`: kiểm tra bit 31.
## Địa chỉ
- `PAGING_SWP`: `((pte & [SWPOFF]) >> 5)`.
- Các thao tác giải mã sau sử dụng [[GETVAL]] với các tham số `*_MASK` và `*_LOBIT`: `PAGING_OFFST`, `PAGING_PGN`, `PAGING_FPN`, `PAGING_PGN`, `PAGING_FPN`.
## Thao tác phạm vi vùng nhớ
- `INCLUDE`
- `OVERLAP`
---
# Thao tác `#define` khác
- [[SETBIT]]
- [[CLRBIT]]
- [[SETVAL]]
- [[GETVAL]]
# Các hàm
## VM region
- [[init_vm_rg]]
- [[enlist_vm_rgnode]]
- [[enlist_pgn_node]]
- [[vmap_page_range]]
- [[vm_map_ram]]
- [[alloc_pages_range]]
- [[__swap_cp_page]]
- [[pte_set_fpn]]
- [[pte_set_swap]]
- [[init_pte]]
- [[__alloc]]
- [[__free]]
- [[__read]]
- [[__write]]
- [[init_mm]]
## Local VM
- [[get_symrg_byid]]
- [[validate_overlap_vm_area]]
- [[get_free_vmrg_area]]
- [[inc_vma_limit]]
- [[find_victim_page]]
- [[get_vma_by_num]]
## MEMPHY
- [[MEMPHY_get_freefp]]
- [[MEMPHY_put_freefp]]
- [[MEMPHY_read]]
- [[MEMPHY_write]]
- `MEMPHY_dump`: in ra màn hình toàn bộ nội dung của [[memphy_struct]]`->storage`.
- [[init_memphy]]
## Print list
- `print_list_fp`, `print_list_rg`, `print_list_vma`, `print_list_pgn` lần lượt in ra các danh sách liên kết đơn [[framephy_struct]]\*, [[vm_rg_struct]]\*, [[vm_area_struct]]\*, [[pgn_t]]\*.
- [[print_pgtbl]]