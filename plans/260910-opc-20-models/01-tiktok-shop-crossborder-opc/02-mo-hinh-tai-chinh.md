# 02. Mô hình tài chính — TikTok Shop xuyên biên giới full-AI (OPC)

> Kèm kế hoạch 01 · Model phụ trách: DeepSeek · Ngày: 2026-09-10 · Trạng thái: draft
> Quy ước: ✅ = có nguồn (xem mục 10) · ⚠️ = số nội bộ/tự đặt, chưa xác minh độc lập · "tr" = triệu VND · tỷ giá mặc định 1 USD = 26.000 VND ⚠️.
> Mọi số dưới đây dùng **baseline**: AOV 250.000đ, giá vốn 40%, phí sàn 15–19% (dùng 17% cho tính toán), ads+affiliate 10%, fulfillment 15.000đ/đơn ⚠️, vốn trần 5.000 USD ≈ 130tr, ngân sách 6 tháng ≈110tr.

## 0. Tóm tắt điều hành (số khoá)

| Chỉ số | Giá trị | Ghi chú |
|---|---|---|
| **Lãi ròng/đơn** (cơ bản, tại 200 đơn/tháng) | **≈38.750đ (15,5% doanh thu)** | sau khi phân bổ phí cố định; tại 230 đơn/tháng = 40.700đ (16,3%) |
| Biên đóng góp (contribution margin)/đơn | 53.750đ (21,5%) | doanh thu − toàn bộ biến phí |
| Tổng "ăn mòn" biên | 78,5% doanh thu | phí sàn 17% + giá vốn 40% + ads/aff 10% + fulfillment + hoàn DP + thuế |
| Điểm hoà vốn | **56 đơn/tháng ≈ 14,0tr doanh thu** | baseline ghi 45–50 đơn — xem mục 5 & 8 giải thích chênh |
| Thu hồi vốn (payback) kịch bản cơ bản | tháng 7 (luỹ kế dương) | đáy lỗ luỹ kế −11,4tr ở T3 |
| Đáy tiền mặt 6 tháng đầu (cơ bản) | ≈56,4tr (tuần 20) | ngân sách 110tr → không đứt nếu payout đúng chu kỳ |
| KILL ngày 90 (baseline) | <30 đơn/tháng VÀ lỗ luỹ kế >3.000 USD | ⚠️ ngưỡng lỗ 3.000 USD quá cao so với ngân sách VN — kiến nghị hạ (mục 8) |
| SCALE (baseline) | lãi >1.500 USD/tháng × 3 tháng liên tiếp | trong kịch bản Tốt đạt ~T15–17; mâu thuẫn với lộ trình mở US — mục 8 |
| **3 giả định rủi ro nhất** | (1) tỷ lệ hoàn thực tế (5% vs 15–30%); (2) phí sàn tiếp tục tăng lên 25%; (3) giá vốn 40% thực tế khó giữ khi cộng đủ phí order + ship + kiểm đếm | xem mục 3 |

---

## 1. Đơn vị kinh tế 1 đơn hàng (unit economics)

### 1.1 Bảng chi tiết từng khoản — đơn chuẩn AOV 250.000đ

| # | Khoản mục | Công thức | Giá trị (đ) | % DT | Nguồn |
|---|---|---|---|---|---|
| 1 | **Giá bán (AOV)** | P | 250.000 | 100% | baseline |
| 2 | **Giá vốn (COGS)** | 40% × P | 100.000 | 40,0% | baseline; gồm: giá 1688 + phí mua hộ từ 1% [thuongdo] + ship nội địa TQ + vận chuyển TQ→VN từ 4.000đ/kg [thuongdo] + kiểm đếm (tuỳ chọn) |
| 3 | Phí giao dịch | 6% × P | 15.000 | 6,0% | ✅ Báo Công Thương (biểu phí từ 09/05/2026) |
| 4 | Hoa hồng nền tảng | 11% × P (dải 9–14%) | 27.500 | 11,0% | ✅ Báo Công Thương; dùng trung vị ngách bách hoá 9–13% |
| 5 | VXP (voucher người bán tài trợ) | 4% × P, tối đa 50.000đ/sp | **0 (tắt)** | 0% | ✅ Báo Công Thương; tự nguyện — tắt giai đoạn đầu |
| 6 | Hoa hồng affiliate | 5% × P | 12.500 | 5,0% | baseline (mở affiliate 10–15% cho SKU chạy — 5% là trung bình giả định) ⚠️ |
| 7 | Quảng cáo Shop Ads | 5% × P | 12.500 | 5,0% | baseline (ads+affiliate 10% chung) |
| 8 | Fulfillment | cố định 15.000đ/đơn | 15.000 | 6,0% | ⚠️ baseline (đóng gói + giao nội địa VN) |
| 9 | Dự phòng hoàn trả | 5% × (P − 50.000) | 10.000 | 4,0% | ⚠️ mỗi đơn hoàn mất ≈P − 50k thu hồi ròng (giá vốn 100k − ship 2 chiều ~30k − hao mòn 20k); KPI baseline: hoàn <5% |
| 10 | Thuế (GTGT + TNCN) | 1,5% × P = 1% + 0,5% | 3.750 | 1,5% | ✅ NĐ 117/2025: sàn TMĐT khấu trừ, nộp thay từ 1/7/2025 (hàng hoá: GTGT 1%, TNCN cá nhân cư trú 0,5%) |
| | **Tổng biến phí** | Σ dòng 2–10 | **196.250** | **78,5%** | |
| | **Biên đóng góp (CM)** | P − tổng biến phí | **53.750** | **21,5%** | |
| 11 | Phí cố định phân bổ | 3.000.000 ÷ số đơn/tháng | tại 56 đơn: 53.571 · tại 200 đơn: 15.000 · tại 230 đơn: 13.043 | | ⚠️ baseline: tools 2tr + kho/vận hành 1tr/tháng |
| | **Lãi ròng/đơn** | CM − phí cố định phân bổ | **tại 200 đơn/tháng: 38.750 (15,5%)** · tại 230: 40.707 (16,3%) | | |

**Công thức tổng quát định giá (dùng cho AI上架师):**

```
Biến phí theo % doanh thu = GT 6% + HH 11% + affiliate 5% + ads 5% + hoàn DP 4% + thuế 1,5% = 32,5%
P_min = (Giá vốn tuyệt đối + 15.000 + CM mục tiêu) / (1 − 0,325) = (GV_abs + 15.000 + CM_mục tiêu) / 0,675
```

