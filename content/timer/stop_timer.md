Dừng timer.
# Quá trình
- Đặt `timer_stop = 1`.
- Đợi cho đến khi timer dừng bằng `pthread_join`.
- Lặp qua các [[timer_id_container_t]] `dev_list`, hủy từng condition và mutex lock, rồi giải phóng danh sách liên kết đơn này.