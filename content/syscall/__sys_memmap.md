Hàm quản lý bộ nhớ dựa theo opcode.
# Tham số
- [[pcb_t]]* `caller`: process gọi lệnh.
- [[sc_regs]]* `regs`: các tham số thanh ghi.
# Quá trình
- Opcode được lưu ở thanh ghi `a1`, dùng switch:
	- `SYSTEM_MAP_OP`: để dành.
	- `SYSTEM_INC_OP`: [[inc_vma_limit]]`(regs->a2, regs->a3)`.
	- `SYSTEM_SWP_OP`: [[__mm_swap_page]]`(regs->a2, regs->a3)`.
	- `SYSTEM_IO_READ`: [[MEMPHY_read]]`(caller->mram, regs->a2, &value)` và lưu `value` vào `a3`.
	- `SYSTEM_IO_WRITE`: [[MEMPHY_write]]`(caller->mram, regs->a2, regs->a3)`.
	- Trường hợp khác thì chỉ in ra màn hình.