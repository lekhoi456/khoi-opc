# TỔNG KẾT — 20 Kế hoạch Xây dựng Công ty OPC (start from scratch → implementation)

> Orchestrator: DeepSeek · Team: 8× DeepSeek + 6× Claude + 6× Codex (Codex bị sandbox read-only → 6 kế hoạch do DeepSeek viết lại theo thiết kế Codex) · Ngày: 2026-09-10
> Nguồn kiến thức nền: master playbook + deep-dive OpenClaw + brief chung (xem `00-index.md`).

## 1. Tóm tắt điều hành

Bộ tài liệu gồm **20 kế hoạch kinh doanh độc lập**, mỗi kế hoạch là một "công ty 1 người" khả thi: mô hình 1 slide → bằng chứng thành công ở Trung Quốc (case đã thẩm định) → phân tích thị trường VN & US → tech stack + kiến trúc tự động hoá → vận hành tuần → tài chính 12 tháng → lộ trình 0–180 ngày cầm tay chỉ việc → rủi ro → KPI kill/scale → nguồn → câu hỏi mở. Tất cả đều đáp ứng: **1 người khả thi trong 6 tháng, vốn ≤5.000 USD**.

Điểm chung rút ra từ 20 kế hoạch (tinh hoa Trung Quốc đã được bản địa hoá):
1. **AI hoá triệt để → chuẩn hoá cục bộ → người giữ phần lõi** (quyết định, niềm tin, rủi ro) — mọi kế hoạch đều chia việc theo nguyên tắc này.
2. **"Vị trí công việc AI có chức danh"** (mẫu 张顺 5 nhân viên AI) xuất hiện trong gần như cả 20 kế hoạch — đây là pattern quản trị OPC chuẩn.
3. **VN là cửa tập, US là cửa tiền:** 19/20 kế hoạch chọn vào VN trước (chi phí thấp, pháp lý nhẹ, Zalo OA) rồi mở US sau (RPM/giá cao hơn 5–30 lần).
4. **Compliance là vũ khí:** video mở hàng chống gian lận hoàn (01, 02), khai báo AI trên YouTube/TikTok (05, 06, 07, 08), VNeID (03), ranh giới UPL/Luật Luật sư (16), Nghị định 13/2023 (gần như mọi kế hoạch VN).
5. **Ngưỡng kill cứng ở ngày 90** + vốn trần rõ ràng — bài học "90% không hoàn vốn" của làn sóng TQ.

## 2. Cách dùng bộ tài liệu

1. Đọc `00-selection-rationale.md` (vì sao 20 mô hình này) → chọn 2–3 ứng viên theo bảng quyết định mục 3.
2. Đọc sâu 2–3 kế hoạch ứng viên (`NN-*.md`), so sánh ngưỡng vốn/hoà vốn/kill.
3. Chọn 1 → làm theo lộ trình 0–30 ngày đúng từng bước; mỗi mốc 30 ngày đối chiếu KPI thật.
4. Trước khi dùng số liệu để ra quyết định tài chính: kiểm tra mục ⚠️ và mục "12. Xác minh bổ sung" (với file Claude), mục 11 (câu hỏi mở).

## 3. Khung ra quyết định — chọn 1 trong 20

| Tiêu chí của bạn | Chọn mô hình |
|---|---|
| Vốn ≤1.000 USD, không cần kỹ năng đặc biệt | 04 (agency listing), 07 (content IP), 20 (IP licensing), 12 (skill builder) |
| Có nền tảng ngành (nhà máy/F&B/kế toán/luật) | 15, 16, 17 — biên lợi nhuận cao nhất, bán kinh nghiệm |
| Biết code / sẵn sàng học vibe coding | 10 (indie SaaS), 11 (edtech), 13 (video SW), 12, 18, 19 |
| Muốn bán hàng vật lý, dòng tiền nhanh | 01 (TikTok Shop VN), 02 (eBay), 03 (livestream) |
| Mạnh sáng tạo nội dung | 05 (short drama), 06 (漫剧 IP), 07 (content dọc), 08 (ads director), 09 (music) |
| Muốn thu USD sớm, chấp nhận build dài hơi | 10, 11, 12, 13 (SaaS toàn cầu) |
| Muốn doanh thu đầu tiên trong 30 ngày | 04, 08, 14, 15 (dịch vụ B2B VN) |
| Thị trường đích chủ yếu US | 02 (eBay), 05/06/07 (content tiếng Anh), 10/11/13 (SaaS), 20 (licensing) |

