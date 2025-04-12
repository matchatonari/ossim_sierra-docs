Đọc dữ liệu bộ nhớ tại địa chỉ cụ thể.
# Tham số
- [[pcb_t]] caller`: process.
- `int vmaid`: virtual memory id.
- `int rgid`: mã register.
- `int offset`: offset
- `BYTE* data`: con trỏ trỏ đến nơi lưu data.
# Quá trình
- Con trỏ kiểu [[vm_rg_struct]] (virtual memory register) `currg` lưu kết quả trả về của hàm [[get_symrg_byid]].
- Con trỏ kiểu [[vm_area_struct]] `cur_vma` lưu kết quả trả về của [[get_vma_by_num]].
- Nếu `currg` hoặc `curvma` NULL thì coi như tìm kiếm vùng nhớ thất bại, trả về -1. Ngược lại ta sẽ tìm giá trị của block bằng hàm [[pg_getval]], kết quả sẽ được lưu vào vùng nhớ được trỏ tới bởi biến `data`.
- Hàm trả về 0 nếu truy vấn thành công, -1 nếu thất bại.