# Các biến toàn cục
- `time_slot`: biến tĩnh lưu thời gian.
- `num_cpus`: biến tĩnh lưu số CPU.
- `done`: biến tĩnh lưu trạng thái hoàn tất xử lý.
### Nếu cờ `MM_PAGING` được bật
- `memramsz`: dung lượng RAM.
- `memswpsz[]`: dung lượng của các bộ nhớ swap (hỗ trợ tối đa 4).
# Các struct
- [[mmpaging_ld_args]]
- [[ld_args]]
- [[cpu_args]]
# Các hàm phụ
- [[cpu_routine]]
- [[ld_routine]]
- [[read_config]]
- [[main]]