Đại diện cho một phân vùng bộ nhớ.

- Biến `int vm_id`: mã của phân vùng.
- Biến `int vm_start`: nơi bắt đầu của phân vùng.
- Biến `int vm_end`: nơi kết thúc phân vùng.
- Biến `int sbrk`.
- Con trỏ [[mm_struct]] `mm` trỏ đến memory manager.
- Con trỏ [[vm_rg_struct]] `vm_freerg_list` lưu các vùng nhớ đang rảnh.
- Con trỏ [[vm_area_struct]] lưu con trỏ trỏ tới phân vùng nhớ tiếp theo (các phân vùng liên kết với nhau như 1 danh sách liên kết đơn).