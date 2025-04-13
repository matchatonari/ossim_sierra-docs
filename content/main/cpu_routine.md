Hoạt động của CPU.
# Tham số
- `void* args`: các tham số đầu vào muốn truyền cho CPU.
# Quá trình
- Lấy ra timer `timer_id` và mã CPU `id`.
- Tạo biến `time_left` là thời gian còn lại để xử lý process.
- Tạo con trỏ [[pcb_t]]* NULL để load process tiếp theo.
- Vào vòng lặp:
	- Nếu `proc == NULL`, lấy ra process tiếp theo từ hàng đợi bằng hàm `get_proc` (`sched.c`). Nếu `proc` vẫn NULL, tick timer bằng [[next_slot]].
	- Nếu `proc->pc == proc->code->size` (program counter chạy đến cuối code - hết process), in ra màn hình thông báo, giải phóng bộ nhớ của `proc`, dùng `get_proc` để lấy process mới, và đặt lại `time_left = 0`.
	- Nếu `time_left = 0` (hết thời gian xử lý), đưa nó trở lại hàng chờ, rồi lấy process khác.
	- Kiểm tra lại, nếu `proc == NULL` và `done` được bật thì thoát chương trình, CPU kết thúc.
		- Nếu biến `done` không được bật lên, chỉ tick qua bằng [[next_slot]] vì có thể có process trong hàng đợi.
	- Nếu `time_left == 0`, chuyển sang process khác, reset `time_left`.
	- Chạy process bằng hàm [[run]], giảm `time_left`, và tick timer bằng [[next_slot]].
- Kết thúc vòng lặp, hủy `timer_id` bằng [[detach_event]].
- Thoát xử lý bằng `pthread_exit`.