Get a free vm region.
# Tham số
- [[pcb_t]]* `caller`: process gọi lệnh.
- `int vmaid`: số thứ tự vùng nhớ muốn tìm.
- `int size`: kích cỡ yêu cầu.
- [[vm_rg_struct]]* `new_rg`: vùng nhớ tìm được.
# Quá trình
- Lấy [[vm_area_struct]]* `cur_vma` bằng hàm [[get_vma_by_num]](`caller->mm, vmaid`).
- Lấy [[vm_rg_struct]]* `rgit` = `cur_vma->vm_free_rg_list`.
- Nếu `rgit == NULL` (không có vùng nhớ trống nào) -> trả về -1 (thất bại).
- Ngược lại, tìm một đoạn RAM liên tiếp trên RAM và đặt `new_rg->rg_start` và `new_rg->rg_end` vào đó. Trả về 0 để kết thúc.