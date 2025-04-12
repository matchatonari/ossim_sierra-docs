# Tham số
- `int done`: cờ hoàn tất (do timer đã chạy xong)
- `int fsh`: cờ hoàn tất (do hoàn thành công việc).
- `pthread_cond_t event_cond`: Điều kiện đánh thức thread `event_lock` để tiếp tục xử lý sự kiện.
- `pthread_mutex_t event_lock`: Mutex xử lý sự kiện.
- `pthread_cond_t timer_cond`: Điều kiện đánh thức thread `timer_lock` để tiếp tục xử lý timer.
- `pthread_mutex_t timer_lock`: Mutex xử lý timer.