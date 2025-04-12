# Tham số
- [[pcb_t]]* `caller`: process gọi lệnh syscall.
- `uint32_t nr`
- [[sc_regs]]* `regs`: dữ liệu thanh ghi của process.
# Quá trình
- `switch nr`, `default` là gọi dummy systemcall `__sys_ni_syscall` (không làm gì cả).