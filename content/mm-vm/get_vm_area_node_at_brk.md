Cấp phát vùng nhớ cho một số trang.
# Tham số
- [[pcb_t]]* `caller`: process gọi lệnh.
- `int vmaid`: mã vùng VMA.
- `int size`: kích cỡ vùng nhớ cần cấp phát thêm.
- `int alignedsz`: trả về kích cỡ vùng nhớ thực tế, đúng với số trang.
# Quá trình
- Cấp phát vùng nhớ cho [[vm_rg_struct]]* `newrg`.
- Lấy VMA bằng [[get_vma_by_num]].
- Chỉnh sửa lại các giới hạn `newrg->rg_start`, `newrg->rg_end`...
- Trả về `newrg`.