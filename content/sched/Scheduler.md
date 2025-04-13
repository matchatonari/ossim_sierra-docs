# Các biến toàn cục
- [[queue_t]] `ready_queue`
- [[queue_t]] `run_queue`
- `pthread_mutex_t queue_lock`
- [[queue_t]] `running_list`
## Nếu `MLQ_SCHED` được bật
- [[queue_t]] `mlq_ready_queue`
- `static int slot[MAX_PRIO]`
# Các hàm
- `queue_empty`: kiểm tra từng hàng theo mức ưu tiên với `MLQ_SCHED`, ngược lại chỉ cần kiểm tra `ready_queue` và `run_queue`.
- [[init_scheduler]]
- `get_proc`: đối với `MLQ_SCHED`, trả về `get_mlq_proc`. Ngược lại, phải thủ công lấy ra từ `ready_queue`.
- `put_proc`: đối với `MLQ_SCHED`, trả về `put_mlq_proc`/`add_mlq_proc`. Ngược lại, dùng [[enqueue]] để đưa process vào `run_queue`.
- `add_proc`: đối với `MLQ_SCHED`, trả về `put_mlq_proc`/`add_mlq_proc`. Ngược lại, dùng [[enqueue]] để đưa process vào `ready_queue`.
## Nếu `MLQ_SCHED` được bật
>Nhớ sử dụng lock để bảo vệ queue.
- `get_mlq_proc`: lấy process ra từ hàng đợi ưu tiên.
- `put_mlq_proc`/`add_mlq_proc`: sử dụng [[enqueue]] để đẩy process vào hàng đợi `mlq_ready_queue` với index là độ ưu tiên.