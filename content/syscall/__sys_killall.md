Lệnh kill toàn bộ process trên hệ điều hành.
# Tham số
- `caller` là process control block (struct pcb_t).
- `regs` là con trỏ kiểu [[sc_regs]] để truyền thanh ghi vào.
# Biến cục bộ
- `char procname[100]`: tên process.
- `uint32_t data`: biến 32-bit tên `data`.
- `uint32_t memrg`: tạm thời đang bị hardcode là thanh ghi A1.

# Quá trình
```cpp
int i = 0;
data = 0;
while(data != -1){
	libread(caller, memrg, i, &data);
	proc_name[i]= data;
	if(data == -1) proc_name[i]='\0';
	i++;
}

printf("The procname retrieved from memregionid %d is \"%s\"\n", memrg, proc_name);
```
Vòng lặp while bắt đầu lặp qua từng thanh ghi và sử dụng hàm [[libread]] để lấy các thông tin về `caller` và đưa vào chuỗi `proc_name`. Nếu `data = -1` thì nghĩa là đã lặp qua toàn bộ các thanh ghi và thoát vòng lặp. Cuối cùng ta in ra màn hình tên process.

Cuối cùng ta lặp qua danh sách các process, kiểm tra và hủy toàn bộ tất cả các process tên `proc_name`. Hàm trả về 0 sau khi hoàn tất xử lý.