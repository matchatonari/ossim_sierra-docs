Đại diện cho một vùng nhớ trên RAM.
# Tham số
- Con trỏ `BYTE* storage` lưu địa chỉ đầu nơi lưu trữ.
- `int maxsz` là dung lượng lưu trữ tối đa của vùng nhớ.
- `int rdmflg`: read mode flag.
- `int cursor`: lưu index hiện tại trên danh sách các frame bộ nhớ.
- [[framephy_struct]]* `free_fp_list`: danh sách các frame nhớ còn trống.
- [[framephy_struct]]* `used_fp_list`: danh sách các frame nhớ đang sử dụng.