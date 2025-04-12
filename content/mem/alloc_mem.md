Cấp phát bộ nhớ và trả về địa chỉ (kiểu `int`).
# Quá trình
1. Khóa vùng cấm địa (`mem_lock`).
2. Tính số frame bộ nhớ trên RAM cần sử dụng.
3. Kiểm tra xem trong vùng địa chỉ ảo (virtual address space) và vùng địa chỉ vật lý (physical address space) còn đủ `size` chỗ trống không, nếu còn, đặt `mem_avail` bằng 1.
4. Nếu `mem_avail = 1`, đẩy base pointer `bp` lên. Cập nhật lại vùng vật lý.
5. Mở khóa và trả về địa chỉ của vùng nhớ mới được cấp phát.