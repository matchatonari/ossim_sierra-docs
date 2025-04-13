Đại diện cho một hàng chờ (nếu không định thời theo multi-level queue).
# Tham số
- `char**` path: mảng `char*` lưu đường dẫn của các process.
- `unsigned long* start_time`: thời gian đến (arrival time).
## Nếu cờ `MLQ_SCHED` được bật
- `unsigned long* prio`: độ ưu tiên.