# Tham số
- [[pcb_t]]* `proc`: process xin cấp phát bộ nhớ.
- `uint32_t size`: kích cỡ vùng nhớ muốn cấp phát.
- `uint32_t reg_index`: index của vùng nhớ muốn cấp phát trên.
# Quá trình
Sử dụng hàm [[__alloc]] để cấp phát bộ nhớ, tại vùng nhớ tương đối 0 (`vmaid` - ID vm area to alloc).