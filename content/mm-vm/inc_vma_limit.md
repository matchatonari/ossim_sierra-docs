Mở rộng VMA.
# Tham số
- [[pcb_t]]* `caller`
- `int vmaid`: ID vùng nhớ.
- `int inc_sz`: dung lượng cần tăng thêm.
# Quá trình
- Tạo mới vùng nhớ sắp được cấp phát [[vm_rg_struct]]* `newrg`.
- Căn chỉnh dung lượng (`inc_amt`) theo số trang bằng [[PAGING_PAGE_ALIGNSZ]].
- Tính số trang `incnumpage` = `inc_amt / PAGING_PAGESZ`.
- Tìm vùng nhớ [[vm_rg_struct]]* `area` đủ lớn cho số trang này bằng hàm [[get_vm_area_node_at_brk]].
- Lấy vùng nhớ [[vm_area_struct]]* `cur_vma` bằng hàm [[get_vma_by_num]].
- Lưu lại giá trị kết thúc cũ của VMA tại `old_end = cur_vma->vm_end`.
- Kiểm tra vùng nhớ hiện tại xem có bị chồng lấp không bằng hàm [[validate_overlap_vm_area]], nếu có thì trả về -1, cấp phát thất bại.
- Tăng vùng nhớ bằng cách sửa lại `cur_vma->vm_end`.
- Map vùng nhớ mới bằng hàm [[vm_map_ram]]. Nếu map thất bại (giá trị trả về âm) thì trả về -1, báo lỗi.
- Trả về 0 nếu không có chuyện gì xảy ra.