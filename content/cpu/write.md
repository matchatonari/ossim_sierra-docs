# Tham số
- [[pcb_t]]* `proc`: process gọi lệnh.
- `BYTE data`: dữ liệu muốn được ghi vào bộ nhớ.
- `uint32_t destination`: index của thanh ghi đích.
- `uint32_t offset`: offset.
# Quá trình
Gọi hàm `write_mem` (tương tự như [[read_mem]]) để ghi dữ liệu tại `proc->regs[destination] + offset`.