- Với GV_abs = 100.000 và CM mục tiêu 53.750 → P_min = 168.750/0,675 = **250.000đ** ✅ khớp bảng trên.
- Quy tắc baseline "giá bán = giá vốn ×3": GV_abs = 83.333 → CM = 0,675×250.000 − 98.333 = **70.400đ/đơn (28,2%)** → BEP chỉ còn 43 đơn/tháng. Đây chính là lý do baseline tính BEP 45–50 đơn (xem mục 5, 8).

### 1.2 Các biến thể quan trọng của 1 đơn

| Biến thể | Thay đổi so với chuẩn | CM/đơn | Lãi ròng/đơn (tại 230 đơn) |
|---|---|---|---|
| Bật VXP 4% | +10.000đ biến phí | 43.750đ | 30.707đ (12,3%) |
| Giá vốn trượt lên 45% (112.500đ) | +12.500đ | 41.250đ | 28.207đ (11,3%) |
| Markup 3× (GV 83.333đ, P giữ 250k) | −16.667đ | 70.417đ | 57.374đ (22,9%) |
| Tăng giá lên 300k (GV giữ 100k) | phí % theo giá tăng | 87.000đ | 73.957đ (24,7%) |

→ **Kết luận vận hành:** ngách phải chọn được sản phẩm có thể bán ở markup ≥2,8–3× (giá vốn ≤33–36%) thì mới đạt lãi ròng ≥20%; mô hình baseline 40% giá vốn chỉ cho lãi ròng 15–16% — mỏng, không có đệm cho sai số.

---

## 2. P&L 24 tháng — 3 kịch bản

### 2.0 Giả định từng kịch bản

| Kịch bản | Xác suất ⚠️ | AOV | Hoàn | Ads | Affiliate | Đơn/tháng (T1 → T6 → T12 → T24) | Ghi chú |
|---|---|---|---|---|---|---|---|
| Tệ | 30% | 230.000đ (giảm giá kéo đơn) | 15% | 10% | 5% | 15 → 20 → 25 → KILL T4 | content không chạy, đốt ads, khuyến mãi sâu |
| Cơ bản | 50% | 250.000đ | 5% | 5% | 5% | 20 → 140 → 230 → 370 | theo đúng đường tăng trưởng kế hoạch 01 |
| Tốt | 20% | VN 250.000đ · US $30 (780.000đ) | 5% | VN 5% · US 10% | VN 5% · US 10% | VN 40 → 240 → 520 → 760 · US 0 → 0 → 100 → 340 | mở US từ T7 (LLC T3, 3PL T6) |

Giả định chung: phí cố định VN 3tr/tháng (tools 2tr + kho/vận hành 1tr) ⚠️; one-time T1 8tr (giấy tờ/thiết bị quay — baseline); phí sàn 17%; thuế 1,5% khấu trừ tại nguồn ✅; tỷ giá 26.000 ⚠️. US: referral 6% ✅, 3PL $4,5/đơn ⚠️, phí cố định US $150/tháng (≈3,9tr) ⚠️, one-time LLC $497 ≈ 12,9tr (T3) + setup logistics 5tr (T6).

### 2.1 Kịch bản TỆ (xác suất chủ quan 30% ⚠️) — AOV 230k, hoàn 15%, ads 10%, KILL ở T4

| T | Đơn | DT (tr) | Giá vốn (tr) | Phí sàn (tr) | Ads/Aff (tr) | Fulfill (tr) | Hoàn DP (tr) | Thuế (tr) | Cố định (tr) | Lãi ròng (tr) | Luỹ kế (tr) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 15 | 3.45 | 1.38 | 0.59 | 0.52 | 0.23 | 0.41 | 0.05 | 11.00 | -10.72 | -10.72 |
| 2 | 20 | 4.60 | 1.84 | 0.78 | 0.69 | 0.30 | 0.54 | 0.07 | 3.00 | -2.62 | -13.34 |
| 3 | 25 | 5.75 | 2.30 | 0.98 | 0.86 | 0.38 | 0.68 | 0.09 | 3.00 | -2.53 | -15.86 |
| 4 | KILL | — | — | — | — | — | — | — | −2,0 (thanh lý tồn) | −2,0 | -17.86 |
| 5–24 | — | dừng/đổi ngách | | | | | | | | | |

⚠️ Lưu ý kill: luỹ kế T3 = −15,9tr ≈ **−610 USD** — chưa chạm ngưỡng "lỗ >3.000 USD" của baseline (điều kiện VÀ). Chỉ điều kiện đơn <30 được thoả → kiến nghị kill theo tinh thần "sai thì bỏ trong vài tuần" (景行) hoặc hạ ngưỡng lỗ xuống 1.500 USD (mục 8).

### 2.2 Kịch bản CƠ BẢN (xác suất chủ quan 50% ⚠️) — AOV 250k, đơn/tháng tăng dần

