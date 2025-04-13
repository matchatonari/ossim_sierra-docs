Khởi tạo hệ thống scheduler.
# Quá trình
- Nếu cờ `MLQ_SCHED` được bật, khởi tạo từng hàng đợi với size = 0, thời gian chạy (`slot[i]`) mặc định bằng `MAX_PRIO - i` (độ ưu tiên càng thấp, thời gian chạy càng ít).
- Không thì chỉ cần khởi tạo `ready_queue` và `run_queue` bằng cách đặt size = 0, và khởi tạo lock `queue_lock` bằng `pthread_mutex_init`.