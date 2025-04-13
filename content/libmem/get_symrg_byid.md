Lấy symbol của VM region dựa trên ID của region
# Tham số
- Biến kiểu [[mm_struct]] (memory manager) là con trỏ `mm`.
- `int rgid`: region id.
# Quá trình
- Nếu region id < 0 hoặc lớn hơn `PAGING_MAX_SYMTBL_SZ` (paging max symbol table size): trả về NULL.
- Ngược lại, trả về `symrgtbl[rgid]` (symbol region table).