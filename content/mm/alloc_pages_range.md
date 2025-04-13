# Tham số
- [[pcb_t]]* `caller`: process gọi lệnh.
- `int req_pgnum`: số trang cần map.
- [[framephy_struct]]** `frm_lst`: danh sách frame vật lý sau map.
# Quá trình
Lặp qua các trang cần cấp phát. Nếu [[MEMPHY_get_freefp]] từ `mram` của `caller` trả về 0 (thành công), thì lưu lại `fpn` mới vào `newfp_str`. Nếu không thì báo lỗi.

Nếu mọi việc hoàn thành tốt đẹp, trả về `frm_lst` và 0.