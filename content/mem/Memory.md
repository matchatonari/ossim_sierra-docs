# Biến toàn cục
- `BYTE _ram[1 << 20]`: RAM.
- `mem_stat[NUM_PAGES]` là một struct gồm có:
	- `uint32_t proc`: PID.
	- `int index`: index của trang hiện tại trong danh sách các trang trong RAM của process.
	- `int next`: trang tiếp theo, nếu là -1 thì `index` là trang cuối cùng.
# Các hàm
- `init_mem`: đặt `_ram` và `mem_stat` về 0 bằng `memset`, đồng thời khởi tạo khóa `mem_lock`.
- [[get_first_lv]], [[get_second_lv]]
- [[get_trans_table]]
- [[translate]]
- [[alloc_mem]]
- [[free_mem]]
- [[read_mem]], `write_mem`
- `dump`: lặp qua từng trang trong bộ nhớ RAM, nếu `proc != NULL` thì in ra PID, PID của process kế tiếp trên RAM, in ra bộ nhớ của process (`_ram` từ `i << 10` đến `(i + 1) << 10`).