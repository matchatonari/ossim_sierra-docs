Hủy timer.
# Tham số
- [[timer_id_t]]* `event`: timer tick.

# Quá trình
Khóa `event_lock`, đặt `fsh` là 1. Đánh thức `event_lock` và mở khóa `event_lock`.