Khởi tạo một [[vm_rg_struct]]* `node` mới.
# Tham số
- `int rg_start`: địa chỉ bắt đầu vùng nhớ.
- `int rg_end`: địa chỉ kết thúc vùng nhớ.
# Quá trình
Tạo mới một [[vm_rg_struct]]* `rgnode` mới. Gán `rgnode->rg_start`, `rgnode->rg_end` cho nó và trả về `rgnode`.