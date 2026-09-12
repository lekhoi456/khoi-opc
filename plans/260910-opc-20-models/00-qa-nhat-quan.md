# BIÊN BẢN QA — Đối chiếu nhất quán 20 kế hoạch (pass 1, 10/09/2026)

> Phạm vi: 15/20 file đã hạ cánh. Sẽ cập nhật khi đủ 20.

## Phát hiện cần sửa ở pass cuối

1. **Tỷ giá không nhất quán:** `01` dùng 1 USD = 26.000 VND; `03`, `05` dùng 25.500 VND. → Ở pass cuối: chốt 1 tỷ giá chuẩn (đề xuất 25.500) và ghi chú ở đầu bộ tài liệu; không sửa số bên trong vì mọi kế hoạch đều đã tự đánh dấu ⚠️ số là ước lượng.
2. **Thông tư thuế hộ kinh doanh:** 4 file dùng **Thông tư 18/2026/TT-BTC** (mới); 2 file (`03`, `05`) vẫn nhắc **Thông tư 40/2021** (cũ). → Ở pass cuối: verify TT 18/2026 có thay thế TT 40/2021 không; nếu có, thêm ghi chú vào mục 12 của `03` và `05`. ⚠️ **Lưu ý bổ sung:** plan 17 đã verify Nghị quyết 198/2025/QH15 **bỏ thuế khoán từ 01/01/2026** → các file dùng "thuế khoán" cần ghi chú đối chiếu (đã note trong plan 17).
3. **Nghị định 13/2023/NĐ-CP:** 13/15 file nhắc tới ✅ — mức độ phủ tốt; 2 file không nhắc (`06`, `02` — do chủ yếu bán thị trường US, chấp nhận được nhưng nên bổ sung 1 dòng khi mở rộng về VN).

## Điểm mạnh thống kê

- 15/15 file đủ 11 mục template.
- 15/15 có mục kill/scale với ngưỡng định lượng cụ thể.
- Case TQ được dẫn lặp lại nhất: 光年易达 (7 file), 张顺 (5 file), 彭青云 (4 file) — đúng trọng tâm "tinh hoa người đi trước".
- Pattern "5 vị trí công việc AI" xuất hiện ở ≥10 file — đã thành chuẩn chung của bộ tài liệu.

## Việc còn lại

- [ ] Thu 5 file: 09, 13, 14, 17, 18
- [ ] Thu verify-pass (mục 12) cho 6 file Claude: 08, 10, 11, 12, 16, 20
- [ ] Pass cuối: chốt tỷ giá chuẩn + note TT 18/2026 vs 40/2021 + điền digest bảng mục 4 của `00-tong-ket-20-ke-hoach.md`
