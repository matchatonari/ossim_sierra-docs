# Tham số
- [[pcb_t]]* `caller`: process chạy lệnh `syscall`.
- `uint32_t syscall_idx`: mã lệnh syscall.
- `uint32_t a1, a2, a3`: các giá trị để đưa vào các thanh ghi `a1, a2, a3` trong struct [[sc_regs]].
# Quá trình
Gọi [[syscall/syscall]] với các tham số thanh ghi như trên.