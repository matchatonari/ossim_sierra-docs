Gom lại để dễ dàng load vào trong [[load|loader]].
# Tham số
- `int vmemsz`: dung lượng bộ nhớ ảo.
- [[memphy_struct]]* `mram`: RAM vật lý.
- [[memphy_struct]]** `mswap`: swap (trong trường hợp có nhiều bộ nhớ swap).
- [[memphy_struct]]* `active_mswp`: các bộ nhớ swap đang hoạt động.
- `int active_mswp_id`: ID của swap đang dùng hiện tại.
- [[timer_id_t]]: timer.