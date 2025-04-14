# Tổng quan
- **Scheduler và Dispatcher**: quyết định xem process này chạy ở CPU nào.
- **RAM ảo**: ngăn cách vùng RAM của process này với vùng RAM của process khác. Dù là sử dụng kĩ thuật chia sẻ RAM nhưng mỗi process có một phần RAM của riêng nó -> hệ điều hành phải tự map về cho đúng ô nhớ của process.
# Code
## File tiêu đề
-  Tự hiểu: [[Timer|timer.h]], [[CPU|cpu.h]], [[queue_t|queue.h]],  [[Scheduler|sched.h]], `mem.h`.
- [[load|loader.h]] load code từ trong đĩa lên bộ nhớ.
- `common.h` -> hàm chung.
- `bitopts.h` -> thao tác bitwise.
- `os-mm.h`, `mm.h` -> quản lý RAM bằng cơ chế page.
- [[os-cfg|os-cfg.h]] -> config của hệ điều hành.
## File source
- Tự hiểu:`timer.c`, `cpu.c`, `queue.c`, `loader.c`, `sched.c`.
- `paging.c` Kiểm tra engine bộ nhớ ảo.
- `os.c`: hàm main.
- `mem.c`: bộ nhớ RAM ảo.
- `mm.c`, `mm-vm.c`, `mm-memphy.c` -> quản lý RAM bằng cơ chế page.
## Các file khác
- `syscalltbl.sh` parse lại file `syscall.tbl` thành `syscalltbl.lst` để chương trình đọc.

# Mục lục
1. [[CPU]]
2. [[Memory]]
3. [[Memory manager]]
4. [[Mạch chính]]
5. [[Scheduler]]
6. [[System call]]