| T | Đơn | DT (tr) | Giá vốn (tr) | Phí sàn (tr) | Ads/Aff (tr) | Fulfill (tr) | Hoàn DP (tr) | Thuế (tr) | Cố định (tr) | Lãi ròng (tr) | Luỹ kế (tr) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 20 | 5.00 | 2.00 | 0.85 | 0.50 | 0.30 | 0.20 | 0.07 | 11.00 | -9.93 | -9.93 |
| 2 | 35 | 8.75 | 3.50 | 1.49 | 0.88 | 0.53 | 0.35 | 0.13 | 3.00 | -1.12 | -11.04 |
| 3 | 50 | 12.50 | 5.00 | 2.12 | 1.25 | 0.75 | 0.50 | 0.19 | 3.00 | -0.31 | -11.36 |
| 4 | 80 | 20.00 | 8.00 | 3.40 | 2.00 | 1.20 | 0.80 | 0.30 | 3.00 | 1.30 | -10.06 |
| 5 | 110 | 27.50 | 11.00 | 4.68 | 2.75 | 1.65 | 1.10 | 0.41 | 3.00 | 2.91 | -7.14 |
| 6 | 140 | 35.00 | 14.00 | 5.95 | 3.50 | 2.10 | 1.40 | 0.53 | 3.00 | 4.53 | -2.62 |
| 7 | 150 | 37.50 | 15.00 | 6.38 | 3.75 | 2.25 | 1.50 | 0.56 | 3.00 | 5.06 | 2.44 |
| 8 | 165 | 41.25 | 16.50 | 7.01 | 4.12 | 2.48 | 1.65 | 0.62 | 3.00 | 5.87 | 8.31 |
| 9 | 180 | 45.00 | 18.00 | 7.65 | 4.50 | 2.70 | 1.80 | 0.67 | 3.00 | 6.68 | 14.99 |
| 10 | 200 | 50.00 | 20.00 | 8.50 | 5.00 | 3.00 | 2.00 | 0.75 | 3.00 | 7.75 | 22.74 |
| 11 | 215 | 53.75 | 21.50 | 9.14 | 5.38 | 3.23 | 2.15 | 0.81 | 3.00 | 8.56 | 31.29 |
| 12 | 230 | 57.50 | 23.00 | 9.78 | 5.75 | 3.45 | 2.30 | 0.86 | 3.00 | 9.36 | 40.66 |
| 13 | 245 | 61.25 | 24.50 | 10.41 | 6.12 | 3.67 | 2.45 | 0.92 | 3.00 | 10.17 | 50.83 |
| 14 | 260 | 65.00 | 26.00 | 11.05 | 6.50 | 3.90 | 2.60 | 0.97 | 3.00 | 10.98 | 61.80 |
| 15 | 275 | 68.75 | 27.50 | 11.69 | 6.88 | 4.12 | 2.75 | 1.03 | 3.00 | 11.78 | 73.58 |
| 16 | 290 | 72.50 | 29.00 | 12.33 | 7.25 | 4.35 | 2.90 | 1.09 | 3.00 | 12.59 | 86.17 |
| 17 | 300 | 75.00 | 30.00 | 12.75 | 7.50 | 4.50 | 3.00 | 1.12 | 3.00 | 13.12 | 99.29 |
| 18 | 310 | 77.50 | 31.00 | 13.18 | 7.75 | 4.65 | 3.10 | 1.16 | 3.00 | 13.66 | 112.96 |
| 19 | 320 | 80.00 | 32.00 | 13.60 | 8.00 | 4.80 | 3.20 | 1.20 | 3.00 | 14.20 | 127.16 |
| 20 | 330 | 82.50 | 33.00 | 14.03 | 8.25 | 4.95 | 3.30 | 1.24 | 3.00 | 14.74 | 141.89 |
| 21 | 340 | 85.00 | 34.00 | 14.45 | 8.50 | 5.10 | 3.40 | 1.27 | 3.00 | 15.27 | 157.17 |
| 22 | 350 | 87.50 | 35.00 | 14.88 | 8.75 | 5.25 | 3.50 | 1.31 | 3.00 | 15.81 | 172.98 |
| 23 | 360 | 90.00 | 36.00 | 15.30 | 9.00 | 5.40 | 3.60 | 1.35 | 3.00 | 16.35 | 189.33 |
| 24 | 370 | 92.50 | 37.00 | 15.73 | 9.25 | 5.55 | 3.70 | 1.39 | 3.00 | 16.89 | 206.22 |

→ Cơ bản: hoà vốn tháng ~T4 (lãi +1,3tr), hoà vốn luỹ kế T7; năm 1 lãi +40,7tr; năm 2 +165,5tr; luỹ kế 24 tháng +206,2tr (~7.900 USD). Không đạt ngưỡng SCALE 1.500 USD/tháng — mở US phải chờ lâu hơn hoặc đẩy đơn (mục 8).

### 2.3 Kịch bản TỐT (xác suất chủ quan 20% ⚠️) — AOV VN 250k, mở US từ T7 (AOV $30 ≈ 780k)

| T | Đơn VN | Đơn US | DT (tr) | Giá vốn (tr) | Phí sàn (tr) | Ads/Aff (tr) | Fulfill (tr) | Hoàn DP (tr) | Thuế (tr) | Cố định (tr) | Lãi ròng (tr) | Luỹ kế (tr) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 40 | 0 | 10.00 | 4.00 | 1.70 | 1.00 | 0.60 | 0.40 | 0.15 | 11.00 | -8.85 | -8.85 |
| 2 | 80 | 0 | 20.00 | 8.00 | 3.40 | 2.00 | 1.20 | 0.80 | 0.30 | 3.00 | 1.30 | -7.55 |
| 3 | 120 | 0 | 30.00 | 12.00 | 5.10 | 3.00 | 1.80 | 1.20 | 0.45 | 15.90 | -9.45 | -17.00 |
| 4 | 160 | 0 | 40.00 | 16.00 | 6.80 | 4.00 | 2.40 | 1.60 | 0.60 | 3.00 | 5.60 | -11.40 |
| 5 | 200 | 0 | 50.00 | 20.00 | 8.50 | 5.00 | 3.00 | 2.00 | 0.75 | 3.00 | 7.75 | -3.65 |
| 6 | 240 | 0 | 60.00 | 24.00 | 10.20 | 6.00 | 3.60 | 2.40 | 0.90 | 8.00 | 4.90 | 1.25 |
| 7 | 320 | 20 | 95.60 | 38.24 | 14.54 | 11.12 | 7.14 | 3.82 | 1.51 | 6.90 | 12.33 | 13.58 |
| 8 | 360 | 30 | 113.40 | 45.36 | 16.70 | 13.68 | 8.91 | 4.54 | 1.82 | 6.90 | 15.49 | 29.07 |
| 9 | 400 | 45 | 135.10 | 54.04 | 19.11 | 17.02 | 11.27 | 5.40 | 2.20 | 6.90 | 19.16 | 48.23 |
| 10 | 440 | 60 | 156.80 | 62.72 | 21.51 | 20.36 | 13.62 | 6.27 | 2.59 | 6.90 | 22.83 | 71.07 |
| 11 | 480 | 80 | 182.40 | 72.96 | 24.14 | 24.48 | 16.56 | 7.30 | 3.05 | 6.90 | 27.01 | 98.08 |
| 12 | 520 | 100 | 208.00 | 83.20 | 26.78 | 28.60 | 19.50 | 8.32 | 3.51 | 6.90 | 31.19 | 129.27 |
| 13 | 540 | 120 | 228.60 | 91.44 | 28.57 | 32.22 | 22.14 | 9.14 | 3.90 | 6.90 | 34.29 | 163.56 |
| 14 | 560 | 140 | 249.20 | 99.68 | 30.35 | 35.84 | 24.78 | 9.97 | 4.28 | 6.90 | 37.40 | 200.96 |
| 15 | 580 | 160 | 269.80 | 107.92 | 32.14 | 39.46 | 27.42 | 10.79 | 4.67 | 6.90 | 40.50 | 241.46 |
| 16 | 600 | 180 | 290.40 | 116.16 | 33.92 | 43.08 | 30.06 | 11.62 | 5.06 | 6.90 | 43.60 | 285.06 |
| 17 | 620 | 200 | 311.00 | 124.40 | 35.71 | 46.70 | 32.70 | 12.44 | 5.45 | 6.90 | 46.70 | 331.76 |
| 18 | 640 | 220 | 331.60 | 132.64 | 37.50 | 50.32 | 35.34 | 13.26 | 5.83 | 6.90 | 49.81 | 381.57 |
| 19 | 660 | 240 | 352.20 | 140.88 | 39.28 | 53.94 | 37.98 | 14.09 | 6.22 | 6.90 | 52.91 | 434.48 |
| 20 | 680 | 260 | 372.80 | 149.12 | 41.07 | 57.56 | 40.62 | 14.91 | 6.61 | 6.90 | 56.01 | 490.50 |
| 21 | 700 | 280 | 393.40 | 157.36 | 42.85 | 61.18 | 43.26 | 15.74 | 6.99 | 6.90 | 59.12 | 549.61 |
| 22 | 720 | 300 | 414.00 | 165.60 | 44.64 | 64.80 | 45.90 | 16.56 | 7.38 | 6.90 | 62.22 | 611.83 |
| 23 | 740 | 320 | 434.60 | 173.84 | 46.43 | 68.42 | 48.54 | 17.38 | 7.77 | 6.90 | 65.32 | 677.16 |
| 24 | 760 | 340 | 455.20 | 182.08 | 48.21 | 72.04 | 51.18 | 18.21 | 8.15 | 6.90 | 68.43 | 745.58 |

