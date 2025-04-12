Cấp phát bộ nhớ.
# Tham số
- [[pcb_t]]* `caller`: process xin cấp phát bộ nhớ.
- `int vmaid`: index của vùng nhớ sẽ chứa vùng nhớ mới.
- `int rgid`: region id (id vùng).
- `int size`: kích cỡ vùng nhớ muốn cấp phát.
- `int* alloc_addr`: địa chỉ vùng nhớ đã cấp phát (giá trị trả về).
# Quá trình
- Tạo một [[vm_rg_struct]] `rgnode` để lưu vùng nhớ mới.
- Nếu [[get_free_vmrg_area]] = 0 (thành công), thì lưu `rgnode` vào `caller->mm->symrgtbl` (symbol region table) (lưu `rg_start = *alloc_addr = rgnode.rg_start` và `rg_end = rgnode.rg_end`), mở khóa `mmvm_lock` và trả về 0.
- Nếu thất bại...
- Lấy lại vùng nhớ [[vm_area_struct]] hiện tại.
	```cpp
	struct vm_area_struct *cur_vma = get_vma_by_num(caller->mm, vmaid);
	```
- Tính số trang của bộ nhớ được cấp phát.
- Lấy lại `cur_vma->sbrk`.
- Gọi `sys_memmap` với `SYSMEM_INC_OP`, lưu các giá trị vào struct [[sc_regs]].
- `sys_memmap` (syscall 17)
- ...
- Trả lại địa chỉ đã được cấp phát qua biến `alloc_addr`.