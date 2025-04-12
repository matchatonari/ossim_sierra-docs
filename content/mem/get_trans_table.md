# Tham số
- `addr_t index`: index của segment trên bộ nhớ.
- [[page_table_t]]* `page_table`: danh sách liên kết đơn các frame của level 1.
# Quá trình
Lặp qua `page_table`, tìm đến index rồi trả về. Nếu không được, trả về NULL.