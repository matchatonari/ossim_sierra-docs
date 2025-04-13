# Tổng quan
Sẽ có một **bảng lệnh syscall** map một con số và một hàm trong thư viện chuẩn.

# Làm sao để thêm một system call?
1. Tạo một file C mới.
2. Thêm file đó vào Makefile.
3. Thêm lệnh đó vào bảng syscall (id, tên và hàm gắn với nó).
# Các lệnh tiền xử lý
- Đọc file `syscalltbl.lst`, đổi macro `__SYSCALL(nr, sym)` thành tên hàm tương ứng có 2 đối [[pcb_t]]* và [[sc_regs]]\*.
- Tạo bảng `sys_call_table` bằng cách parse macro theo định dạng `id-name`.
# Các struct & biến toàn cục
- [[sc_regs]]
- `extern const char* sys_call_table[]`: bảng lệnh syscall.
- `extern const int syscall_table_size`: độ dài bảng lệnh syscall.
# Các hàm
- [[syscall]]
- [[libsyscall]]
- `__sys_ni_syscall`: phế.
# Các lệnh của HDH
- [[__sys_killall]]
- `__sys_listsyscall`: in ra toàn bộ lệnh syscall trong bảng `sys_call_table`.
- [[__sys_memmap]]