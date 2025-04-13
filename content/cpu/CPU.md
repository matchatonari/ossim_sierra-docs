---

---
# Hàm chính
- [[run]]
### Hàm phụ (các lệnh CPU hỗ trợ)
- `calc`
- `alloc`: cấp phát bộ nhớ cho process `proc` (kích cỡ `size`, lưu vào thanh ghi `reg_index`) bằng hàm [[alloc_mem]]. Hàm trả về 0 nếu cấp phát thành công, địa chỉ sẽ nằm trong `proc->regs[reg_index]`, ngược lại trả về 1.
- `free_data`: sử dụng `free_mem` (lỗi thời) để giải phóng bộ nhớ của tiến trình `proc` tại địa chỉ lưu trong thanh ghi `proc->regs[reg_index]`.
- `read`: sử dụng hàm [[read_mem]] để đọc RAM tại địa chỉ `proc->regs[source] + offset` sử dụng bởi [[pcb_t]] `proc` và lưu vào `data`. Hàm trả về 0 nếu đọc thành công, 1 nếu thất bại.
- `write`: tương tự như `read` nhưng là ghi vào RAM.