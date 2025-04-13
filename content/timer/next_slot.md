Báo hiệu với timer là đã hoàn thành xong công việc tại thời điểm hiện tại để chuyển qua tick tiếp theo.
# Tham số
- [[timer_id_t]]* `timer_id`: timer.
# Quá trình
1. Khóa `event_lock`lại. Đặt biến `done` của [[timer_id_t]] là 1. Đánh thức `event_cond` và mở khóa `event_lock`.
2. Khóa `timer_lock` lại. Đợi cho đến khi timer tick thì mở khóa `timer_lock` và kết thúc 1 tick của timer.