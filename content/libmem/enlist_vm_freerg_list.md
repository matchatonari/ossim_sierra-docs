Thêm một vùng nhớ vào `freerg_list` (free region list).
# Tham số
- [[mm_struct]]* `mm`: memory manager.
- [[vm_rg_struct]]* `rg_elmt`: vùng nhớ cần được thêm vào danh sách.
# Quá trình
- Lấy head của danh sách liên kết đơn `vm_freerg_list` của `mm` là [[vm_rg_struct]]* `rg_node = mm->mmap->vm_freerg_list`.
- Nếu `rg_elmt->rg_start >= rg_elmt->rg_end` -> fail (-1).
- Nếu `rg_node` không NULL thì gắn thêm một node ở đầu là `rg_elmt`. Trả về 0 để kết thúc.