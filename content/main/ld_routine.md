Hoạt động của loader.
# Tham số
- `void* args`: bất kì tham số gì truyền vào cho loader.
# Quá trình
- Nếu cờ `MM_PAGING` được bật, lần lượt lấy ra `mram`, `mswp`, `active_mswp`, `timer_id` từ [[mmpaging_ld_args]]. Ngược lại chỉ lấy ra `timer_id`.
- Vào vòng lặp, load process i `proc` bằng hàm [[load]], truyền đường dẫn vào bằng `path[i]`.
	- Nếu `MLQ_SCHED` bật thì truyền độ ưu tiên vào `proc`.
	- Nếu chưa đến lúc process chạy thì [[next_slot]].
	- Nếu `MM_PAGING` bật thì khởi tạo `proc->mm` bằng hàm [[init_mm]], `proc->mram`, `proc->mswap`, `proc->active_mswp`.
	- In ra màn hình thông báo load thành công, PID, độ ưu tiên. Thêm vào hàng đợi bằng `add_proc`, giải phóng `path[i]`, tăng i và [[next_slot]].
- Kết thúc vòng lặp, giải phóng toàn bộ [[mmpaging_ld_args]], đặt `done = 1`, hủy timer bằng [[detach_event]], thoát thread bằng `pthread_exit`.