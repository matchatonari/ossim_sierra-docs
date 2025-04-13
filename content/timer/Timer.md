# Struct
1. [[timer_id_t]]
2. `timer_id_container_t`: là struct danh sách liên kết đơn của các [[timer_id_t]].
# Hàm
1. [[start_timer]]
2. [[stop_timer]]
3. `stop_timer`: dừng timer, hủy toàn bộ lock + mutex, giải phóng bộ nhớ.
4. [[attach_event]]
5. [[detach_event]]
6. [[next_slot]]
7. `current_time`: trả về `_time`.