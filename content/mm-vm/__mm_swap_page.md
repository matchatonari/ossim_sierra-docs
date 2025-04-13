Là [[__swap_cp_page]] nhưng thực hiện trên RAM chính.
# Tham số
- [[pcb_t]]* `caller`: process gọi lệnh.
- `int vicfpn`: mã khung trang muốn chuyển sang swap.
- `int swpfpn`: mã khung trang trong swap làm đích đến.
# Quá trình
Gọi [[__swap_cp_page]]`(caller->mram, vicfpn, caller->activemswp, swpfpn)`.