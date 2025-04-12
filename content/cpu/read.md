# Tham số
- [[pcb_t]]* `proc`: process thực hiện lệnh đọc.
- `uint32_t source`: index của thanh ghi chứa địa chỉ nguồn.
- `uint32_t offset`: offset.
- `uint32_t destination`: index của thanh ghi đích.
# Quá trình
- Tạo biến `data` kiểu `BYTE` lưu giá trị trả về của hàm [[read_mem]], và đặt dữ liệu của `data` vào thanh ghi đích, trả về 0 (nếu thành công).
- Nếu thất bại, trả về 1.