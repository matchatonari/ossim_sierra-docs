Tạo mới một đối tượng Memory Management.
# Tham số
- [[mm_struct]]* `mm`: giá trị trả về.
- [[pcb_t]]* `caller`: process gọi lệnh.
# Quá trình
- Tạo ra một [[vm_area_struct]]* `vma0` (mỗi process có ít nhất một VMA khi tạo).
- Cấp phát bộ nhớ cho `mm->pgd`.
- Đặt `vm_id = 0`, tạo VMA rỗng (tất cả bằng 0).
- Tạo mới một VM region mới, gọi [[init_vm_rg]] để khởi tạo. Cuối cùng là đưa vào trong danh sách quản lý của VMA.
- Khởi tạo con trỏ next... của VMA.
- Đặt bộ quản lý của VMA này là `mm`.
- Update `mmap` của `mm`...
- Trả về 0 để kết thúc.