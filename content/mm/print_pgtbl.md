In bảng trang.
# Tham số
- [[pcb_t]]* `caller`: process gọi lệnh.
- `uint32_t start`: số trang bắt đầu.
- `uint32_t end`: số trang kết thúc.
# Quá trình
- Khai báo các biến `pgn_start` = [[PAGING_PGN]] `(start)`, `pgn_end` = [[PAGING_PGN]] `(end)`, `pgit` (int).
- Nếu `end = -1` nghĩa là in đến hết.
- In ra màn hình dòng giới thiệu `print_pgtbl: start - end`.
- Nếu `caller = NULL` -> trả về -1 (thất bại).
- Lặp qua từng trang (qua biến `pgit` từ `pgn_start` đến `pgn_end`), in ra offset của trang trong RAM và số thứ tự của nó. Trả về 0 để kết thúc.