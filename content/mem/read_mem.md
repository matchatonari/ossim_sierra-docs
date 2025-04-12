# Tham số
- `addr_t address`: địa chỉ (tương đối theo process).
- [[pcb_t]]* `proc`: process.
- `BYTE data`: nơi lưu dữ liệu.
# Quá trình
Sử dụng hàm [[translate]] để đổi địa chỉ tương đối theo process sang địa chỉ tuyệt đối theo RAM. Nếu hàm `translate` trả về 1 (thành công) thì lưu vào mảng `_ram` (RAM) tại địa chỉ vật lý vừa tính được và trả về 0 (thành công). Ngược lại trả về 1 (thất bại).