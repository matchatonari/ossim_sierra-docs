Đại diện cho một vùng nhớ trên RAM vật lý.
# Tham số
- Con trỏ `BYTE* storage` lưu địa chỉ đầu nơi lưu trữ.
- `int maxsz` là dung lượng lưu trữ tối đa của vùng nhớ.
- `int rdmflg` (random flag): nếu cờ này bật lên thì vùng nhớ này không thể đọc được ngẫu nhiên mà chỉ có thể đọc lần lượt từ đầu tới cuối, và ngược lại.
- `int cursor`: lưu index hiện tại trên danh sách các frame bộ nhớ.
- [[framephy_struct]]* `free_fp_list`: danh sách các frame nhớ còn trống.
- [[framephy_struct]]* `used_fp_list`: danh sách các frame nhớ đang sử dụng.