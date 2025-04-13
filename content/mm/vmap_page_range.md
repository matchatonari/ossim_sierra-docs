Ánh xạ về danh sách các frame vật lý, trả về vùng địa chỉ ảo đã ánh xạ thành công ([[vm_rg_struct]]\*).
# Tham số
- [[pcb_t]]* `caller`: process gọi lệnh.
- `int addr`: địa chỉ đầu vùng nhớ muốn map.
- `int pgnum`: số trang ánh xạ.
- [[framephy_struct]]* `frames`: danh sách các frame ánh xạ.
- [[vm_rg_struct]]* `ret_rg`: vùng địa chỉ ảo đã map thành công.
# Quá trình
- Gán `rg_start` và `rg_end` của `ret_rg`.
- Map đoạn địa chỉ `[addr, addr + pgnum * PAGING_PAGESZ]` vào `caller->mm->pgd`.
- Cho vào danh sách trang bằng [[Memory manager#^7745e4|enlist_pgn_node]].
- Trả về 0 để kết thúc.