→ Tốt: luỹ kế dương từ T6; lãi VN+US T24 = 68,4tr/tháng (~2.630 USD); luỹ kế 24 tháng +745,6tr (~28.700 USD). ⚠️ US bắt đầu lãi chỉ từ T9 (trước đó lỗ 0,9–1,9tr/tháng do 3PL + phí cố định); SCALE 1.500 USD/tháng đạt ~T15–17 (mục 8 — mâu thuẫn lộ trình).

### 2.4 Đối chiếu 3 kịch bản

| | Tệ | Cơ bản | Tốt |
|---|---|---|---|
| Lãi luỹ kế T6 | −17,9tr (KILL T4) | −2,6tr | +1,3tr |
| Lãi luỹ kế T12 | — | +40,7tr | +129,3tr |
| Lãi luỹ kế T24 | — | +206,2tr | +745,6tr |
| Lãi/tháng đỉnh | — | +16,9tr (T24) | +68,4tr (T24) |
| Tiền đã chi tối đa | ~18tr | ~11,4tr (đáy T3) | ~17,0tr (đáy T3) |
| Quyết định | KILL T4, đổi ngách | chạy tiếp, cân nhắc US sau T18 nếu muốn SCALE | SCALE ~T15–17; mở shop 3, tuyển người |

---

## 3. Phân tích độ nhạy (6 bảng)

Trạng thái tham chiếu: **kịch bản cơ bản tháng 12 = 230 đơn/tháng, lãi ròng +9,36tr/tháng**. Mỗi bảng chỉ thay 1 biến, giữ nguyên phần còn lại.

### 3.1 Giá bán ±20% (giữ giá vốn tuyệt đối 100.000đ, giữ % các loại phí)

| Giá bán | CM/đơn | Lãi ròng/tháng (230 đơn) | Δ vs base | BEP |
|---|---|---|---|---|
| 200.000đ (−20%) | 20.500đ | +1,72tr | **−7,65tr** | 146 đơn/tháng |
| 250.000đ (base) | 53.750đ | +9,36tr | 0 | 56 đơn |
| 300.000đ (+20%) | 87.000đ | +17,01tr | +7,65tr | 34 đơn |

→ Giá là đòn bẩy mạnh nhất theo chiều tích cực; nhưng giảm giá 20% là tự sát ở mô hình này (BEP nhảy lên 146 đơn). **Tuyệt đối không đua giá với hàng TQ bán trực tiếp.**

### 3.2 Tỷ lệ hoàn trả 5% vs 15% vs 30%

| Tỷ lệ hoàn | Dự phòng/đơn | CM/đơn | Lãi ròng/tháng (230 đơn) | Δ vs base |
|---|---|---|---|---|
| 5% (base) | 10.000đ | 53.750đ | +9,36tr | 0 |
| 15% | 30.000đ | 33.750đ | +4,76tr | −4,60tr |
| 30% | 60.000đ | 3.750đ | **−2,14tr** | −11,50tr |

→ Hoàn 30% làm mô hình lỗ ngay cả ở 230 đơn/tháng (BEP ~800 đơn). Đây là rủi ro số 1 — case 光年易达 mất 60–70% đơn vì hoàn trả gian lận (baseline): video mở hàng + chứng từ + blacklist từ đơn đầu tiên là **bắt buộc**, không phải tuỳ chọn.

### 3.3 Phí sàn 19% vs 25% (phí giao dịch giữ 6%, hoa hồng tăng)

| Phí sàn | Cấu thành | CM/đơn | Lãi ròng/tháng (230 đơn) | Δ vs base | BEP |
|---|---|---|---|---|---|
| 17% (base) | GT 6% + HH 11% | 53.750đ | +9,36tr | 0 | 56 đơn |
| 19% | GT 6% + HH 13% | 48.750đ | +8,21tr | −1,15tr | 62 đơn |
| 25% | GT 6% + HH 19% | 33.750đ | +4,76tr | −4,60tr | 89 đơn |

→ Báo chí đã ghi nhận phí sàn Shopee/TikTok chạm mốc ~25% doanh thu ✅ [VnBusiness]. Ở 25%, mô hình vẫn sống nhưng biên đóng góp chỉ còn 13,5% — phải tăng markup lên 3–3,5× hoặc chuyển ngách phí thấp. Theo dõi thông báo Seller Center hằng tuần (baseline).

### 3.4 Chi phí ads+affiliate 10% vs 15% vs 20%

| Ads + Aff | CM/đơn | Lãi ròng/tháng (230 đơn) | Δ vs base | BEP |
|---|---|---|---|---|
| 10% (base) | 53.750đ | +9,36tr | 0 | 56 đơn |
| 15% | 41.250đ | +6,49tr | −2,88tr | 73 đơn |
| 20% | 28.750đ | +3,61tr | −5,75tr | 104 đơn |

→ Ở 20%, BEP gần gấp đôi. Nguyên tắc: không chạy ads trước khi organic chứng minh được đơn (CTR/video tự chạy); tận dụng Dynamic Commission khi chạy Shop Ads (baseline).

### 3.5 Vận chuyển tăng 30%

