# Struct
1. [[timer_id_t]]
2. `timer_id_container_t`: là struct danh sách liên kết đơn của các [[timer_id_t]].
# Hàm
1. `start_timer`: tạo một thread mới tên `timer` chạy [[timer_routine]]
2. `stop_timer`: dừng timer, hủy toàn bộ lock + mutex, giải phóng bộ nhớ.
3. `attach_event`: tạo event mới. Nếu đang ở giữa tick thì không chấp nhận, hủy bỏ thao tác, ngược lại thì khởi tạo `timer_id_t` mới, các mutex lock và condition, cuối cùng là thêm vào danh sách `dev_list` (toàn cục) (theo kiểu LIFO - stack).
4. `detach_event`: hủy event. khóa `event_lock`, đặt `fsh` là 1, đánh thức `event_lock` và mở khóa `event_lock`.
5. `next_slot`
	1. Khóa `event_lock`lại. Đặt biến `done` của [[timer_id_t]] là 1. Đánh thức `event_cond` và mở khóa `event_lock`.
	2. Khóa `timer_lock` lại. Đợi cho đến khi timer tick thì mở khóa `timer_lock` và kết thúc 1 tick của timer.
6. `current_time`: trả về `_time`.