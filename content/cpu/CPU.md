---

---
# Hàm chính
- `run`: chạy process.
	- Kiểm tra xem program counter của process <= kích cỡ của text segment của process hay không, nếu không hợp lệ trả về 1 -> thất bại.
	- Bắt đầu lấy lệnh (dùng struct [[inst_t]]), tăng program counter, kiểm tra opcode, trả kết quả của hàm về biến `stat` (status):
		- `CALC`
		- `ALLOC`: cấp phát bộ nhớ, nếu cờ `MM_PAGING` được bật (phân trang RAM) thì dùng [[liballoc]], không thì dùng [[alloc]].
		- `FREE`: giải phóng bộ nhớ, tương tự với [[libfree]] và [[free_data]].
		- `READ`: đọc bộ nhớ, tương tự với [[libread]] và [[read]].
		- `WRITE`: ghi vào bộ nhớ, tương tự với [[libwrite]] và [[write]].
		- `SYSCALL`: [[libsyscall]].
	- Trả về biến `stat`.
### Hàm phụ (các lệnh CPU hỗ trợ)
- `calc`
- `alloc`: cấp phát bộ nhớ cho process `proc` (kích cỡ `size`, lưu vào thanh ghi `reg_index`) bằng hàm [[alloc_mem]]. Hàm trả về 0 nếu cấp phát thành công, địa chỉ sẽ nằm trong `proc->regs[reg_index]`, ngược lại trả về 1.
- `free_data`: sử dụng `free_mem` (lỗi thời) để giải phóng bộ nhớ của tiến trình `proc` tại địa chỉ lưu trong thanh ghi `proc->regs[reg_index]`.
- `read`: sử dụng hàm [[read_mem]] để đọc RAM tại địa chỉ `proc->regs[source] + offset` sử dụng bởi [[pcb_t]] `proc` và lưu vào `data`. Hàm trả về 0 nếu đọc thành công, 1 nếu thất bại.
- `write`: tương tự như `read` nhưng là ghi vào RAM.