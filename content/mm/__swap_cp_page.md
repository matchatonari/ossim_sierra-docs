Chuyển trang nhớ từ trang này sang trang khác.
# Tham số
- [[memphy_struct]]* `mpsrc`: source.
- [[memphy_struct]]* `mpdst`: destination.
- `int srcfpn`: số hiệu trang ở source.
- `int dstfpn`: số hiệu trang ở destination.
# Quá trình
- Lặp qua từng offset bằng biến `cellidx`:
	- `addrsrc = srcfpn * PAGING_PAGESZ + cellidx`.
	- `addrdst = dstfpn * PAGING_PAGESZ + cellidx`.
- Tạo 1 biến `data` kiểu `BYTE` để lưu dữ liệu đọc được từ source bằng hàm [[MEMPHY_read]] rồi viết lại vào destination bằng [[MEMPHY_write]].