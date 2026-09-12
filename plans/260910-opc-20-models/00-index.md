# INDEX — 20 Kế hoạch Xây dựng Công ty OPC (start from scratch → implementation)

> Orchestrator: DeepSeek (agent chính). Team: 8× DeepSeek + 6× Claude + 6× Codex.
> Ngày khởi động: 2026-09-10. Trạng thái cập nhật dần khi từng agent hoàn thành.

## Bảng trạng thái

| # | File | Mô hình | Model | Trạng thái |
|---|---|---|---|---|
| 00 | `00-brief-va-template.md` | Brief chung + template (đọc trước) | Orchestrator | ✅ xong |
| 01 | `01-tiktok-shop-crossborder-opc.md` | TikTok Shop xuyên biên giới full-AI | DeepSeek | ✅ xong (176 dòng, 5/5) |
| 02 | `02-ebay-solo-five-ai-employees.md` | Solo seller eBay/Amazon + 5 AI employees | DeepSeek | ✅ xong (188 dòng, 5/5) |
| 03 | `03-digital-human-livestream-studio.md` | Studio livestream AI 数字人 xuyên biên giới | DeepSeek | ✅ xong (175 dòng, 5/5 — kèm pivot tuân thủ VNeID/policy US) |
| 04 | `04-ai-listing-content-agency.md` | Agency AI listing/content cho seller nhỏ | DeepSeek | ✅ xong (155 dòng, 5/5) |
| 05 | `05-ai-short-drama-studio.md` | AI short drama studio xuất khẩu | DeepSeek | ✅ xong (147 dòng, 5/5) |
| 06 | `06-ai-comic-animation-ip-channel.md` | Kênh AI 漫剧/hoạt hình tự xây IP | DeepSeek | ✅ xong (175 dòng, đạt 5/5 tiêu chí) |
| 07 | `07-ai-content-ip-operator.md` | Vận hành kênh content IP dọc bằng AI agent | DeepSeek | ✅ xong (183 dòng, 5/5) |
| 08 | `08-ai-video-ads-director.md` | "AI Director" video quảng cáo cho SME | Claude | ✅ xong (170 dòng, cấu trúc 5/5) |
| 09 | `09-ai-music-audio-studio.md` | Studio nhạc AI/âm thanh cho game-video-podcast | Codex (thiết kế) → DeepSeek | ✅ xong (216 dòng, 5/5) |
| 10 | `10-indie-saas-vibe-coding.md` | Indie SaaS niche toàn cầu bằng vibe coding | Claude | ✅ xong (202 dòng; web bị chặn → số ngoài brief ⚠️ cần verify) |
| 11 | `11-ai-edtech-grading-tool.md` | Công cụ AI chấm bài/essay (mẫu 作文说) | Claude | ⚠️ xong draft (cấu trúc 5/5; web bị chặn → cần verify pass) |
| 12 | `12-ai-agent-skill-builder.md` | Xưởng skill/plugin/MCP cho AI agent | Claude | ✅ xong (167 dòng; web bị chặn → số ngoài brief ⚠️ cần verify) |
| 13 | `13-ai-video-editing-software.md` | Phần mềm dựng video AI niche | Codex (thiết kế) → DeepSeek | ✅ xong (182 dòng, 5/5) |
| 14 | `14-ai-chatbot-rag-agency.md` | Agency chatbot/RAG cho SME địa phương | Codex (thiết kế) → DeepSeek | ✅ xong (189 dòng, 5/5) |
| 15 | `15-ai-industry-consulting.md` | Tư vấn AI chuyển đổi số ngành dọc | DeepSeek | ✅ xong (175 dòng, 5/5) |
| 16 | `16-ai-legal-services-sme.md` | Dịch vụ pháp lý AI cho SME | Claude | ⚠️ xong draft (cấu trúc 5/5; web bị chặn → cần verify pass) |
| 17 | `17-ai-accounting-tax-sellers.md` | AI kế toán–thuế cho hộ kinh doanh/seller VN | Codex (thiết kế) → DeepSeek | ✅ xong (156 dòng, 5/5 — verify NQ198/NĐ70/TT10) |
| 18 | `18-ai-data-annotation-opc.md` | OPC cung cấp dữ liệu AI (annotation) | Codex → DeepSeek | ✅ xong (173 dòng, 5/5) |
| 19 | `19-agent-manager-workforce.md` | Agent Manager: đội ngũ AI thuê cho doanh nghiệp | Codex → DeepSeek | ✅ xong (161 dòng, 5/5) |
| 20 | `20-ai-ip-licensing-design.md` | Xưởng IP/thiết kế cấp phép bằng AI | Claude | ✅ xong (183 dòng, cấu trúc 5/5; web bị chặn → số ⚠️ cần verify) |

## Cách đọc bộ kế hoạch

1. Đọc `00-brief-va-template.md` (kiến thức chung đã thẩm định + template 11 mục).
2. Mỗi kế hoạch `NN-*.md` độc lập, theo đúng 11 mục: mô hình 1 slide → vì sao thắng ở TQ → thị trường VN/US → tech stack → vận hành → doanh thu/chi phí → lộ trình 0-180 ngày → rủi ro → KPI kill/scale → nguồn → câu hỏi mở.
3. Tài liệu nền: `plans/reports/260910-1118-opc-china-master-playbook.md` + `plans/reports/260910-1119-openclaw-opc-agentos-deep-dive.md`.

## Tiêu chí kiểm duyệt của Orchestrator (sẽ áp khi thu bài)

- [ ] File tồn tại, đúng tên, tiếng Việt, 150–300 dòng
- [ ] Đủ 11 mục template, không bỏ mục
- [ ] Claim ngoài brief có link nguồn; số ⚠️ được gắn cờ
- [ ] Lộ trình "cầm tay chỉ việc" với chi phí cụ thể VND/USD
- [ ] Khả thi 1 người trong 6 tháng, vốn ≤5.000 USD (trừ khi có lý do nêu rõ)
