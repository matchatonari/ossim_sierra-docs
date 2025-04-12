Đại diện cho một lớp quản lý phân vùng nhớ (manager).
# Tham số
- Con trỏ số nguyên 32-bit `pgd` (page data, như số thứ tự).
- Con trỏ `mmap` kiểu [[vm_area_struct]] (đại diện cho một phân vùng bộ nhớ).
- Mảng các vùng nhớ do struct này quản lý `symrgtbl` kiểu [[vm_rg_struct]].
- Con trỏ danh sách liên kết đơn [[pgn_t]] `fifo_pgn`.