## 4. Digest 20 kế hoạch

| # | Mô hình (1 dòng) | Vốn | Hoà vốn | Kill (ngày 90) | Trạng thái |
|---|---|---|---|---|---|
| 01 | TikTok Shop VN→US full-AI, 5 AI employees, nhập 1688 | ~110tr VND | 45–50 đơn/tháng | <30 đơn & lỗ >$3k | ✅ |
| 02 | Solo eBay/Amazon, 5 AI employees, hàng thủ công <500g | ~$2.270 | 15–20 đơn/tháng | <20 đơn/tháng | ✅ |
| 03 | Studio 数字人 livestream + LIVE lai (tuân thủ VNeID/policy US) | 120tr VND | ~30tr/tháng (tháng 7) | theo KPI mục 9 | ✅ |
| 04 | Agency AI listing/content cho seller (bán xẻng) | ~26tr VND | tháng 3 | <10 khách | ✅ |
| 05 | AI short drama studio xuất khẩu + B2B phim QC | ~127tr VND | tháng 6–7 | 0đ doanh thu + <3k view | ✅ |
| 06 | Kênh AI 漫剧 tiếng Anh tự xây IP (RPM US) | ~$3.000 | tháng 11–12 (tốt) | $1.500 đốt / <50k view | ✅ |
| 07 | Kênh content dọc AI (affiliate-first + newsletter $5) | ≤$2.000 | tháng 9–10 | <100k views + <2k follower | ✅ |
| 08 | "AI Director" video ads trọn gói cho SME | thấp (~$500–1.000) | sau 3–5 đơn | theo mục 9 | ✅ (verify-pass) |
| 09 | Studio nhạc AI/âm thanh cho game-video-podcast (Rights Ledger + human finishing) | ≤$2.000 | ~$180/tháng | MRR <$250 ngày 90 | ✅ |
| 10 | Indie SaaS niche toàn cầu (vibe coding, MoR Paddle) | ≤$3.000 | — | — | ✅ (verify-pass) |
| 11 | AI chấm bài văn/essay (mẫu 作文说) | ~$2.000–2.500 | tháng 5–6 | <30 học sinh trả phí | ✅ (verify-pass) |
| 12 | Xưởng skill/MCP cho AI agent (opc-skills-vn) | ≤$2.000 | — | — | ✅ (verify-pass) |
| 13 | Phần mềm dựng video AI niche ($19/$49/$99, human-approval) | $4.650 | ~7 khách | <12 khách / acceptance <40% | ✅ |
| 14 | Agency chatbot RAG cho SME (vertical nhà hàng, Zalo OA) | $1.700 | tháng 3 | <2 khách trả phí | ✅ |
| 15 | Tư vấn AI ngành dọc (F&B 私域 + nhà máy 质检) | ≤50tr VND | đơn thứ 1–2 | <2 đơn trả phí | ✅ |
| 16 | Dịch vụ pháp lý AI cho SME (ranh giới UPL) | ~2–3tr VND + biến phí | tháng 3–4 | <10 khách/tháng | ✅ (verify-pass) |
| 17 | AI kế toán–thuế cho hộ kinh doanh/seller VN (bản nháp, hậu NQ198) | ~49tr VND | 45–50 khách | <10 khách trả phí | ✅ |
| 18 | OPC dữ liệu AI (annotation 3 tầng, ngách tiếng Việt/y tế) | ≤$3.000 | ~$800 MRR | MRR <$500 tháng 6 | ✅ |
| 19 | Agent Manager: đội ngũ AI thuê cho doanh nghiệp (SLA) | ≤$3.000 | ~2 khách | <2 khách trả tiền | ✅ |
| 20 | Xưởng IP/thiết kế cấp phép (hoa văn, marketplace) | ≤$2.000 | — | — | ✅ (verify-pass) |

## 5. Việc còn lại sau khi đủ 20 file

1. ✅ Điền digest 20/20 kế hoạch vào bảng mục 4 — đã xong.
2. 🔄 Verify-pass cho 6 file Claude (agent đang chạy) — chờ thu.
3. ✅ QA nhất quán pass 1 — xem `00-qa-nhat-quan.md` (tỷ giá, Thông tư thuế, NĐ13).
4. Pass cuối (khi verify-pass xong): chốt tỷ giá chuẩn + note TT 18/2026 vs 40/2021 vào đầu bộ tài liệu.