| Biến | CM/đơn | Lãi ròng/tháng (230 đơn) | Δ vs base | BEP |
|---|---|---|---|---|
| Base (fulfillment 15.000đ) | 53.750đ | +9,36tr | 0 | 56 đơn |
| Fulfillment VN +30% (19.500đ) | 49.250đ | +8,33tr | −1,04tr | 61 đơn |
| + vận chuyển TQ→VN +30% (giá vốn +7.500đ nếu logistics chiếm 25% giá vốn ⚠️) | 41.750đ | +6,60tr | −2,76tr | 72 đơn |

→ Tăng phí ship ít gây chết người hơn hoàn/phí sàn, nhưng cộng dồn cả hai tuyến vận chuyển thì −2,8tr/tháng. Phòng thủ: 2–3 nguồn vận chuyển song song, kiểm đếm tại kho TQ (baseline).

### 3.6 Tỷ giá 24.000 vs 28.000 (giả định 60% giá vốn nhạy tỷ giá ⚠️)

| Tỷ giá | Giá vốn/đơn | CM/đơn | Lãi ròng/tháng (230 đơn) | Δ vs base | BEP | Ngân sách 5.000 USD |
|---|---|---|---|---|---|---|
| 24.000 | 95.385đ | 58.365đ | +10,42tr | +1,06tr | 52 đơn | 120tr |
| 26.000 (base) | 100.000đ | 53.750đ | +9,36tr | 0 | 56 đơn | 130tr |
| 28.000 | 104.615đ | 49.135đ | +8,30tr | −1,06tr | 62 đơn | 140tr |

→ Hiệu ứng hai chiều: VND yếu làm giá vốn nhập tăng (xấu cho biên) nhưng làm vốn USD "nở" ra (tốt cho ngân sách). Tác động ròng ở quy mô này nhỏ (±1,1tr/tháng) — tỷ giá không phải rủi ro top 3, nhưng cần theo dõi khi mở US (doanh thu USD về VND).

**Xếp hạng sát thương** (Δ lãi/tháng tại 230 đơn): 1) Hoàn 30% (−11,5tr) · 2) Giá −20% (−7,65tr) · 3) Ads 20% (−5,75tr) · 4) Phí sàn 25% (−4,6tr) · 5) Hoàn 15% (−4,6tr) · 6) Vận chuyển +30% cả tuyến (−2,76tr) · 7) Tỷ giá (−1,06tr).

---

## 4. Vốn lưu động & dòng tiền

### 4.1 Chu kỳ tiền (từ trả tiền hàng TQ đến nhận tiền TikTok)

| Bước | Thời gian | Nguồn |
|---|---|---|
| 1. Đặt hàng 1688 + thanh toán (qua dịch vụ mua hộ, phí từ 1%) | T0 | ✅ thuongdo (đặt siêu tốc 2–4 giờ) |
| 2. Vận chuyển TQ → kho VN | 3–5 ngày (đơn vị cam kết) · ⚠️ tắc biên 15–60 ngày | ✅ thuongdo; rủi ro baseline |
| 3. Tồn kho trước khi bán | ~14 ngày (mục tiêu tồn bán chạy 2 tuần) | baseline |
| 4. Giao hàng VN | 2–5 ngày | ⚠️ ước |
| 5. Hậu mãi (sau giao, đơn được chốt) | 6 ngày tự nhiên (VN) | ✅ keyouyun (TikTok Shop ĐNÁ) |
| 6. Chốt thanh toán + tiền về | T+1 chốt + 1–5 ngày làm việc về ví/ngân hàng | ✅ keyouyun (Payoneer/LianLian/…; min 1 USD) |
| **Tổng chu kỳ tiền** | **≈33–40 ngày** (stress: 60+ ngày) | khớp dải "payout 7–15 ngày sau giao" của baseline |

⚠️ Lưu ý: số liệu keyouyun mô tả seller **xuyên biên giới** ĐNÁ nhận qua Payoneer/PingPong (có phí rút ~1–2% ⚠️); seller nội địa VN nhận qua ngân hàng VN có thể khác chu kỳ — cần kiểm chứng ở Seller Center (câu hỏi mở 1). Mỗi chu kỳ tiền quay thêm 1 ngày ≈ kẹt thêm ~0,75tr vốn ở 230 đơn/tháng.

### 4.2 Tiền mặt tối thiểu theo mức đơn/tháng

```
WC(D) = D × giá vốn × (ngày hàng+vận chuyển+tồn 34 ngày / 30) + D × payout ròng × (15 ngày / 30) + phí cố định 1 tháng
      = D × 100.000 × 34/30 + D × 191.250 × 15/30 + 3.000.000
      ≈ D × 208.958 + 3.000.000
```

| Đơn/tháng | Vốn hàng tồn + đang bay (tr) | Tiền chờ payout (tr) | Đệm phí cố định (tr) | **Tiền mặt tối thiểu (tr)** |
|---|---|---|---|---|
| 50 (≈ BEP) | 5,7 | 4,8 | 3,0 | **13,4** |
| 100 | 11,3 | 9,6 | 3,0 | **23,9** |
| 155 (trần với 40tr vốn hàng) | 17,6 | 14,8 | 3,0 | **35,4** |
| 230 (cơ bản T12) | 26,1 | 22,0 | 3,0 | **51,1** |
| 400 | 45,3 | 38,3 | 3,0 | **86,6** |
| 760 (tốt T24, riêng VN) | 86,1 | 72,7 | 3,0 | **161,8** |

→ **Nút thắt cứng:** ngân sách chỉ cho 40tr vốn hàng → trần ~150–155 đơn/tháng nếu chỉ sống bằng vốn ban đầu; mọi tăng trưởng vượt trần phải tự tài trợ từ lãi luỹ kế (cơ bản T12 lãi luỹ kế 40,7tr → tổng nguồn ~80tr > WC cần 51,1tr ✅ đủ, nhưng căng). Ở Tốt T24, WC VN cần ~162tr + tồn kho US ~13tr — đều lấy từ lãi tái đầu tư.

### 4.3 Dòng tiền 6 tháng đầu — từng tuần (kịch bản cơ bản)

Giả định: mở đầu 110tr = 40tr lô hàng 1 (trả trước) + 70tr tiền mặt; tiền vào = payout đơn tuần (t−2) × 250.000đ × 0,765 (trừ tại nguồn: phí sàn 17% + affiliate 5% + thuế 1,5%); tiền ra = nhập hàng trước 2 tuần (100.000đ/đơn) + fulfillment 15.000đ + ads 12.500đ (5%) của tuần + phí cố định 750.000đ/tuần. Đơn/tuần theo đường tăng trưởng cơ bản (M1 20 → M6 140 đơn).

