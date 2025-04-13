Là wrapper của [[vmap_page_range]]. Tạo ra các frame để [[vmap_page_range]] chạy được.
# Tham số
- [[pcb_t]]* `caller`: process gọi lệnh.
- `int astart`: địa chỉ bắt đầu của vm area
- `int aend`: địa chỉ kết thúc của vm area
- `int mapstart`: điểm bắt đầu map (tham số truyền vào [[vmap_page_range]]).
- `int incpgnum`: số trang cần cấp phát
- [[vm_rg_struct]]* `ret_rg`
# Quá trình
- Tạo [[framephy_struct]]* `frm_lst` để truyền vào [[vmap_page_range]].
- Tạo `ret_alloc` để lưu kết quả trả về từ hàm [[alloc_pages_range]]. Nếu `ret_alloc` âm và khác -3000 thì trả về -1 (lỗi).
- Nếu `ret_alloc = -3000` thì đó là lỗi hết bộ nhớ, nếu cờ `MMDBG` bật thì thông báo lỗi được đưa ra màn hình -> trả về -1 (lỗi).
- Ngược lại ta gọi [[vmap_page_range]].