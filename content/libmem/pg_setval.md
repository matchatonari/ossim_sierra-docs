# Tham số
- [[mm_struct]]* `mm` -> memory manager.
- `int addr`: địa chỉ.
- `BYTE value`: giá trị cần set.
- [[pcb_t]]* `caller`: process gọi lệnh.
# Quá trình
- Tìm ra số trang (page number) bằng [[PAGING_PGN]].
- Có thể tiếp tục tìm offset bằng cách thao tác với một bitmask nào đó (`PAGING_OFFSET`).
- Tìm khung trang (`fpn`) bằng cách dùng [[pg_getpage]]. Nếu hàm này trả về khác 0, trả về -1 (invalid page access).
- MEMPHY_WRITE...
- Sử dụng [[sc_regs]] để thêm dữ liệu vào thanh ghi.
- Sử dụng syscall 17.
- Update `data` và trả về 0 để kết thúc.