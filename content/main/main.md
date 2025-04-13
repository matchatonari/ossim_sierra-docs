# Tham số
- `int argc`: số tham số dòng lệnh.
- `char* argv[]`: các tham số dòng lệnh.
# Quá trình
- Nếu `argc != 2`, trả về 1 -> sai cách gọi. Ngược lại sẽ đọc config bằng [[read_config]].
- Tạo luồng mới cho cpu ảo (`pthread_t`), cấp phát bộ nhớ cho thread và các [[cpu_args]], loader.
- Tạo các timer cho các cpu, mỗi cpu là 1 timer bằng [[attach_event]].
- Tạo thêm một timer cho loader (`ld_event`) và bắt đầu timer bằng [[start_timer]].
## Nếu `MM_PAGING` được bật
- Khởi tạo RAM và swap bằng [[init_memphy]], cho phép `rdmflg = 1`.
- Nếu sử dụng cơ chế phân trang thì các vùng nhớ của từng process phải được truyền thông qua loader, vì vậy phải tạo mới một [[mmpaging_ld_args]] `mm_ld_args` với đầy đủ `timer_id`, `mram`, `mswp`, `active_mswp` và `active_mswp_id`.
---
- Bắt đầu scheduler bằng [[init_scheduler]].
- Chạy loader bằng cách dùng `pthread_create` với [[ld_routine]] và `mm_ld_args` (nếu sử dụng phân trang), không thì chỉ cần truyền `ld_event` vào là đủ.
- Chạy các CPU bằng `pthread_create` với [[cpu_routine]] và các thông số trong [[cpu_args]] và `pthread_join`.
- Sau khi các threads kết thúc, dùng [[stop_timer]]. Trả về 0 để kết thúc chương trình.