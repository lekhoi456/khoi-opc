# 08 — Sổ tay rủi ro & bảng KILL/SCALE (TikTok Shop xuyên biên giới OPC)

> Kế hoạch gốc: `01-tiktok-shop-crossborder-opc.md` · Ngày: 2026-09-10 · Trạng thái: draft
> Người dùng: founder 1 người. Quy ước: mọi số tiền VND là ước lượng nội bộ ⚠️ trừ khi có nguồn; tỷ giá 1 USD = 26.000 VND (theo kế hoạch gốc).
> Vai trò theo nguyên tắc 4 của playbook: **người giữ rủi ro là founder** — tài liệu này là công cụ để giữ rủi ro, không phải để AI thay người quyết định.

---

## 1. Nguyên tắc chung

1. **Ngưỡng viết trước, quyết định viết sau:** mọi ngưỡng KILL/SCALE trong tài liệu này được khoá ngay ngày khai trương shop. Không sửa ngưỡng sau khi đã chạm ngưỡng (chỉ sửa trước, bằng văn bản, có lý do).
2. **Rủi ro tính bằng tiền:** mỗi rủi ro có ước lượng tác động VND. Nếu tổng tác động của 1 rủi ro >20% ngân sách 6 tháng (≈26tr), nó tự động vào danh sách giám sát hằng tuần.
3. **AND/OR phải rõ:** ngưỡng KILL ngày 90 của baseline là điều kiện **VÀ** (AND): *đơn <30/tháng VÀ lỗ luỹ kế >3.000 USD* — không được giết shop vì mới chỉ 1 vế.
4. **Mọi sự cố lớn đều có 24h đầu được kịch bản hoá sẵn (mục 5)** — khi khủng hoảng, không nghĩ, chỉ làm theo giờ.
5. **Đối trọng độc lập:** thuê 1 người ngoài (mentor/đối tác) giữ bản copy tài liệu này và quyền chất vấn khi founder muốn "thêm 1 tháng nữa".

---

## 2. Risk register — 20 rủi ro, 5 nhóm

Định nghĩa xác suất: **Thấp** (<20%/6 tháng) · **TB** (20–50%) · **Cao** (>50%).
Thang tác động: **T1** <10tr · **T2** 10–40tr · **T3** >40tr.

### Nhóm 1 — Nền tảng (TikTok Shop)