| Tuần | Đơn | Tiền vào (tr) | Tiền ra (tr) | Ròng (tr) | Số dư cuối tuần (tr) |
|---|---|---|---|---|---|
| 1 | 3 | 0,00 | 1,43 | −1,43 | 68,57 |
| 2 | 4 | 0,00 | 1,56 | −1,56 | 67,01 |
| 3 | 6 | 0,57 | 1,61 | −1,04 | 65,97 |
| 4 | 7 | 0,77 | 1,74 | −0,98 | 64,99 |
| 5 | 7 | 1,15 | 1,84 | −0,69 | 64,29 |
| 6 | 8 | 1,34 | 2,07 | −0,73 | 63,56 |
| 7 | 9 | 1,34 | 2,10 | −0,76 | 62,80 |
| 8 | 11 | 1,53 | 2,25 | −0,72 | 62,08 |
| 9 | 11 | 1,72 | 2,35 | −0,63 | 61,45 |
| 10 | 12 | 2,10 | 2,48 | −0,38 | 61,07 |
| 11 | 13 | 2,10 | 2,81 | −0,70 | 60,37 |
| 12 | 14 | 2,29 | 3,04 | −0,74 | 59,63 |
| 13 | 17 | 2,49 | 3,32 | −0,83 | 58,80 |
| 14 | 19 | 2,68 | 3,57 | −0,90 | 57,90 |
| 15 | 21 | 3,25 | 3,73 | −0,48 | 57,43 |
| 16 | 23 | 3,63 | 3,98 | −0,35 | 57,08 |
| 17 | 24 | 4,02 | 4,31 | −0,29 | 56,78 |
| 18 | 26 | 4,40 | 4,57 | −0,17 | 56,62 |
| 19 | 29 | 4,59 | 4,75 | −0,16 | 56,46 |
| 20 | 31 | 4,97 | 5,00 | −0,03 | **56,43 (đáy)** |
| 21 | 32 | 5,55 | 5,23 | +0,32 | 56,75 |
| 22 | 34 | 5,93 | 5,49 | +0,44 | 57,19 |
| 23 | 36 | 6,12 | 5,44 | +0,68 | 57,87 |
| 24 | 38 | 6,50 | 5,50 | +1,01 | 58,88 |

→ **Kết luận dòng tiền:** với ngân sách 110tr và đúng chu kỳ payout, 6 tháng đầu không thiếu tiền (đáy 56,4tr, tuần 20). Nếu payout chậm thêm 1 tuần → đáy thấp thêm ~5–6,5tr; chậm 2 tuần → ~12tr (vẫn an toàn, nhưng phải cắt ads sớm). Quy tắc cứng: **giữ số dư ≥ WC(D) ở mục 4.2 + 10tr đệm**; chạm ngưỡng → dừng ads, giảm nhập, không mở shop mới.

### 4.4 Ngân sách 110tr — đối chiếu với nhu cầu vốn

| Khoản (baseline) | Số tiền | Nhận xét mô hình |
|---|---|---|
| Vốn hàng lô 1–2 | 40tr | trần ~150–155 đơn/tháng (mục 4.2) — nút thắt chính |
| Tools 6 tháng | 12tr | đã nằm trong phí cố định 2tr/tháng |
| Giấy tờ/thiết bị | 8tr | đã tính one-time T1 trong P&L |
| Ads 3 tháng đầu | 15tr | ở cơ bản ads thực chi 3 tháng đầu = 5% × (5+8,75+12,5)tr ≈ 1,3tr ⚠️ ads tính theo % DT, con số 15tr là trần cam kết |
| Dự phòng + US | 35tr | LLC 12,9tr + logistics US 5tr + hàng tồn kho US 8–13tr = 26–31tr → **vừa khít, không nên dùng hết** |
| Tổng | ≈110tr | đáy tiền mặt mô hình 56,4tr + tồn kho ~14tr → tổng tài sản đáy ≈ 70tr < 110tr ban đầu ✅ nằm trong ngân sách |

---

## 5. Điểm hoà vốn

**Công thức:**

```
Q* (đơn/tháng) = Phí cố định / Biên đóng góp 1 đơn = FC / CM = 3.000.000 / 53.750 = 55,8 → 56 đơn/tháng
DT* (doanh thu hoà vốn) = Q* × AOV = 56 × 250.000 ≈ 14,0 triệu VND/tháng
CM = P − (GV 100.000 + GT 15.000 + HH 27.500 + aff 12.500 + ads 12.500 + ful 15.000 + hoàn 10.000 + thuế 3.750) = 53.750đ
```

| Biến số thay đổi | BEP (đơn/tháng) | BEP doanh thu |
|---|---|---|
| Base (GV 40%) | **56** | **14,0tr** |
| Markup 3× (GV 33,3%) — ngầm định của baseline | 43 | 10,7tr |
| Giá bán 200.000đ / 300.000đ | 146 / 34 | 29,3tr / 10,3tr |
| Phí sàn 19% / 25% | 62 / 89 | 15,4tr / 22,2tr |
| Ads+aff 15% / 20% | 73 / 104 | 18,2tr / 26,1tr |
| Hoàn 15% / 30% | 89 / ~800 | 22,2tr / ~200tr |
| Fulfillment +30% | 61 | 15,2tr |
| Tỷ giá 24.000 / 28.000 | 52 / 62 | 12,9tr / 15,4tr |

⚠️ Chênh với baseline (45–50 đơn ≈ 12–13tr): baseline ngầm giả định markup ×3 (giá vốn ~33–36%) và chưa tách thuế + dự phòng hoàn thành dòng riêng; mô hình này thận trọng hơn (GV 40% + thuế 1,5% + hoàn DP 4%). **Hai số đều đúng với giả định của chính nó — vận hành theo số thận trọng (56 đơn).**

---

## 6. KPI tài chính theo dõi hằng tuần (báo cáo 6h sáng — n8n)

