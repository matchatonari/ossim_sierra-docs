# Tham số
- [[pcb_t]]* `proc`: process xin phép cấp phát bộ nhớ.
- `uint32_t size`: kích cỡ vùng nhớ được cấp phát.
- `uint32_t reg_index`: index của thanh ghi lưu địa chỉ vùng nhớ mới.
# Quá trình
Gọi hàm [[alloc_mem]] để lấy địa chỉ vùng nhớ mới. Nếu nhận được NULL thì trả về 1 (thất bại), không thì đặt địa chỉ vùng nhớ mới vào thanh ghi `reg_index` của process.