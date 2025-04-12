Ghi dữ liệu bộ nhớ tại địa chỉ cụ thể.
# Tham số
- [[pcb_t]]* `caller`: process gọi lệnh.
- `int vmaid`: ID vm area to alloc
- `int rgid`: region id
- `int offset`: offset
- `BYTE value`: giá trị được ghi vào
# Quá trình
- Lấy region ([[vm_rg_struct]]) bằng [[get_symrg_byid]].
- Lấy area ([[vm_area_struct]]) bằng [[get_vma_by_num]].
Nếu một trong hai bằng NULL thì hàm trả về -1 (thất bại).
Ngược lại ta dùng [[pg_setval]] để đặt giá trị vào RAM (phân trang). Trả về 0 (thành công).