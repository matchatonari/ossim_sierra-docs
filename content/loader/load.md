Tạo ra một process mới.
# Tham số
- `char* path`: đường dẫn đến file thực thi.
# Quá trình
- Tạo một [[pcb_t]]* `proc` mới: 
	- gắn PID cho nó, đồng thời tăng biến đếm PID lên 1.
	- tạo [[page_table_t]]* mới và gán vào `proc->page_table`.
	- gán base pointer `bp` = `1 << 10` và `pc` = 0.
- Mở file thực thi lên đọc code, nếu đọc không được (con trỏ `FILE*` NULL) thì thoát chương trình, mã -1.
- In ra đường dẫn tới process (ra stdin), tối đa `2 * sizeof(path) + 1` kí tự.
- Tạo [[code_seg_t]]* và gán vào `proc`.
- Cấp phát bộ nhớ cho các lệnh chỉ dẫn [[inst_t]] trong `proc->code->text`.
- Bắt đầu đọc opcode và đưa vào các `arg0...arg3` của [[inst_t]].
- Kết quả trả về là `proc`.