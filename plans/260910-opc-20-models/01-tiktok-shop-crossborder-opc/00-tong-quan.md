# 00 — TỔNG QUAN GÓI SÂU: TikTok Shop xuyên biên giới OPC

> Bộ tài liệu vận hành cấp cao cho mô hình 01 · Ngày: 2026-09-10 · Trạng thái: chờ người dùng duyệt chuẩn
> Kế hoạch gốc: `../01-tiktok-shop-crossborder-opc.md` · Tỷ giá chuẩn gói: 1 USD = 26.000 VND · Vốn trần 130 triệu

## 1. Bản đồ gói (đọc theo thứ tự nào)

| # | File | Dòng | Dùng khi |
|---|---|---|---|
| 00 | `00-tong-quan.md` (file này) | — | Trước khi bắt đầu: nắm tổng thể + các thay đổi so với kế hoạch gốc |
| 01 | `01-nghien-cuu-thi-truong.md` | 395 | Quyết định ngách + hiểu thị trường (117 link nguồn) |
| 02 | `02-mo-hinh-tai-chinh.md` | 406 | Dự toán tiền, điểm hoà vốn, độ nhạy — đọc kỹ trước khi bỏ vốn |
| 03 | `03-lich-trinh-26-tuan.md` | 634 | Lịch làm hằng tuần — mở cùng lúc khi bắt tay vào làm |
| 04 | `04-prompt-library.md` | 865 | Dán prompt cho 5 nhân viên AI (copy-paste chạy ngay) |
| 05 | `05-sop-checklist.md` | 374 | In ra dán tường kho — 12 SOP thao tác lặp |
| 06 | `06-ha-tang-va-du-lieu.md` | 451 | Cài n8n/Coze/Airtable/DeepSeek từng lệnh |
| 07 | `07-phap-ly-thue.md` | 317 | Đăng ký, thuế 2026, hợp đồng — làm trước tuần 1 |
| 08 | `08-rui-ro-va-kill-scale.md` | 324 | Giám sát hằng tuần; bảng kill/scale theo tháng |
| 09 | `09-kich-ban-outreach.md` | 207 | Mẫu tin chào KOC/đối tác — dùng từ tuần 3 |

**Tổng gói: 3.973 dòng (~400KB).** Mỗi file đọc độc lập được; các file khớp nhau qua "baseline chung" dưới đây.

## 2. Baseline chung của gói (đã cập nhật, khác kế hoạch gốc)

Kế hoạch gốc viết tháng 9/2026 nhưng một số số liệu đã lỗi thời ngay khi viết. Gói sâu đã cập nhật:

| Hạng mục | Kế hoạch gốc | Gói sâu (đã xác minh) | Nguồn |
|---|---|---|---|
| Hoa hồng bách hoá (ngách gợi ý) | 9–13% | **≤9,5% từ 03/07/2026** | Báo Công Thương (file 01) |
| VXP | 4% | **5%** | Báo Công Thương |
| Tổng phí sàn | ~15–19% | **~15,5%** (ngách bách hoá); trần sức khoẻ-làm đẹp 19,8% | file 01 |
| Phí giao dịch seller mới | 6% | **0% trong 60 ngày nếu mở shop trước 30/09/2026** (cap 1.200 USD) | file 01 |
| Thuế hộ kinh doanh | thuế khoán | **ĐÃ BỎ khoán từ 01/01/2026** (NQ198/2025/QH15): ≤200tr miễn thuế + kê khai 2 lần/năm; 200tr–3 tỷ: GTGT 1% + TNCN 0,5% kê khai quý; sàn TMĐT khấu trừ nộp thay | file 07 |
| Điểm hoà vốn | 45–50 đơn/tháng | **56 đơn/tháng** (tách thuế + dự phòng hoàn thành dòng riêng) | file 02 |

## 3. 3 bất nhất quán phát hiện khi chấm chéo — CẦN BẠN CHỐT

1. **Ngưỡng SCALE "lãi >1.500 USD/tháng" mâu thuẫn lộ trình mở US** (kịch bản cơ bản không bao giờ chạm 1.500 USD; kịch bản tốt chạm ~tháng 15–17 trong khi US mở tháng 7). → Đề xuất: SCALE VN = **lãi ≥20 triệu/tháng (≈770 USD) 3 tháng liên tiếp**; giữ 1.500 USD làm ngưỡng SCALE cho giai đoạn US.
2. **Ngưỡng KILL "lỗ 3.000 USD" quá rộng** (kịch bản tệ 12 tháng chỉ lỗ ~610 USD → gần như không bao giờ kích hoạt). → Đề xuất: KILL = **lỗ luỹ kế >1.500 USD** hoặc <30 đơn/tháng ở tuần 12.
3. **Dự phòng 35tr "vừa khít" khi mở US** (LLC 12,9tr + logistics 5tr + tồn kho US 8–13tr ≈ 26–31tr). → Đề xuất: giữ nguyên 35tr nhưng chỉ GO-US khi VN lãi ≥2 tháng liên tiếp VÀ dự phòng còn nguyên ≥25tr (đã ghi trong file 03 tuần 17–18).

## 4. Điều hành viên đã duyệt gì (checklist QA)

- [x] 9/9 file đúng tên, đúng thư mục, đủ mục
- [x] Mọi file có mục "Thay đổi so với baseline" + "Câu hỏi mở"
- [x] Mọi số liệu ngoài baseline có link + ngày truy cập (file 01: 117 link)
- [x] Không phát hiện số bịa — chỗ không có nguồn đều gắn ⚠️
- [x] 4 phát hiện nâng cấp: ưu đãi phí 0% (mở shop ngay tháng 9/2026), phí bách hoá giảm, chuỗi thuế hậu NQ198, cảnh báo Form 5472 $25k/năm

## 5. Việc tiếp theo

1. **Bạn duyệt gói này** — đọc 00→02→03 trước; góp ý gì tôi sửa ngay.
2. Sau khi chuẩn hoá: tôi nhân bản đúng quy trình (6 chuyên gia × baseline chung × QA chéo) cho 19 mô hình còn lại, theo thứ tự ưu tiên trong `../00-tong-ket-20-ke-hoach.md`.
