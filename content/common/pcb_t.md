Đại diện cho 1 process.
# Tham số
- `uint32_t pid`: Biến int 32-bit lưu mã process.
- `uint32_t priority`: Biến int 32-bit lưu độ ưu tiên (vị trí trong hàng đợi `ready_queue`).
- `char path[100]`: Lưu đường dẫn đến file thực thi process.
- [[code_seg_t]]* `code`: Đại diện cho code segment (phần nhị phân lưu code) của process.
- `addr_t regs[10]`: 10 thanh ghi int 32-bit cho phép lưu dữ liệu của process, dùng để lưu địa chỉ các vùng nhớ đã cấp phát.
- `uint32_t pc`: program counter, trỏ đến lệnh tiếp theo.
- [[queue_t]]* `ready_queue`: hàng đợi lưu các process đang ở trạng thái ready.
- [[queue_t]]* `running_list`: hàng đợi lưu các process đang chạy.
## Nếu cờ `MLQ_SCHED` (multi-level queue) được bật
- [[queue_t]]* `mlq_ready_queue`: hàng đợi multi-level queue để lưu các process đang ở trạng thái ready.
- `uint32_t prio`: biến 32-bit lưu độ ưu tiên (vị trí trong hàng đợi `mlq_ready_queue`).
## Nếu cờ `MM_PAGING` (sử dụng cơ chế paging của bộ nhớ) được bật
- [[mm_struct]]* `mm`: đối tượng quản lý vùng nhớ.
- [[memphy_struct]]* `mram`: RAM.
- [[memphy_struct]]** `mswap`: swap.
- [[memphy_struct]]* `active_mswap`: RAM swap đang hoạt động.
- `uint32_t active_mswap_id`: mã vùng swap đang hoạt động.