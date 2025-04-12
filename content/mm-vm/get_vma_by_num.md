Trả về một phân vùng nhớ dựa trên mã ID.
# Tham số
- Con trỏ [[mm_struct]]* `mm`.
- `int vmaid` là ID vm to alloc.
# Quá trình
```cpp
struct vm_area_struct *get_vma_by_num(struct mm_struct *mm, int vmaid)
{
	struct vm_area_struct *pvma = mm->mmap;
	if (mm->mmap == NULL)
		return NULL;
	int vmait = pvma->vm_id;
	while (vmait < vmaid) {
		if (pvma == NULL)
			return NULL;
		pvma = pvma->vm_next;
		vmait = pvma->vm_id;
	}
	return pvma;
}
```

- Nếu `mm->mmap == NULL` (phân vùng nhớ `mm` không quản lý vùng nhớ nào kiểu [[vm_rg_struct]]) -> trả về NULL.
- Đặt `vmait` là mã vùng nhớ của `mm->mmap` (nếu không NULL).
- Vòng lặp while bắt đầu, truy ngược `vmait` về đến `vmaid` (`vmait` là vùng nhớ hiện tại, `vmaid` là vùng nhớ đích ta cần lấy, vì RAM trong BTL này được tổ chức phân cấp thành nhiều lớp).
	- Nếu trong quá trình truy đụng NULL (mà không đến được `vmaid`) -> trả về NULL.
	- Ngược lại kết quả trả về của hàm là vùng nhớ cần tìm.