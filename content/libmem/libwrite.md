Ghi dữ liệu vào một vùng nhớ (có sử dụng phân trang).
# Tham số
- [[pcb_t]]* `proc`: process thực hiện lệnh.
- `BYTE data`: dữ liệu để ghi vào bộ nhớ.
- `uint32_t destination`: index của thanh ghi đích.
- `uint32_t offset`
# Quá trình
- Nếu cờ `IODUMP` được bật thì lệnh này sẽ xuất ra màn hình `destination`, `offset` và `data`, và dùng hàm `MEMPHY_dump` để ghi vào RAM.
- Nếu cờ `PAGETBL_DUMP` được bật thì máy sẽ chạy hàm [[print_pgtbl]] để ghi dữ liệu vào phân trang.
- Thực hiện lệnh chính là gọi hàm [[__write]].