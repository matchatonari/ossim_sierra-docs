Là [[SETBIT]] nhưng thực hiện trên vùng bit nhất định (dịch phải một đoạn `offst`).
# Tham số
- `v` là giá trị hiện tại.
- `value` là giá trị sắp được gán vào `v`.
- `mask`
- `offst`
# Quá trình
- Xóa sạch vùng bit sắp thay đổi bằng cách thực hiện `v = (v & ~mask)`.
- Dời `value` đi một đoạn `offst` để giữ nguyên các bit dưới của `v`.
- Ghép lại bằng toán tử OR.