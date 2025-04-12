Hàm liên kết với thread timer (những gì trong 1 tick timer sẽ làm).
# Biến
1. `fsh`: số công việc đã hoàn thành.
2. `event`: số công việc đã bắt đầu.
# Quá trình
1. In ra thời gian hiện tại (tick).
2. Ở đoạn này:
	```c
	/* Wait for all devices have done the job in current
	* time slot */
	struct timer_id_container_t * temp;
	for (temp = dev_list; temp != NULL; temp = temp->next) {
		pthread_mutex_lock(&temp->id.event_lock);
		while (!temp->id.done && !temp->id.fsh) {
			pthread_cond_wait(
				&temp->id.event_cond,
				&temp->id.event_lock
			);
		}
		if (temp->id.fsh) {
			fsh++;
		}
		event++;
		pthread_mutex_unlock(&temp->id.event_lock);
	}
	```
	Có thể đại diện bất kì một process nào là `temp`. Lần lượt lặp qua từng công việc, ta dùng mutex của `temp` để khóa vùng cấm địa lại, rồi chờ đến khi `&temp->id.event_cond` được kích hoạt (tính như 1 đơn vị thời gian), cuối cùng nếu công việc đã hoàn thành thì tăng biến đếm `fsh`, tăng biến đếm `event`, và mở khóa vùng cấm địa để `temp->next` có thể làm việc.
3. Tăng `_time`.
4. Vì đã qua time slot khác, tiếp tục thực hiện công việc: khóa vùng cấm địa, đặt biến `done` về 0, khởi chạy thread `timer` (để thực hiện phần ở trên), rồi mở khóa vùng cấm địa.
5. Nếu toàn bộ các công việc đã hoàn thành (`fsh == event`), thoát thread.