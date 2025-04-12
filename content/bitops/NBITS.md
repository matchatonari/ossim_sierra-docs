# Tham số
- `n`: số cần tính.
# Tác dụng
Tính số bit cần thiết để biểu diễn `n` dưới dạng nhị phân.
- `NBITS2(n)`: nếu trả về 1 thì cần ít nhất 2 bit.
- `NBITS4(n)`: nếu trả về `2+NBITS2(n>>2)` (bật bit 1, đồng thời kiểm tra bit 2 và 3), không thì chỉ trả về `NBITS2(n)`.
Tương tự với `NBITS8(n)`, `NBITS16(n)`... tối đa 32 bit.
---
**Lưu ý:** Chỉ sử dụng `NBITS(n)` vì nó sẽ tự động gọi đệ quy đến các hàm con `NBITSx`.