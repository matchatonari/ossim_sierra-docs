Đại diện cho một hàng đợi process.
# Tham số
- [[pcb_t]]* `proc[MAX_QUEUE_SIZE]`: hàng đợi lưu các process.
- `int size`: số phần tử của hàng đợi.
# Các hàm
- `empty`: Hàng đợi `q` chỉ trống khi nó NULL hoặc `q->size == 0`.
- `enqueue`: đưa [[pcb_t]] vào hàng đợi.
- `dequeue`: lấy ra [[pcb_t]] có ưu tiên cao nhất rồi loại bỏ khỏi hàng đợi.