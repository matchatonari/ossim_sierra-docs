# Tham số
- [[pcb_t]]* `proc`: process xin được giải phóng bộ nhớ.
- `uint32_t reg_index`: mã vùng nhớ muốn giải phóng.
# Quá trình
- ...
- Sử dụng hàm [[__free]] để giải phóng vùng nhớ (tại `vmaid = 0`).