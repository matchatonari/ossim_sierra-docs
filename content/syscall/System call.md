# Tổng quan
Sẽ có một **bảng lệnh syscall** map một con số và một hàm trong thư viện chuẩn.

# Làm sao để thêm một system call?
1. Tạo một file C mới.
2. Thêm file đó vào Makefile.
3. Thêm lệnh đó vào bảng syscall (id, tên và hàm gắn với nó).
# Danh sách
1. [[sys_killall.c]]