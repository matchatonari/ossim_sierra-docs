# Tham số
- `addr_t virtual_addr`: địa chỉ tương đối theo process.
- `addr_t* physical_addr`: nơi lưu địa chỉ tuyệt đối.
- [[pcb_t]]* `proc`: process.
# Quá trình
- Sử dụng hàm `get_offset` (là một bitmask và bằng `0x3FF` hay 1023, AND với địa chỉ).
- Tìm ra số trang ở level 1 và level 2 của địa chỉ ảo bằng [[get_first_lv]] và [[get_second_lv]].
- Bắt đầu dò trong map [[trans_table_t]] bằng hàm [[get_trans_table]], nếu dò được NULL thì báo lỗi, không thể tìm được địa chỉ vật lý thỏa điều kiện.
- Nếu được (có index của level 1), tiếp tục dò trong `trans_table->table[i]` (là 1 map), kiểm tra xem có bằng với số trang ở level 2 không. Nếu được thì ghi lại địa chỉ vật lý vào `physical_addr` và trả về 1, không thì trả về 0, tìm kiếm thất bại.