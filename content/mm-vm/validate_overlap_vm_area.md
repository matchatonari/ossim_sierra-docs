Kiểm tra xem vùng nhớ được đưa vào có bị chồng lên nhau hay không.
# Tham số
- [[pcb_t]]* `caller`
- `int vmaid`: VMA id.
- `int vmastart`: địa chỉ bắt đầu VMA.
- `int vmaend`: địa chỉ kết thúc VMA.
# Quá trình
- Lấy [[vm_area_struct]]* `vma` = `caller->mm->mmap`.
- ...
- Trả về 0 để kết thúc.