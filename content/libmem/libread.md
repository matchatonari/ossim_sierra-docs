# Tham số
- [[pcb_t]] `proc`: process hiện tại.
- `uint32_t source`: index của thanh ghi nguồn.
- `uint32_t offset`: index của thanh ghi lưu offset. (địa chỉ nguồn = `[source]+[offset]`).
- `uint32_t* destination`: địa chỉ thanh ghi đích.
# Quá trình
- Khai báo một biến `data` để lưu dữ liệu trả về từ hàm [[__read]] và một biến `val` để kiểm tra xem truy vấn có thành công không.
- Ghi dữ liệu đọc được vào `destination`. Ngoài ra nếu các cờ sau đây được bật lên thì:
	- `IODUMP`: in ra màn hình và đẩy vào RAM giá trị đọc được.
	- `PAGETBL_DUMP`: in ra page table giá trị đọc được.
- Hàm trả về `val`.