#### R1.1 Phí sàn tăng / chính sách đổi liên tục
- **Tình huống:** TikTok Shop VN tăng phí giao dịch/hoa hồng như đợt 09/05/2026 (tổng phí sàn 15–19% DT — [Báo Công Thương](https://congthuong.vn/tu-9-5-tiktok-shop-tiep-tuc-tang-bieu-phi-voi-nha-ban-hang-454850.html)); một đợt tăng thêm 3–5 điểm % có thể nuốt sạch lãi của shop đang hoà vốn.
- **Xác suất:** Cao · **Tác động:** T2 — mất 1,5–2,5tr/tháng ở DT 50tr, ≈18–30tr/năm ⚠️.
- **Chỉ báo sớm:** ① thông báo Seller Center trước 30–60 ngày; ② tin ngành về "biểu phí mới" (Báo Công Thương, group seller); ③ bảng đối soát thấy khoản khấu trừ mới/tăng đột biến.
- **Giảm thiểu:** ① giữ biên gộp ≥35% (giá bán = giá vốn ×3 trở lên — kế hoạch gốc); ② mở kênh dự phòng Shopee/Facebook từ M4; ③ đọc thông báo Seller Center hằng tuần (lịch thứ 2).
- **Kế hoạch B:** tính lại giá bán ngay trong 48h; cắt SKU biên <25%; nếu tổng phí >25% DT → chuyển trọng tâm sang Shopee, giữ TikTok làm kênh phụ.

#### R1.2 Khoá tài khoản / đình chỉ shop
- **Tình huống:** shop bị khoá vì nghi vấn gian lận, vi phạm IP, tỷ lệ hoàn cao hoặc khiếu nại khách tăng — mất kênh bán duy nhất, tiền đối soát bị giữ 90–180 ngày ⚠️.
- **Xác suất:** TB · **Tác động:** T3 — doanh thu 0 + 40tr hàng tồn kẹt + tiền đang giữ; tổng thiệt hại 50–80tr + 2–4 tháng ⚠️.
- **Chỉ báo sớm:** ① điểm sức khoẻ shop (Shop Health Score) giảm dưới 80; ② cảnh báo vi phạm đầu tiên (email/thông báo); ③ khiếu nại khách/vi phạm vận chuyển tăng 3 lần so với tuần trước.
- **Giảm thiểu:** ① compliance từ đơn số 1: video mở hàng + đóng gói + chứng từ (bài học 光年易达); ② không bán hàng gắn logo/nhãn hiệu người khác, tự xử lý ảnh bằng AI; ③ mở shop dự phòng thứ 2 từ M3–M4 (cùng hộ kinh doanh), phân tán 30% SKU chủ lực.
- **Kế hoạch B:** quy trình 24h ở mục 5.1; song song chuyển đơn sang Shopee/Facebook trong 48h; dùng bằng chứng video đã lưu để kháng nghị.

#### R1.3 Thuật toán giảm traffic organic
- **Tình huống:** thuật toán đổi → video organic từ 10–50k view/tuần rơi còn vài trăm; traffic mua phụ thuộc 100% ads → chi phí đội lên.
- **Xác suất:** Cao · **Tác động:** T2 — DT giảm 30–50% trong 1–2 tháng ≈ 15–30tr mất đi ⚠️.
- **Chỉ báo sớm:** ① view trung bình/video giảm >30% trong 14 ngày; ② tỷ lệ video đạt >1k view giảm; ③ CTR listing giảm dù giá/ảnh không đổi.
- **Giảm thiểu:** ① không đặt toàn bộ trứng 1 giỏ: 3–5 video/tuần đều đặn + 2 video quay tay; ② affiliate làm nguồn traffic thứ hai (mục tiêu ≤30% DT từ affiliate, không để phụ thuộc); ③ lưu danh sách khách lặp lại vào Zalo OA (traffic riêng).
- **Kế hoạch B:** tăng affiliate lên nhóm mồi 20–30%; chạy Shop Ads giữ rank; đẩy mạnh nhóm khách cũ qua Zalo OA.

#### R1.4 Content AI bị gắn cờ / giảm phân phối
- **Tình huống:** chính sách nội dung AI (数字人, video sinh) siết chặt — video AI không gắn nhãn bị hạ phân phối hoặc gỡ; shop bị cảnh cáo nội dung.
- **Xác suất:** TB · **Tác động:** T2 — mất kênh content chính, phải dựng lại 2–4 tuần ≈ 10–20tr ⚠️.
- **Chỉ báo sớm:** ① thông báo policy mới về AI content (kiểm tra hằng tuần); ② video bị gỡ lần đầu; ③ view video AI sinh giảm bất thường so với video tay.
- **Giảm thiểu:** ① tỷ lệ cứng 60% video tay / 40% AI ở giai đoạn đầu (kế hoạch gốc: 5 AI + 5 tay); ② gắn nhãn nội dung AI khi nền tảng yêu cầu; ③ founder duyệt 100% video trước đăng (giữ phần lõi).
- **Kế hoạch B:** chuyển nhanh sang 100% video tay/điện thoại trong 1 tuần; dùng AI chỉ để viết kịch bản, người quay.

### Nhóm 2 — Chuỗi cung ứng (1688 → VN)

#### R2.1 Đứt gãy nguồn hàng TQ (delay, tắc biên)
- **Tình huống:** lô hàng kẹt biên/tắc cảng 15–60 ngày (baseline đã dự kiến kịch bản này); SKU bán chạy hết tồn → mất rank + mất DT.
- **Xác suất:** TB · **Tác động:** T2 — hết hàng 2–4 tuần ≈ mất 10–20tr DT + chi phí leo rank lại ⚠️.
- **Chỉ báo sớm:** ① thông tin tắc biên/cảng trên group nhập hàng; ② thời gian vận chuyển TB của đơn hàng mẫu tăng >30%; ③ dịch vụ order báo delay/đổi tuyến.
- **Giảm thiểu:** ① 2–3 nguồn cung song song (kế hoạch gốc); ② tồn kho SKU chủ lực đủ 2 tuần (tăng 4 tuần vào mùa cao điểm); ③ nhập trước lịch sớm 10 ngày so với dự kiến bán hết.
- **Kế hoạch B:** dừng ads SKU hết hàng, đẩy SKU tồn kho; chuyển đơn sang nguồn B dù giá cao hơn 5–10%; đặt hàng gấp qua tuyến nhanh.

#### R2.2 Lô hàng lỗi 100% / sai mẫu hàng loạt
- **Tình huống:** lô 10–20tr về VN phát hiện lỗi toàn bộ (sai màu, sai thông số, vỡ) sau khi đã lên đơn bán.
- **Xác suất:** Thấp · **Tác động:** T3 — mất giá trị lô (10–40tr) + hoàn tiền khách + điểm shop tụt ⚠️.
- **Chỉ báo sớm:** ① ảnh kiểm đếm tại kho TQ lộ dấu hiệu sai; ② khách nhận hàng báo lỗi giống nhau ≥3 đơn; ③ nhà cung cấp phản hồi chậm khi hỏi thông số.
- **Giảm thiểu:** ① kiểm đếm + quay video tại kho TQ trước khi xuất (yêu cầu bắt buộc với dịch vụ order); ② đặt lô thử 5–10 sp trước khi lô lớn; ③ hợp đồng dịch vụ ghi rõ điều khoản bồi thường hàng lỗi.
- **Kế hoạch B:** quy trình 24h ở mục 5.2; hoàn tiền chủ động cho khách trước khi khiếu nại; dùng lô lỗi làm quà tặng/khuyến mãi nếu dùng được.

#### R2.3 Dịch vụ order 1688 lừa đảo / bùng tiền
- **Tình huống:** dịch vụ order nhận tiền lô 10–20tr rồi biến mất (tài khoản Zalo/FB xoá), đặc biệt khi giao dịch lần đầu qua tin nhắn.
- **Xác suất:** TB · **Tác động:** T2 — mất trực tiếp tiền lô 10–40tr ⚠️.
- **Chỉ báo sớm:** ① giá rẻ bất thường so với mặt bằng; ② không có địa chỉ kho/giấy tờ, chỉ nhận chuyển khoản cá nhân; ③ phản hồi chậm sau khi nhận cọc, né kiểm đếm.
- **Giảm thiểu:** ① lô đầu tiên ≤5tr, chia nhỏ 2–3 dịch vụ cùng lúc (kế hoạch gốc: so sánh 2 đơn vị); ② ưu tiên đối tác có chính sách kiểm đếm + bồi thường bằng văn bản; ③ không chuyển toàn bộ trước, giữ lại 30% đến khi hàng về.
- **Kế hoạch B:** báo ngân hàng phong toả + công an khu vực trong 24h; dùng dịch vụ dự phòng thay thế ngay; ghi nhận mẫu lừa đảo vào SOP chọn đối tác.

#### R2.4 Phụ thuộc 1 nhà vận chuyển TQ–VN
- **Tình huống:** nhà VC duy nhất tăng giá/tắc tuyến/dừng nhận → toàn bộ chuỗi nhập tê liệt dù có nguồn hàng.
- **Xác suất:** TB · **Tác động:** T1 — trễ 1–2 tuần, chi phí tăng 1–3tr/lô ⚠️.
- **Chỉ báo sớm:** ① báo giá tăng liên tục; ② tỷ lệ trễ đơn tăng; ③ thông báo dừng tuyến/khu vực.
- **Giảm thiểu:** ① ký 2 nhà VC từ ngày đầu (kế hoạch gốc: so sánh 2 đơn vị vận chuyển); ② luân phiên gửi 30% đơn qua bên phụ; ③ hỏi giá định kỳ 3 tháng để không bị "nuôi giá".
- **Kế hoạch B:** chuyển toàn bộ sang nhà VC phụ trong 24h; tạm nhập qua tuyến khác (chính ngạch nếu lô lớn).

### Nhóm 3 — Tài chính

#### R3.1 Hoàn hàng / gian lận hoàn tiền cao
- **Tình huống:** khách nhận hàng rồi báo lỗi/không nhận để hoàn tiền; case 光年易达 từng mất 60–70% đơn vì gian lận hoàn trả trước khi dựng video mở hàng (playbook mục 3).
- **Xác suất:** Cao (thị trường VN) · **Tác động:** T2 — tỷ lệ hoàn 5%→20% = mất ~15% DT + phí ship 2 chiều ≈ 10–30tr/tháng ở quy mô lớn ⚠️.
- **Chỉ báo sớm:** ① tỷ lệ hoàn tuần vượt 5%; ② cùng 1 khách/tệp khách hoàn lặp; ③ đơn COD bùng hoặc khiếu nại "hàng lỗi" tăng.
- **Giảm thiểu:** ① video mở hàng + đóng gói + chứng từ mọi đơn từ đơn số 1 (bài học copy số 2); ② blacklist khách hoàn gian lận (chia sẻ trong nhóm seller); ③ chính sách đổi trả 7 ngày rõ ràng trên listing + chatbot.
- **Kế hoạch B:** khi tỷ lệ hoàn >10% trong 2 tuần: tạm tắt COD ở vùng rủi ro, bật phí ship khách trả; nộp bằng chứng video lên sàn tranh chấp từng đơn; hạ affiliate ở SKU bị hoàn nhiều.

#### R3.2 Đốt tiền quảng cáo (ROAS thấp)
- **Tình huống:** Shop Ads 200–500k/ngày nhưng ROAS <1 kéo dài; ngân sách 15tr (3 tháng đầu) cạn trước khi tìm được video thắng.
- **Xác suất:** Cao · **Tác động:** T1 — mất tối đa 15tr ngân sách ads + cơ hội ⚠️.
- **Chỉ báo sớm:** ① ROAS <1 trong 3 ngày liên tiếp; ② CTR video <1% dù đã chạy 2 ngày; ③ chi phí mỗi đơn từ ads > biên lợi nhuận/đơn.
- **Giảm thiểu:** ① quy tắc cứng: 7 ngày ROAS <1 → tắt campaign (không "chờ thêm"); ② chỉ chạy ads cho 2 video tốt nhất (đã có view organic); ③ tận dụng Dynamic Commission giảm phí khi chạy ads (kế hoạch gốc).
- **Kế hoạch B:** ngừng ads 100% trong 1 tuần, chạy lại bằng affiliate mồi (hoa hồng 20–30%) — trả tiền theo kết quả thay vì trả trước.

#### R3.3 Kẹt dòng tiền (chu kỳ nhập hàng dài)
- **Tình huống:** tiền nằm trong hàng tồn 20–40tr + TikTok giữ tiền đối soát 7–14 ngày ⚠️ → không còn tiền nhập lô mới dù đang có đơn.
- **Xác suất:** TB · **Tác động:** T2 — đứt hàng 1–2 tuần, mất đà tăng trưởng ≈ 10–20tr ⚠️.
- **Chỉ báo sớm:** ① tồn kho chủ lực <1 tuần bán; ② tiền mặt < chi phí cố định 2 tháng; ③ nhập lô mới phải vay/ứng tiền cá nhân.
- **Giảm thiểu:** ① giữ ngân quỹ tối thiểu 15tr (quỹ dự phòng trong 130tr ngân sách); ② nhập lô nhỏ xoay vòng 2 lần/tháng thay vì 1 lô lớn; ③ đối soát tiền hằng ngày bằng AI (AI法务财务) để biết trước 7 ngày.
- **Kế hoạch B:** ngừng nhập SKU chậm, chỉ nhập 3 SKU chủ lực; bán nhanh tồn chậm giá vốn để xoay tiền; hoãn kế hoạch shop 2.

#### R3.4 Tỷ giá / biến động chi phí nhập
- **Tình huống:** tỷ giá NDT/VND hoặc phí vận chuyển tăng 5–10% → giá vốn 40% thành 44%, biên gộp bị bào.
- **Xác suất:** Thấp · **Tác động:** T1 — tăng chi 1–3tr/tháng ở DT 50tr ⚠️.
- **Chỉ báo sớm:** ① tỷ giá tăng >3% trong 1 tháng; ② dịch vụ order báo tăng phí; ③ bảng giá nhà VC mới cao hơn 5%.
- **Giảm thiểu:** ① công thức giá về tay cập nhật mỗi lô ([nhaphangchina.net](https://nhaphangchina.net/cach-tinh-gia-ve-tay-khi-order-hang-trung-quoc-chuan-nhat-2026/)); ② đệm biên gộp ≥35%; ③ mua lô khi tỷ giá thuận, giữ tồn 4 tuần.
- **Kế hoạch B:** tăng giá bán 5–10% cho lô mới; cắt SKU biên thấp; chuyển bớt sang SKU nội địa nếu có.

### Nhóm 4 — Pháp lý & tuân thủ

#### R4.1 Thuế hộ kinh doanh (khoán, hoá đơn)
- **Tình huống:** không đăng ký/kê khai đúng → truy thu + phạt; bán lẻ online thường thuế khoán GTGT+TNCN ~1–1,5% DT ⚠️ (kế hoạch gốc, cần xác nhận chi cục).
- **Xác suất:** TB · **Tác động:** T2 — truy thu + phạt 5–20tr cho 1–2 năm ⚠️.
- **Chỉ báo sớm:** ① thư/công văn chi cục thuế; ② sàn gửi thông báo yêu cầu mã số thuế; ③ doanh thu vượt ngưỡng khoán.
- **Giảm thiểu:** ① lập hộ kinh doanh cá thể tuần 1 (kế hoạch gốc, lệ phí ~100k ⚠️); ② xuất hoá đơn điện tử theo Thông tư 78; ③ hỏi mức khoán tại chi cục trước khi bán.
- **Kế hoạch B:** liên hệ chi cục để được hướng dẫn bổ sung kê khai; cân nhắc chuyển lên công ty TNHH MTV khi DT >1 tỷ/năm.

#### R4.2 Vi phạm IP / nhãn hiệu (hàng nhái logo)
- **Tình huống:** SKU vô tình dính logo/hình nhân vật có bản quyền (ảnh lấy thẳng 1688) → shop bị khoá + bồi thường theo luật SHTT.
- **Xác suất:** TB · **Tác động:** T3 — khoá shop (xem R1.2) + yêu cầu bồi thường 20–100tr ⚠️.
- **Chỉ báo sớm:** ① listing bị gỡ vì IP; ② cảnh báo "hàng giả/vi phạm thương hiệu"; ③ phát hiện logo/thiết kế giống thương hiệu khi soi ảnh 1688.
- **Giảm thiểu:** ① check nhãn hiệu trước khi chọn hàng (bước bắt buộc trong prompt AI选品师); ② tự chụp/xử lý lại ảnh bằng AI, không dùng ảnh gốc 1688; ③ không bán hàng thương hiệu, chọn sản phẩm OEM.
- **Kế hoạch B:** gỡ toàn bộ SKU nghi vấn trong 2h; kháng nghị kèm bằng chứng nguồn gốc nếu bị nhầm; chuyển sang ngách khác nếu toàn bộ danh mục dính IP.

#### R4.3 Vi phạm Nghị định 13/2023/NĐ-CP (dữ liệu cá nhân)
- **Tình huống:** bot CSKH lưu SĐT/địa chỉ khách vào Airtable/Zalo không có cam kết bảo vệ dữ liệu → vi phạm quy định bảo vệ dữ liệu cá nhân VN.
- **Xác suất:** Thấp–TB · **Tác động:** T2 — phạt hành chính (mức theo NĐ13) + xử lý dữ liệu ⚠️.
- **Chỉ báo sớm:** ① khiếu nại khách về tin nhắn quảng cáo không mong muốn; ② dữ liệu khách bị lộ (nhóm nội bộ); ③ yêu cầu xoá dữ liệu từ khách.
- **Giảm thiểu:** ① chỉ lưu dữ liệu tối thiểu phục vụ đơn hàng; ② Airtable để chế độ riêng tư, giới hạn người/tool truy cập; ③ mẫu câu xin phép khi thu thập qua Zalo OA (đồng ý trước khi nhận thông tin khuyến mãi).
- **Kế hoạch B:** ngừng chiến dịch tin nhắn, rà soát toàn bộ dữ liệu đang lưu, xoá dữ liệu khách yêu cầu trong 72h.

#### R4.4 US: LLC + Form 5472 + FTC disclosure (giai đoạn 2)
- **Tình huống:** mở shop US mà bỏ sót kê khai Form 5472 (LLC 1 thành viên do người nước ngoài sở hữu) hoặc KOC không gắn nhãn quảng cáo — FTC phạt tới $51.744/vi phạm ([TheAmericanLLC](https://www.theamericanllc.com/llc/tiktok-shop)).
- **Xác suất:** TB · **Tác động:** T3 — phạt hàng chục triệu VND + mất quyền bán US ⚠️.
- **Chỉ báo sớm:** ① nhận thư IRS/FTC; ② đối tác/kế toán nhắc nộp form; ③ KOC đăng video quảng cáo không gắn nhãn.
- **Giảm thiểu:** ① chỉ mở US khi VN có lãi (gate baseline); ② thuê dịch vụ kế toán US gói rẻ ngay khi DT >$2k/tháng (kế hoạch gốc); ③ hợp đồng KOC ghi rõ nghĩa vụ gắn nhãn quảng cáo.
- **Kế hoạch B:** tạm dừng shop US, nộp bổ sung form + phạt qua kế toán; chấm dứt hợp đồng KOC vi phạm.

### Nhóm 5 — Cá nhân (founder)

#### R5.1 Burn-out / suy sụp sức khoẻ
- **Tình huống:** founder ôm quá nhiều việc (duyệt SKU, video, khách khiếu nại, đóng gói) → kiệt sức sau 8–12 tuần, bỏ dở hệ thống đúng lúc cần nhất.
- **Xác suất:** Cao · **Tác động:** T3 — ngừng vận hành = mất toàn bộ (130tr + thời gian) ⚠️.
- **Chỉ báo sớm:** ① giờ vận hành liên tục >4h/ngày trong 2 tuần; ② giấc ngủ kém/tâm trạng chán việc, né mở Seller Center; ③ video mới không ra trong 7 ngày.
- **Giảm thiểu:** ① mục tiêu cứng <2h/ngày vận hành, nghỉ thứ 7 (kế hoạch gốc); ② AI gánh 80% khối lượng: CSKH đêm, báo cáo, listing; ③ thuê CTV đóng gói ngay khi >30 đơn/tháng.
- **Kế hoạch B:** kích hoạt "chế độ tối thiểu" viết sẵn: tắt ads, giữ CSKH bot, chỉ duyệt 2 việc/ngày trong 2 tuần nghỉ ngơi; nhờ CTV/đối tác giữ shop tạm.

#### R5.2 Phụ thuộc 1 người (key-man)
- **Tình huống:** founder ốm/gia đình có việc 2–4 tuần → không ai duyệt video, xử lý tranh chấp, quyết định giá.
- **Xác suất:** TB · **Tác động:** T3 — gián đoạn kéo dài, mất rank và khách ⚠️.
- **Chỉ báo sớm:** ① lịch cá nhân có dấu hiệu quá tải/ốm; ② founder là người duy nhất biết mật khẩu/quy trình; ③ không có ai ngoài founder trả lời được khách khiếu nại nặng.
- **Giảm thiểu:** ① toàn bộ SOP đóng gói thành tài liệu + prompt (tài sản kể cả khi kill — tinh thần 景行); ② phân quyền hạn chế cho 1 trợ lý bán thời gian từ M4; ③ lưu mật khẩu/passkey ở két an toàn + hướng dẫn khẩn cấp 1 trang.
- **Kế hoạch B:** trợ lý/đối tác vận hành chế độ tối thiểu theo hướng dẫn khẩn cấp; shop chỉ giữ trạng thái "đang hoạt động" chờ founder về.

#### R5.3 Lệch khỏi ngách / hội chứng "sản phẩm mới sáng bóng"
- **Tình huống:** thấy ngách khác đang hot → nhập thêm lung tung, phá vỡ ngách dọc 1 mũi nhọn, tồn kho phân mảnh.
- **Xác suất:** Cao · **Tác động:** T1 — mất tập trung, thêm 5–10tr tồn chết ⚠️.
- **Chỉ báo sớm:** ① Airtable xuất hiện SKU ngoài ngách; ② thời gian duyệt dành cho "ý tưởng mới" nhiều hơn vận hành; ③ tồn chậm >30 ngày tăng.
- **Giảm thiểu:** ① quy tắc: mọi SKU mới phải nằm trong ngách đã khai báo, ngoài ngách = cần văn bản đổi chiến lược; ② 1 tháng chỉ test 1 ngách phụ, tối đa 5 SKU; ③ xem lại tài liệu này mỗi thứ 2 (lịch có sẵn).
- **Kế hoạch B:** thanh lý ngay tồn ngoài ngách; quay lại danh mục gốc 100%.

#### R5.4 Tâm lý "thêm 1 tháng nữa" (chi phí chìm)
- **Tình huống:** shop chạm ngưỡng KILL nhưng founder tự thuyết phục "sắp bùng rồi", đổ thêm tiền/ thời gian tháng thứ 4, 5, 6.
- **Xác suất:** Cao · **Tác động:** T2 — vượt ngân sách thêm 10–30tr + mất cơ hội đổi ngách ⚠️.
- **Chỉ báo sớm:** ① các câu nói "chỉ cần thêm 1 tháng", "chắc do mùa thấp điểm"; ② founder tự ý sửa ngưỡng trong đầu; ③ chi tiêu cá nhân bắt đầu bù cho shop.
- **Giảm thiểu:** ① ngưỡng viết ra giấy, ký tên, đưa người ngoài giữ bản sao; ② báo cáo KPI tự động 6h sáng không cho phép "không nhìn"; ③ prompt "hội đồng rủi ro AI" chấm theo ngưỡng, founder không tự chấm.
- **Kế hoạch B:** áp dụng toàn bộ mục 6 (quy tắc dừng lỗ tâm lý) — bắt buộc, không thương lượng.

---

## 3. Ma trận ưu tiên (xác suất × tác động)

Chấm điểm: XS Thấp=1, TB=2, Cao=3 · Tác động T1=1, T2=2, T3=3.

| Mã | Rủi ro | XS | TD | Điểm | Nhóm |
|---|---|---|---|---|---|
| R5.1 | Burn-out founder | 3 | 3 | **9** | Cá nhân |
| R1.2 | Khoá tài khoản | 2 | 3 | **6** | Nền tảng |
| R4.2 | Vi phạm IP/nhãn hiệu | 2 | 3 | **6** | Pháp lý |
| R5.2 | Key-man (phụ thuộc 1 người) | 2 | 3 | **6** | Cá nhân |
| R3.1 | Hoàn/gian lận hoàn tiền | 3 | 2 | **6** | Tài chính |
| R1.1 | Phí sàn tăng | 3 | 2 | 6 | Nền tảng |
| R1.3 | Thuật toán giảm traffic | 3 | 2 | 6 | Nền tảng |
| R5.4 | "Thêm 1 tháng nữa" | 3 | 2 | 6 | Cá nhân |
| R2.3 | Dịch vụ order lừa đảo | 2 | 2 | 4 | Chuỗi cung |
| R1.4 | Content AI bị gắn cờ | 2 | 2 | 4 | Nền tảng |
| R2.1 | Đứt gãy nguồn TQ | 2 | 2 | 4 | Chuỗi cung |
| R3.3 | Kẹt dòng tiền | 2 | 2 | 4 | Tài chính |
| R4.1 | Thuế hộ kinh doanh | 2 | 2 | 4 | Pháp lý |
| R4.4 | US LLC/FTC | 2 | 2 | 4 | Pháp lý |
| R2.2 | Lô hàng lỗi 100% | 1 | 3 | 3 | Chuỗi cung |
| R5.3 | Lệch ngách | 3 | 1 | 3 | Cá nhân |
| R3.2 | Đốt tiền ads | 3 | 1 | 3 | Tài chính |
| R2.4 | Phụ thuộc 1 nhà VC | 2 | 1 | 2 | Chuỗi cung |
| R4.3 | Nghị định 13/2023 | 1 | 2 | 2 | Pháp lý |
| R3.4 | Tỷ giá/chi phí nhập | 1 | 1 | 1 | Tài chính |

### Top 5 rủi ro giám sát hằng tuần (thứ 2, 30 phút, trước khi đọc KPI)

1. **R5.1 Burn-out** — đếm giờ vận hành tuần trước; nếu >14h/tuần 2 tuần liên tiếp → cắt việc ngay (thuê CTV/tắt ads).
2. **R1.2 Khoá tài khoản** — check Shop Health Score + hộp thư cảnh báo + khiếu nại tuần.
3. **R4.2 Vi phạm IP** — rà nhanh 10 SKU mới nhất: có logo/hình nhân vật nghi vấn không.
4. **R5.2 Key-man** — kiểm tra SOP khẩn cấp + phân quyền còn hiệu lực; test trợ lý 1 câu hỏi ngẫu nhiên.
5. **R3.1 Hoàn gian lận** — đọc báo cáo hoàn tuần: tỷ lệ, khách lặp, vùng địa lý bất thường.

---

## 4. Bảng KILL/SCALE theo tháng 1–12

> Cơ sở số liệu: AOV 250k, biên/đơn sau phí sàn 16% + giá vốn 40% + ads/affiliate 10% + fulfillment 15k ≈ **70k/đơn** ⚠️; phí cố định ≈3tr/tháng → hoà vốn ≈ 45–50 đơn/tháng (khớp kế hoạch gốc).
> **Cổng KILL chính (ngày 90):** đơn <30/tháng **VÀ** lỗ luỹ kế >3.000 USD (78tr) → KILL.
> **Cổng SCALE chính:** lãi >1.500 USD/tháng (≈39tr) 3 tháng liên tiếp **VÀ** <2h/ngày → mở US.

| Tháng | Ngưỡng đơn | Lãi/lỗ | Hoàn % | Giờ vận hành | Hành động |
|---|---|---|---|---|---|
| 1 | ≥5 (tốt ≥20) | Lỗ tháng ≤10tr | <12% | ≤5h/ngày | **Tiếp tục** nếu ≥5 đơn. **Cảnh báo** nếu 1–4 đơn: tăng video lên 7/tuần. **Cảnh báo đỏ** nếu 0 đơn sau 30 ngày + ≥10 video: xem lại ngách, chưa kill (chưa đủ 90 ngày) |
| 2 | ≥15 | Lỗ luỹ kế ≤25tr | <10% | ≤4h/ngày | **Tiếp tục** nếu ≥15. **Cảnh báo** nếu 5–14: đổi content + mở affiliate 10–15%. **Cảnh báo đỏ** nếu <5: chuẩn bị phương án pivot (đổi ngách trong ≤2 tuần) |
| 3 (ngày 90) | ≥30 | Lỗ luỹ kế ≤78tr | <8% | ≤3h/ngày | **KILL** nếu đơn <30 **VÀ** lỗ >78tr. **Gia hạn có điều kiện tối đa 30 ngày** nếu 20–29 đơn nhưng đơn tăng ≥50%/tháng và lỗ <78tr. **Tiếp tục** nếu ≥30 đơn |
| 4 | ≥40 | Lỗ tháng ≤2tr (gần hoà vốn) | <6% | ≤3h/ngày | **Tiếp tục** nếu ≥40. **Cảnh báo** nếu lùi dưới mức tháng 3 → coi như trượt cổng, quay lại điều kiện KILL |
| 5 | ≥50 | **Hoà vốn** (lãi ≥0) | <6% | ≤2,5h/ngày | Cột mốc hoà vốn baseline (T5). **Cảnh báo** nếu chưa hoà vốn: cắt chi phí cố định, tăng giá 5% |
| 6 | ≥55 | Lãi ≥3tr | <5% | <2h/ngày | **Tiếp tục.** Nếu M4–6 đơn ≥50 liên tiếp và lãi ≥0: chuẩn bị mở shop 2 (cùng ngách lệch) |
| 7 | ≥60 | Lãi ≥5tr | <5% | <2h/ngày | **Mở shop 2** nếu M5–7 đơn ≥50/tháng liên tục và giờ <2h (điều kiện kế hoạch gốc: shop 1 có 50+ đơn/tháng) |
| 8 | ≥65 | Lãi ≥8tr | <5% | <2h/ngày | **Tiếp tục.** Shop 2 chạy ổn định ≥20 đơn/tháng thì cân nhắc CTV đóng gói dài hạn |
| 9 | ≥70 | Lãi ≥10tr | <5% | <2h/ngày | **Tiếp tục.** Đối chiếu cổng scale US (cần 39tr/tháng — xem ghi chú dưới bảng) |
| 10 | ≥75 | Lãi ≥12tr | <5% | <2h/ngày | **Tiếp tục** nếu đang leo. **Mở US** chỉ khi lãi >39tr/tháng đã đạt 2 tháng liên tiếp trước đó |
| 11 | ≥80 | Lãi ≥15tr | <5% | <2h/ngày | **Tiếp tục.** Nếu lãi >39tr/tháng 3 tháng liên tiếp → kích hoạt lộ trình US (LLC → EIN → Mercury → 3PL) |
| 12 | ≥90 | Lãi ≥20tr | <5% | <2h/ngày | **SCALE US** theo kế hoạch gốc bước 90–180 ngày. Hoặc scale VN: tuyển người làm video/content đầu tiên (OPC → STC) |

**Ghi chú quan trọng:**
- **Ngưỡng lãi scale 39tr/tháng cao hơn kịch bản "tốt" của kế hoạch gốc** (M10–12 lãi 20–35tr). Hai cách hiểu hợp lệ: (a) giữ nguyên 39tr → US có thể chỉ mở sau tháng 12; (b) hạ ngưỡng về 20tr/tháng 3 tháng liên tiếp → khả thi từ M10. **Quyết định trước M9, ghi bằng văn bản** (xem câu hỏi mở).
- KILL không chỉ ở tháng 3: bất kỳ tháng nào từ M4, nếu **đơn <30 trong 2 tháng liên tiếp HOẶC lỗ luỹ kế >78tr** → KILL shop đó. Với 2 shop: giết shop lỗ, giữ shop lãi.
- Tất cả ngưỡng đo bằng báo cáo KPI tự động 6h sáng; founder chỉ duyệt, không tự thống kê (chống tự dối).

---

## 5. Kịch bản khủng hoảng top 3 — quy trình 24h đầu

### 5.1 Khoá tài khoản TikTok Shop

| Giờ | Hành động |
|---|---|
| 0–1h | Chụp màn hình thông báo + mã lý do; **dừng ngay** mọi hành động tự động (n8n đăng bài, bot CSKH trả lời chính sách); không thao tác cuống (đăng nhập lại liên tục làm tệ hơn). |
| 1–3h | Tra cứu mục vi phạm trong Seller Center; đọc đúng điều khoản bị dẫn chiếu; kiểm tra xem có phải nhầm lẫn không (ví dụ IP, khiếu nại khách, hoàn cao). |
| 3–6h | Nộp **kháng nghị (appeal) lần 1** qua Seller Center kèm bằng chứng: video mở hàng/đóng gói lưu sẵn, hoá đơn nhập hàng, chứng từ vận chuyển. Chụp màn hình biên bản nộp. |
| 6–12h | Thông báo nội bộ khách đang chờ (bot chế độ "đơn đang xử lý, không hoàn trước khi shop trả lời"); liên hệ hỗ trợ qua email/kênh chính thức; nhờ mentor/group seller rà kinh nghiệm trường hợp giống. |
| 12–24h | Nếu chưa mở: kích hoạt **kế hoạch B kênh** — đăng 3 SKU chủ lực lên Shopee/Facebook, đổi link Zalo OA, rút 30% tồn về kho nhà; chuẩn bị hồ sơ appeal lần 2. |
| Cổng 24h | Không có phản hồi → thuê luật sư/tư vấn chuyên e-com (ngân sách ≤2tr ⚠️). Cổng 72h: vẫn khoá → công bố kênh Shopee là kênh chính tạm, không chờ đợi thụ động. |

### 5.2 Lô hàng lỗi 100% (sai mẫu, vỡ, lỗi hàng loạt)

| Giờ | Hành động |
|---|---|
| 0–1h | **Ẩn ngay** toàn bộ listing dùng lô này + tạm khoá tồn trong Airtable; dừng ads/affiliate các SKU đó. |
| 1–3h | Quay video + chụp ảnh từng mẫu lỗi (đủ bằng chứng), lập bảng lỗi đếm số lượng; gọi/zalo dịch vụ order báo sự cố. |
| 3–6h | Gửi yêu cầu bồi thường chính thức (ảnh + bảng lỗi + điều khoản hợp đồng); nếu là lỗi nhà máy → dịch vụ order phải đứng ra khiếu nại nhà cung cấp trên 1688. |
| 6–12h | Thông báo **chủ động** cho khách đã đặt: 2 lựa chọn — hoàn tiền 100% + voucher 30k, hoặc chờ hàng thay thế 5–7 ngày (nếu nguồn B có). Bot CSKH bật kịch bản này trong 1 phút. |
| 12–24h | Chốt phương án: (a) hoàn toàn bộ đơn bị ảnh hưởng (ưu tiên giữ điểm shop); (b) đặt lô thay thế nguồn B nếu đã kiểm; (c) cập nhật SOP kiểm đếm: bắt buộc video kiểm 100% lô >10tr. |
| Cổng 24h | Dịch vụ order không phản hồi/không bồi thường → chặn hợp tác, đưa vào danh sách đen, báo cộng đồng; thiệt hại ghi nhận vào bảng theo dõi rủi ro R2.2. |

### 5.3 Bùng nổ đơn quá tải (sốc đơn)

| Giờ | Hành động |
|---|---|
| 0–1h | Đánh giá công suất thật: số đơn chờ đóng, số đơn đóng được/ngày hiện tại; nếu tồn đơn >3 ngày công → kích hoạt chế độ khẩn cấp. |
| 1–3h | Liên hệ 2 CTV đóng gói dự phòng + 1 dịch vụ fulfillment (đã lập danh sách sẵn từ M3); chốt hỗ trợ ngay hôm nay. |
| 3–6h | Đăng video "cảm ơn + xin kiên nhẫn 3–5 ngày" lên kênh shop; bot CSKH bật chế độ thông báo delay giao; tạm tắt Shop Ads để giảm đơn mới về nếu quá tải >150% công suất. |
| 6–12h | Điều đơn theo FIFO (ngày thanh toán), ưu tiên khách lặp lại/VIP; mua gấp vật tư đóng gói; thuê shipper gom nếu cần. |
| 12–24h | Chạy ca đóng gói (kể cả founder); theo dõi tỷ lệ giao đúng hạn và khiếu nại trễ; nếu xu hướng đơn cao kéo dài >3 ngày → ký CTV dài hạn, cập nhật chi phí vào mô hình. |
| Cổng 24h | Tỷ lệ giao trễ >10% hoặc đơn tồn >5 ngày → giảm cầu chủ động (tắt ads, tăng giá 5–10%, ẩn SKU cháy hàng) — ưu tiên chất lượng dịch vụ hơn GMV. |

---

## 6. Quy tắc dừng lỗ (stop-loss) tài chính & tâm lý

### 6.1 Dừng lỗ tài chính (ngưỡng cứng, không bàn cãi)

1. **Trần tuyệt đối:** lỗ luỹ kế chạm **78tr (3.000 USD)** → dừng mọi chi tiêu mới trong vòng 24h: tắt ads, ngừng nhập lô, ngừng thuê ngoài. Trong 2 tuần tiếp theo chỉ được: thanh lý tồn, hoàn tất đơn, đóng shop gọn gàng (tinh thần 景行: "sai thì bỏ trong vài tuần").
2. **Trần giai đoạn:** M1 lỗ ≤15tr · M2 luỹ kế ≤25tr · M3 luỹ kế ≤50tr (chỉ cho phép tới 78tr nếu đơn tăng ≥30%/tháng). Tổng ngân sách không bao giờ vượt 130tr (5.000 USD) — không có ngoại lệ.
3. **Ngưỡng ads:** ROAS <1 trong 7 ngày liên tiếp → tắt campaign; mỗi video chỉ được thử lại tối đa 3 lần ngân sách nhỏ.
4. **Ngưỡng SKU:** 14 ngày 0 view → tắt listing; 30 ngày 0 đơn → thanh lý tồn bằng mọi giá ≥ giá vốn −20%.
5. **Ngưỡng hoàn:** tỷ lệ hoàn >10% trong 2 tuần liên tiếp → tạm tắt COD vùng rủi ro + siết chính sách đổi trả.
6. **Cấm tuyệt đối:** dùng tiền sinh hoạt cá nhân, vay nóng, hoặc rút quỹ dự phòng gia đình để "cứu shop". Shop là khoản đầu tư có trần, không phải con bạc.

### 6.2 Dừng lỗ tâm lý (chống "thêm 1 tháng nữa")

1. **Cam kết trước (pre-commitment):** ngày khai trương, founder viết tay và ký 1 trang A4: ngưỡng KILL ngày 90 + trần 78tr + cam kết "không gia hạn khi đã chạm ngưỡng". Gửi ảnh cho 1 người ngoài (mentor/đối tác) giữ — người này có quyền chất vấn.
2. **Quy tắc 3 KHÔNG:** không quyết định kill/scale trong 22h–6h; không quyết định khi đói/mệt/ốm; không sửa ngưỡng sau khi đã chạm (sửa trước = viết lại giấy, nêu lý do bằng dữ liệu).
3. **Bảng chi phí chìm:** mỗi lần nghĩ "thêm 1 tháng nữa", bắt buộc viết ra 2 con số: (a) 1 tháng thêm = 3tr cố định + thời gian founder; (b) số tháng liên tiếp dưới đường tăng trưởng yêu cầu. Nếu (b) ≥2 → quy trình kill tự động khởi động, không cần quyết định nữa.
4. **Nghỉ 48h rồi mới quyết:** mọi quyết định KILL/SCALE thực thi sau 48h kể từ khi chạm ngưỡng — đủ thời gian để cảm xúc lắng, nhưng quá hạn 48h mà chưa hành động thì người giữ giấy cam kết có quyền gọi điện.
5. **Đối trọng AI:** lập prompt "Hội đồng quản trị rủi ro" (DeepSeek API) chấm hằng tuần theo đúng ngưỡng trong bảng mục 4; founder KHÔNG được tự chấm, chỉ đọc kết quả. AI không quyết định thay người, nhưng AI không biết nói dối ngưỡng.
6. **Kỷ luật ngược ở chiều scale:** không scale theo 1 tháng đột biến (1 tháng lãi 45tr không phải là "3 tháng liên tiếp"); không mở shop 2 trước khi shop 1 đạt 50+ đơn/tháng ổn định 2 tháng.
7. **Kill = thắng một nửa:** khi kill đúng ngưỡng, đóng gói toàn bộ prompt/SOP/video/data thành "skill" — đó là tài sản để mô hình tiếp theo (ngách khác) xuất phát nhanh gấp 3. Tinh thần này ghi sẵn trong giấy cam kết để lúc kill không coi là thất bại toàn phần.

---

## 7. Thay đổi so với baseline (kế hoạch 01)

1. **Cụ thể hoá** 7 rủi ro của kế hoạch gốc thành 20 rủi ro có điểm số, tác động VND, chỉ báo sớm và kế hoạch B — baseline chỉ liệt kê + 1 câu phòng thủ.
2. **Bổ sung cổng giám sát hằng tuần top 5** (baseline không có cơ chế giám sát rủi ro định kỳ).
3. **Thêm các ngưỡng trung gian theo tháng 1–12** (đơn, lãi, hoàn %, giờ vận hành) — baseline chỉ có 1 cổng KILL ngày 90 và 1 cổng SCALE.
4. **Làm rõ điều kiện AND của KILL** và bổ sung cơ chế gia hạn có kiểm soát (tối đa 30 ngày, đơn tăng ≥50%/tháng) — baseline không nói gì khi chỉ đạt 1 trong 2 vế.
5. **Phát hiện mâu thuẫn nội tại:** ngưỡng SCALE lãi >1.500 USD/tháng (≈39tr) cao hơn kịch bản "tốt" 12 tháng của baseline (lãi 20–35tr) → đề xuất chốt lại trước M9 (giữ 39tr hoặc hạ 20tr).
6. **Thêm quy tắc dừng lỗ tâm lý** (pre-commitment, 3 KHÔNG, đối trọng AI) — baseline chỉ có ngưỡng tài chính.

## 8. Nguồn tham khảo

- [Báo Công Thương — Từ 9/5 TikTok Shop tăng biểu phí](https://congthuong.vn/tu-9-5-tiktok-shop-tiep-tuc-tang-bieu-phi-voi-nha-ban-hang-454850.html) — truy cập 10/09/2026.
- [TheAmericanLLC — US LLC cho TikTok Shop, phạt FTC](https://www.theamericanllc.com/llc/tiktok-shop) — truy cập 10/09/2026.
- [Nhập Hàng China — cách tính giá về tay](https://nhaphangchina.net/cach-tinh-gia-ve-tay-khi-order-hang-trung-quoc-chuan-nhat-2026/) — truy cập 10/09/2026.
- Master playbook nội bộ: `plans/reports/260910-1118-opc-china-master-playbook.md` (case 光年易达 chống hoàn trả gian lận, nguyên tắc 10 điều).
- Kế hoạch gốc: `plans/260910-opc-20-models/01-tiktok-shop-crossborder-opc.md`.

## 9. Câu hỏi mở

1. **Ngưỡng SCALE:** giữ 1.500 USD/tháng (39tr) hay hạ về 20tr/tháng 3 tháng liên tiếp để khớp kịch bản tài chính? Ai là người quyết định và chốt trước tháng 9?
2. TikTok Shop VN thực tế giữ tiền đối soát bao nhiêu ngày khi shop bị đình chỉ? Có kênh kháng nghị chính thức nào ngoài Seller Center không?
3. Mức bồi thường hàng lỗi thực tế của các dịch vụ order 1688 hiện tại là bao nhiêu % và bao lâu trả — chưa có dữ liệu công khai.
4. Ngưỡng thuế khoán chính xác cho hộ kinh doanh bán online tại địa phương của founder (Hà Nội/TP.HCM) năm 2026?
5. Chính sách AI content (video sinh/gắn nhãn) trên TikTok Shop VN hiện hành có bắt buộc gắn nhãn cho video KOC quay tay dùng kịch bản AI không?
