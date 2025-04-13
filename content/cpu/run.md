Chạy process.
# Tham số
- [[pcb_t]]* `proc`: process đang xử lý.
# Quá trình
- Kiểm tra xem program counter của process <= kích cỡ của text segment của process hay không, nếu không hợp lệ trả về 1 -> thất bại.
- Bắt đầu lấy lệnh (dùng struct [[inst_t]]), tăng program counter, kiểm tra opcode, trả kết quả của hàm về biến `stat` (status):
	- `CALC`
	- `ALLOC`: cấp phát bộ nhớ, nếu cờ `MM_PAGING` được bật (phân trang RAM) thì dùng [[liballoc]], không thì dùng [[alloc]].
	- `FREE`: giải phóng bộ nhớ, tương tự với [[libfree]] và [[free_data]].
	- `READ`: đọc bộ nhớ, tương tự với [[libread]] và [[read]].
	- `WRITE`: ghi vào bộ nhớ, tương tự với [[libwrite]] và [[write]].
	- `SYSCALL`: [[libsyscall]].
- Trả về biến `stat`.