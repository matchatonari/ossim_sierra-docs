# Tham số
- `x`: số để áp dụng bitmask.
# Quá trình
- `PAGING_PGN` sẽ gọi hàm [[GETVAL]]`(x,PAGING_PGN_MASK,PAGING_ADDR_PGN_LOBIT)` = `(x & 0xFFF00) >> 8`.
- `PAGING_PGN_MASK` = [[GENMASK]](`PAGING_ADDR_PGN_HIBIT`, `PAGING_ADDR_PGN_LOBIT`) = [[GENMASK]]`(21,`[[NBITS]]`(PAGING_PAGESZ))` = [[GENMASK]]`(21, 8)` = `0xFFF00`.
Tóm lại, giá trị trả về là `(addr & 0xFFF00) >> 8`.