| # | KPI | Định nghĩa | Công thức | Ngưỡng cảnh báo | Hành động khi chạm |
|---|---|---|---|---|---|
| 1 | Đơn/tuần | số đơn 7 ngày gần nhất | Σ đơn (7 ngày) | <14/tuần (=BEP/4) vàng · <7 đỏ | soi content/SKU; dừng ads nếu TACOS cao |
| 2 | Đơn/tháng chạy | trailing 30 ngày | Σ đơn (30 ngày) | <56 (dưới BEP) | đối chiếu lộ trình kill ngày 90 |
| 3 | Biên đóng góp/đơn | lãi gộp sau biến phí | (DT − biến phí)/đơn | <40.000đ | soi giá vốn, phí sàn, tỷ lệ affiliate |
| 4 | Tỷ lệ hoàn 7 ngày | đơn hoàn/đơn giao | hoàn ÷ đơn trong kỳ | >5% vàng · >10% đỏ | video mở hàng, blacklist, đổi trả 7 ngày rõ |
| 5 | TACOS | tổng chi phí bán hàng quảng cáo | (ads + affiliate) ÷ DT | >15% vàng · >20% đỏ | tắt campaign lỗ, giảm hoa hồng affiliate |
| 6 | AOV | giá trị trung bình đơn | GMV ÷ đơn | <230.000đ | xem lại khuyến mãi/bundle |
| 7 | Chu kỳ tiền | ngày tồn + ngày payout | (tồn kho ÷ giá vốn/ngày) + (số dư chờ payout ÷ DT ròng/ngày) | >45 ngày vàng · >60 đỏ | giảm nhập, đàm phán vận chuyển, kiểm đối soát |
| 8 | Số dư tiền mặt | đệm so với nhu cầu vốn | tiền mặt − WC(D) (mục 4.2) | < 10tr đệm | dừng ads, hoãn nhập, không mở shop mới |
| 9 | Lỗ luỹ kế | tổng lỗ từ đầu, quy USD | luỹ kế ÷ 26.000 | >1.500 USD vàng (kiến nghị mới) · >3.000 USD = KILL (baseline) | họp quyết định kill/pivot ≤2 tuần |
| 10 | Giờ vận hành/ngày | thời gian founder trực tiếp làm | theo log n8n/OpenClaw | >2h/ngày liên tục | tự động hoá thêm 1 khâu đang tốn giờ nhất |

Tần suất: KPI 1–5, 8 hằng ngày (báo cáo tự động 6h sáng); KPI 6, 7, 9, 10 hằng tuần (thứ 2). Mọi KPI ghi vào Airtable để prompt chọn hàng hằng tuần học theo (vòng lặp dữ liệu — baseline).

---

## 7. So sánh kênh: TikTok Shop VN vs Shopee VN vs TikTok Shop US

| Tiêu chí | TikTok Shop VN | Shopee VN | TikTok Shop US |
|---|---|---|---|
| Phí bắt buộc | GT 6% + HH 9–14% → **15–19%** ✅ [Công Thương]; đã ghi nhận chạm ~25% ✅ [VnBusiness] | phí cố định ~1–10%+ theo ngành (từ 01/05/2026 giảm vài ngành) + phí xử lý giao dịch ~5% (gồm VAT) + hạ tầng 3.000đ/đơn ✅ [varecom] → tổng ~6–15% tuỳ ngành ⚠️ tự cộng | referral 6% phẳng (5% trang sức), 3% cho seller mới 30 ngày, không có phí GD riêng ✅ [OneCart] |
| Phí tự nguyện | VXP 4% (tối đa 50k/sp) ✅ | Voucher Xtra 2% (max 50k/sp), Freeship Xtra ✅ | affiliate 5–25% do seller đặt ✅ |
| Chu kỳ tiền | giao + 6 ngày hậu mãi + T+1 + 1–5 ngày làm việc ≈ **33–40 ngày tổng** ✅ [keyouyun] ⚠️ seller nội địa có thể khác | ⚠️ chưa xác minh chu kỳ 2026 (đơn hoàn tất → ví → rút NH) | ⚠️ chưa xác minh |
| Nguồn traffic | organic video + live mạnh; AI chatbot seller x2,2 chuyển đổi ✅ [100ec] | tìm kiếm/SEO/trả phí là chính, cần ads nhiều hơn ⚠️ | organic video; rào cản content tiếng Anh |
| Rủi ro hoàn | cao — case CN mất 60–70% đơn do gian lận (baseline) | trung bình, cơ chế khiếu nại sàn mạnh ⚠️ | có; cộng thêm FTC disclosure, phạt tới $51.744/vi phạm (baseline) |
| Biên đóng góp theo mô hình này | **21,5%** (AOV 250k, GV 40%) | ⚠️ ước tương đương hoặc nhỉnh hơn ở ngách phí 1–5% (phí thấp hơn nhưng AOV cạnh tranh hơn, phải mua ads) | **~13%** ($3,90/đơn tại AOV $30, 3PL $4,5 ⚠️) |
| Rào cản vào | 0đ, CCCD, 1–3 ngày (baseline) | 0đ, dễ | LLC + EIN + bank US + **kho nội địa US** ✅ [妙手ERP] — $397+ năm đầu (baseline) |
| Phù hợp OPC giai đoạn | **Giai đoạn 1 (bắt buộc)** — chi phí thấp, traffic organic | kênh phụ đa dạng hoá khi VN đã có SOP (phòng thủ phí sàn tăng) | giai đoạn 2 — chỉ khi VN lãi 2 tháng liên tiếp + đủ đệm 35tr |

→ Khuyến nghị: **TikTok Shop VN trước** (đúng baseline), Shopee VN là kênh phòng thủ thứ 2 (listing AI đã dịch sẵn, chi phí chuyển kênh gần bằng 0), TikTok US chỉ mở khi VN có lãi ổn định vì biên US mỏng ở quy mô nhỏ và rào cản pháp lý cao.

---

## 8. Thay đổi so với baseline

