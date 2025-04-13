# Tham số
- `const char* path`: đường dẫn tới file config.
# Quá trình
- Mở file bằng `fopen`, nếu mở không được thì trả về -1.
- 3 dòng đầu sẽ là giá trị của `time_slot`, số CPU và số process, sử dụng `fscanf`.
- Cấp phát bộ nhớ cho [[ld_args]].
- Nếu `MM_PAGING` bật:
	- Nếu `MM_FIXED_MEMSZ` bật, ta sẽ tự đặt `memramsz`, `memswpsz`.
	- Ngược lại, ta sẽ đọc từ file config.
- Nếu `MLQ_SCHED` bật:
	- Cấp phát bộ nhớ cho `prio` trong [[ld_args]].
	- Lặp qua đủ số process, khởi tạo các `path[i]` là `input/proc/`, tiếp tục dùng `fscanf` để đưa vào `start_time`, `proc` và `prio`. Ngược lại chỉ cần đưa vào `start_time` và `proc`.
	- Dùng `strcat` để nối `/input/proc` với `proc`.