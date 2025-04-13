Tính số byte gần `sz` nhất mà có số trang không lẻ.
# Tham số
- `sz`: số byte.
# Quá trình
Thực hiện phép `sz / PAGING_PAGESZ` (dung lượng mỗi trang), làm tròn lên rồi nhân lại với `PAGING_PAGESZ`.