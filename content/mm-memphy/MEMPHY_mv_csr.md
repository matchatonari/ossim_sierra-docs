Di chuyển con trỏ của [[memphy_struct]] đi một đoạn `offset`.
# Tham số
- [[memphy_struct]]* `mp`
- `int offset`
# Quá trình
- Gọi `numstep` là biến đếm, đặt `mp->cursor` tại 0, rồi liên tục kiểm tra xem `numstep` không vượt quá `offset` và `mp->maxsz` thì tăng `mp->cursor` lên (nếu vượt quá `maxsz` sẽ về lại 0) và `numstep`.
- Trả về 0 để kết thúc.