1. **Thêm 2 dòng chi phí tường minh** — thuế 1,5% (GTGT 1% + TNCN 0,5%) ✅ NĐ 117/2025 và dự phòng hoàn 4% DT → BEP tăng từ ~45–50 đơn lên **56 đơn (~14tr)**. Không phải mâu thuẫn: baseline ngầm giả định markup ×3 (giá vốn ~33–36%) — với markup ×3 mô hình này cho BEP 43 đơn, khớp baseline. Vận hành theo số thận trọng 56.
2. **Thuế đã được sàn khấu trừ, nộp thay từ 1/7/2025** (NĐ 117/2025 ✅) — hộ kinh doanh không phải tự khai/nộp GTGT+TNCN cho phần doanh thu trên sàn (bù trừ khi hoàn/huỷ). Baseline chỉ nói "thuế khoán 1–1,5% ⚠️" → giờ có nguồn và cơ chế rõ.
3. **Payout có nguồn chính thức:** VN = giao + 6 ngày hậu mãi + T+1 chốt + 1–5 ngày làm việc ✅ keyouyun → chu kỳ tiền tổng ~33–40 ngày, khớp "7–15 ngày" baseline nhưng cần cộng thêm thời gian giao + tồn kho khi dự trù vốn.
4. **Mâu thuẫn nội bộ SCALE vs lộ trình US:** KPI SCALE yêu cầu lãi >1.500 USD/tháng × 3 tháng liên tiếp (~39tr), nhưng lộ trình 90–180 ngày chỉ cần "VN có lãi 2 tháng liên tiếp". Trong kịch bản Tốt, US mở từ T7 (theo lộ trình) trong khi ngưỡng 1.500 USD chỉ đạt ~T15–17; ở cơ bản **không bao giờ đạt 1.500 USD/tháng trong 24 tháng**. Kiến nghị: (a) "mở US thử nghiệm" = VN lãi 2 tháng + đủ đệm 35tr; (b) "SCALE chính thức (tuyển người, mở rộng)" = lãi >1.500 USD/tháng × 3 tháng.
5. **Ngưỡng KILL lỗ 3.000 USD quá cao cho VN:** 3.000 USD ≈ 78tr ≈ 71% ngân sách 110tr. Kịch bản Tệ chỉ lỗ ~610 USD sau 3 tháng → điều kiện VÀ không kích hoạt. Kiến nghị hạ còn **1.500 USD (~39tr)** để còn vốn đổi ngách trong ≤2 tuần (tinh thần 景行).
6. **US margin mỏng:** CM US chỉ ~$3,90/đơn (13%) ở AOV $30 + 3PL $4,5 ⚠️ — US lỗ 0,9–1,9tr/tháng trong 2 tháng đầu. Cần test US ≤60 ngày với ngân sách cứng ~20tr (LLC 12,9tr + logistics 5tr đã tính trong P&L Tốt) và điều kiện cắt rõ.
7. **Dự phòng 35tr vừa khít khi mở US:** LLC 12,9tr + logistics 5tr + tồn kho US 8–13tr = 26–31tr → không nên dùng hết; giữ ≥10tr đệm VN.
8. **Giới hạn vốn hàng 40tr** = trần ~150–155 đơn/tháng; vượt trần phải tự tài trợ từ lãi (cơ bản T12 vừa đủ, căng) — cần kế hoạch tái đầu tư lãi rõ từng tháng.
9. **Thêm chi phí ngầm của seller xuyên biên giới:** nhận tiền qua Payoneer/PingPong có phí rút ~1–2% ⚠️ (keyouyun) — nếu đăng ký shop dạng xuyên biên giới; seller nội địa VN nhận NH VN thì không chịu khoản này (cần xác minh).

## 9. Câu hỏi mở

1. TikTok Shop VN **seller nội địa** (nhận qua ngân hàng VN) chu kỳ đối soát/thanh toán chính xác hiện tại? (Nguồn keyouyun mô tả seller xuyên biên giới ĐNÁ nhận qua Payoneer/PingPong.)
2. TikTok Shop VN đã áp dụng khấu trừ thuế nộp thay theo NĐ 117/2025 chưa, và cơ chế bù trừ thuế khi hoàn/huỷ đơn cụ thể ra sao?
3. Biểu hoa hồng thực tế 2026 cho ngách dự định (bách hoá 9–13% hay sức khoẻ–làm đẹp 12,5–14%)? — quyết định dùng HH 11% hay 14% trong mô hình.
4. NĐ 68/2026 (hiệu lực 5/3/2026 ✅): hộ kinh doanh vượt 500tr doanh thu/năm phải chuyển phương pháp kê khai — chi phí kế toán tăng bao nhiêu ở kịch bản Tốt T10+ (~130tr/tháng)?
5. Chi phí 3PL US thực tế 2026 cho gói <1kg (storage + pick/pack + last-mile)? — giả định $4,5/đơn quyết định CM US $3,90 có đúng không.

## 10. Nguồn tham khảo (truy cập 10/09/2026)

- [Báo Công Thương — Từ 9/5, TikTok Shop tăng biểu phí (03/05/2026)](https://congthuong.vn/tu-9-5-tiktok-shop-tiep-tuc-tang-bieu-phi-voi-nha-ban-hang-454850.html)
- [VnBusiness — Shopee và TikTok Shop: phí sàn chạm 25% doanh thu](https://vnbusiness.vn/hai-ong-lon-shopee-va-tiktok-shop-cung-day-phi-san-cham-nguong-ky-luc-25-doanh-thu.html)
- [Báo Pháp luật VN — Sàn TMĐT khấu trừ, nộp thuế thay người bán từ 1/7 (NĐ 117/2025)](https://baophapluat.vn/san-thuong-mai-dien-tu-se-khau-tru-nop-thue-thay-nguoi-ban-hang-online-tu-17-post551488.html)
- [Chinhphu.vn — Toàn văn Nghị định 68/2026/NĐ-CP về thuế hộ kinh doanh](https://xaydungchinhsach.chinhphu.vn/print/toan-van-nghi-dinh-68-2026-nd-cp-quy-dinh-ve-chinh-sach-thue-quan-ly-thue-voi-ho-kinh-doanh-119260306102906789.htm)
- [客优云 keyouyun — TikTok Shop ĐNÁ: chu kỳ kết toán/thanh toán (22/04/2026)](https://www.keyouyun.com/dongnanyaqinglaizheliheduijiesuanxinxi/)
- [VAR eCOM — Phí hoa hồng Shopee 2026 (20/08/2026)](https://varecom.vn/phi-hoa-hong-shopee/)
- [Thương Đô Logistics — Dịch vụ order 1688 về VN: phí mua hộ từ 1%, ship từ 4.000đ/kg, 3–5 ngày (09/2026)](https://www.thuongdo.com/dat-hang-1688)
- [OneCart — TikTok Shop Seller Fees (04/2026)](https://www.getonecart.com/tiktok-shop-seller-fees/) · [妙手ERP — TikTok US 跨境店 điều kiện](https://erp.91miaoshou.com/platforms/tiktokshopus.html) · [TheAmericanLLC — US LLC cho TikTok Shop](https://www.theamericanllc.com/llc/tiktok-shop) · [Nhập Hàng China — giá về tay 1688](https://nhaphangchina.net/cach-tinh-gia-ve-tay-khi-order-hang-trung-quoc-chuan-nhat-2026/) (qua kế hoạch 01)
- Kế hoạch 01 nội bộ: `plans/260910-opc-20-models/01-tiktok-shop-crossborder-opc.md`; Master playbook: `plans/reports/260910-1118-opc-china-master-playbook.md`.
