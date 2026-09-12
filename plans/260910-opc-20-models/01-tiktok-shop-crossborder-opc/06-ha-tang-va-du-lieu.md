# 06. Hạ tầng & Dữ liệu cho TikTok Shop xuyên biên giới full-AI (OPC) — Cài đặt tận tay

> Thuộc kế hoạch 01 · Model phụ trách: DeepSeek · Ngày: 2026-09-10 · Trạng thái: draft
> Đọc kèm: `01-tiktok-shop-crossborder-opc.md` (kế hoạch gốc) và `07-phap-ly-thue.md` (pháp lý).
> Ký hiệu: ✅ đã xác minh nguồn · ⚠️ số tự khai/chưa xác minh — phải kiểm tra lại trước khi chi tiền.

## 0. Nguyên tắc & sơ đồ tổng thể

- **Nguyên tắc 1 (từ master playbook):** "1 bảng tính + 1 chat + vài bot là đủ chạy doanh nghiệp 1 người" — không dựng microservices, không K8s.
- **Nguyên tắc 2:** thứ gì có API thì nối n8n; thứ gì không có API (batch upload, đăng video) thì **người duyệt + AI soạn sẵn + bấm 1 nút**; OpenClaw chỉ thêm ở giai đoạn 2.
- **Nguyên tắc 3:** founder chỉ nhận quyết định qua **Telegram**, không đăng nhập 10 hệ thống mỗi ngày.
- **Nguyên tắc 4:** mọi key/secret để trong **n8n Credentials** (mã hoá) và vault riêng, không dán vào file trên VPS trần.

```mermaid
flowchart LR
    TTS["TikTok Shop VN<br/>(Seller Center + API/CSV)"] -->|đơn, hoàn| N8N["n8n (VPS Docker)<br/>+ Cloudflare Tunnel"]
    N8N <--> AT[("Airtable — DB trung tâm<br/>SKU · Đơn · Hoàn · Khách · Video · Chi phí")]
    DS["DeepSeek API"] --> N8N
    CZ["Coze bot CSKH"] <-->|webhook/API| N8N
    ZALO["Zalo OA"] <-->|webhook| N8N
    TG["Telegram (founder)"] <--alert/duyệt--> N8N
    N8N -->|6h sáng| RP["Báo cáo KPI"] --> TG
    KL["Kling + CapCut"] -.video nháp.-> AT
    F["🧑💼 Founder"] -.duyệt SKU/video/giá.-> AT
```

## 1. 10 tài khoản cần mở (từ seller đến thanh toán)

> Thứ tự mở khớp lộ trình ngày 1–7 của kế hoạch 01. Tổng phí mở tài khoản ≈ **0 đồng** (chỉ VPS + domain mất tiền).

| # | Tài khoản | URL đăng ký | Giấy tờ cần | Phí | Thời gian | Mở ngày |
|---|---|---|---|---|---|---|
| 1 | **TikTok Shop Seller Center VN** | https://seller-vn.tiktok.com | CCCD hoặc Giấy CNĐK hộ kinh doanh; TK ngân hàng chính chủ; SĐT + email | 0đ | 1–3 ngày xét duyệt | Ngày 1 |
| 2 | **Tài khoản TikTok creator** (đăng video organic, gắn shop) | https://www.tiktok.com/signup | SĐT/email; nối với shop qua Seller Center → "TikTok Account Binding" | 0đ | Ngay lập tức | Ngày 1 |
| 3 | **Zalo OA** (kênh chat CSKH + bot) | https://oa.zalo.me | CCCD hoặc GPKD hộ kinh doanh; SĐT; mô tả ngành nghề | 0đ (tạo OA miễn phí; gói gửi tin tính phí theo lượt ⚠️) | 1–2 ngày duyệt | Ngày 2 |
| 4 | **Airtable** (DB trung tâm) | https://airtable.com/signup | Email + Google | Free (2.500 records/base, 100 automation/month) | Ngay | Ngày 2 |
| 5 | **DeepSeek Platform** (API) | https://platform.deepseek.com/sign_up | Email + SĐT; nạp tiền bằng thẻ Visa/Mastercard quốc tế | Pay-as-you-go (xem mục 5) | Ngay | Ngày 3 |
| 6 | **Coze quốc tế** (bot CSKH) | https://www.coze.com | Email/Google | Free (giới hạn token/tháng ⚠️ kiểm tra trang pricing) | Ngay | Ngày 3 |
| 7 | **Telegram + BotFather** (kênh cảnh báo/duyệt cho founder) | https://t.me/BotFather | SĐT; tạo bot lấy token; lấy `chat_id` của bạn qua @userinfobot | 0đ | 5 phút | Ngày 3 |
| 8 | **Cloudflare** (domain + tunnel HTTPS cho webhook) | https://dash.cloudflare.com/sign-up | Email; mua domain `.com` ~$10/năm tại Cloudflare Registrar | ~$10/năm ⚠️ | Ngay (DNS vài giờ) | Ngày 3 |
| 9 | **VPS** (chạy n8n) — DigitalOcean/Vultr/Hetzner | https://www.digitalocean.com hoặc https://www.vultr.com | Thẻ Visa; chọn Ubuntu 24.04, 2GB RAM, 50GB SSD | $6–12/tháng | 5–10 phút khởi tạo | Ngày 4 |
| 10 | **TK ngân hàng VN riêng cho shop** (thanh toán từ sàn về; sàn yêu cầu chính chủ) | Chi nhánh ngân hàng gần nhà | CCCD + Giấy CNĐK hộ kinh doanh; đăng ký luôn **Internet Banking + SMS** | 0đ | 1–2 ngày | Ngày 2 |

**Ghi chú:**
- Tài khoản thứ 11 (không tính vào 10): tài khoản **dịch vụ order 1688** — thường dùng web + thanh toán VND qua ngân hàng VN, không cần tài khoản quốc tế; so sánh 2 đơn vị (phí 1–5% + ship, theo kế hoạch 01) ⚠️.
- Giai đoạn 2 (US): thêm **Mercury** (https://mercury.com — cần LLC + EIN) và **Wise** (nhận/trả USD) — chi tiết ở `07-phap-ly-thue.md` mục 5.
- Với mọi tài khoản: bật **2FA**, dùng email riêng của shop, mật khẩu lưu trong vault.

## 2. Cài n8n trên VPS — từng lệnh Docker thật

### 2.1. Chuẩn bị VPS (Ubuntu 24.04, chạy SSH với user `root`)

```bash
# Cập nhật hệ thống + cài Docker chính thức (repo docker.com)
apt update && apt upgrade -y
curl -fsSL https://get.docker.com | sh
systemctl enable --now docker

# Tạo thư mục dự án + khóa mã hóa n8n (lưu khóa này ra vault!)
mkdir -p /opt/n8n && cd /opt/n8n
openssl rand -hex 24 > .encryption_key    # N8N_ENCRYPTION_KEY
cat .encryption_key
```

### 2.2. File `docker-compose.yml` (n8n + Postgres + Caddy + Watchtower)

```yaml
# /opt/n8n/docker-compose.yml
services:
  postgres:
    image: postgres:16-alpine
    restart: unless-stopped
    environment:
      POSTGRES_USER: n8n
      POSTGRES_PASSWORD: ${DB_PASSWORD}        # đặt trong .env
      POSTGRES_DB: n8n
    volumes: [ "pgdata:/var/lib/postgresql/data" ]
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U n8n"]
      interval: 10s
      timeout: 5s
      retries: 5

  n8n:
    image: docker.n8n.io/n8nio/n8n
    restart: unless-stopped
    ports: [ "127.0.0.1:5678:5678" ]           # chỉ nghe localhost, Caddy phơi HTTPS
    environment:
      DB_TYPE: postgresdb
      DB_POSTGRESDB_HOST: postgres
      DB_POSTGRESDB_DATABASE: n8n
      DB_POSTGRESDB_USER: n8n
      DB_POSTGRESDB_PASSWORD: ${DB_PASSWORD}
      N8N_HOST: ${N8N_HOST}                    # ví dụ n8n.shopcuatoi.com
      N8N_PROTOCOL: https
      N8N_PORT: 5678
      WEBHOOK_URL: https://${N8N_HOST}/
      N8N_EDITOR_BASE_URL: https://${N8N_HOST}/
      GENERIC_TIMEZONE: Asia/Ho_Chi_Minh
      TZ: Asia/Ho_Chi_Minh
      N8N_ENCRYPTION_KEY: ${ENCRYPTION_KEY}
      N8N_DIAGNOSTICS_ENABLED: "false"
      N8N_SECURE_COOKIE: "true"
      EXECUTIONS_DATA_PRUNE: "true"
      EXECUTIONS_DATA_MAX_AGE: 168              # giữ log 7 ngày cho gọn
      EXECUTIONS_DATA_PRUNE_MAX_COUNT: 10000
    volumes: [ "n8n_data:/home/node/.n8n" ]
    depends_on:
      postgres:
        condition: service_healthy

  caddy:
    image: caddy:2-alpine
    restart: unless-stopped
    ports: [ "80:80", "443:443" ]
    environment:
      DOMAIN: ${N8N_HOST}
    volumes:
      - ./Caddyfile:/etc/caddy/Caddyfile
      - caddy_data:/data
      - caddy_config:/config

  watchtower:
    image: containrrr/watchtower
    restart: unless-stopped
    command: --interval 86400 --cleanup n8n    # tự cập nhật image n8n mỗi ngày
    volumes: [ "/var/run/docker.sock:/var/run/docker.sock" ]

volumes: { n8n_data: , pgdata: , caddy_data: , caddy_config: }
```

File `Caddyfile` (TLS tự động từ Let's Encrypt qua Cloudflare DNS):

```
{$DOMAIN} {
    reverse_proxy n8n:5678
}
```

### 2.3. Khởi động & tạo tài khoản chủ

```bash
cat > .env <<EOF
DB_PASSWORD=$(openssl rand -hex 16)
ENCRYPTION_KEY=$(cat .encryption_key)
N8N_HOST=n8n.shopcuatoi.com
EOF
docker compose up -d
docker compose logs -f n8n          # chờ dòng "Editor is now accessible"
# Mở https://n8n.shopcuatoi.com → tạo owner: email + mật khẩu mạnh
```

Kiểm tra sức khỏe (dùng cho UptimeRobot ở mục 8): `curl -f https://n8n.shopcuatoi.com/healthz` → trả về `{"status":"ok"}`.

### 2.4. Mở webhook ra ngoài & bảo mật

- Đã có domain + Caddy thì webhook mặc định chạy được (`WEBHOOK_URL` ở trên). Nếu VPS sau NAT/không mở port, dùng **Cloudflare Tunnel**: cài `cloudflared`, chạy `cloudflared tunnel login` → `cloudflared tunnel create n8n` → route `cloudflared tunnel route dns n8n n8n.shopcuatoi.com` → chạy dưới systemd.
- **Tắt port 5678 public**: trong compose đã bind `127.0.0.1:5678` — chỉ Caddy nói chuyện với n8n.
- Bật thêm: firewall UFW chỉ mở 22/80/443; fail2ban cho SSH; n8n User Management: tạo user riêng cho từng vai trò (founder = owner).
- **Credentials cần tạo trong n8n** (Credentials → New): Airtable (Personal Access Token), HTTP Request cho DeepSeek (Header `Authorization: Bearer <key>`), Telegram (bot token), Zalo OA (Access Token OA + App ID/Secret Key), Google Drive (OAuth2) để lưu CSV/backup.

### 2.5. Kết nối TikTok Shop

- Đường chính hãng: **TikTok Shop Open Platform** — đăng ký app tại Partner Center (https://partner.tiktokshop.com ⚠️ kiểm tra URL hiện hành cho seller VN) → lấy App Key/App Secret → webhook Order Create/Update/Refund. **Mất 1–3 tuần duyệt app** ⚠️.
- Đường tắt cho 30 ngày đầu (không cần duyệt): Seller Center → Orders → **Export CSV** → n8n đọc CSV qua Google Drive/watch folder → ghi Airtable. Đơn vẫn vào DB đầy đủ, chỉ chậm hơn vài phút.

## 3. Sáu workflow n8n (nút thật, trigger, đầu ra)

> Đặt tên theo "vị trí công việc AI" của kế hoạch 01. Mỗi workflow có Error Trigger phụ: bắt lỗi → Telegram cho founder.

### WF1 — `01-don-moi-vao-airtable` (AI法务财务)
- **Trigger:** Webhook "TikTok Shop Order Create" (hoặc Google Drive Trigger trên file CSV export).
- **Chuỗi nút:** Webhook/GoogleDrive → **Code** (map: order_id, sku, qty, price, buyer_name, phone, address, status) → **Airtable** (tạo dòng bảng `Đơn`, upsert theo `Order ID` để không trùng) → **Airtable** (tạo/tìm dòng bảng `Khách`) → **Telegram** gửi: `🛒 Đơn mới #... | SP: ... | 250.000đ | KH: T.***`.
- **Output:** đơn nằm sẵn trong DB, founder biết ngay khi có đơn.

### WF2 — `02-listing-draft-batch-dang` (AI上架师)
- **Trigger:** n8n Form/Webhook "duyệt listing" — founder bấm nút từ Telegram (n8n hỗ trợ "n8n Chat"? không — thay bằng Telegram nút/URL webhook test).
- **Chuỗi:** Webhook (SKU id + `approved=true`) → **Airtable** (lọc SKU trạng thái `Chờ duyệt`) → **Code** (đóng gói payload tiêu đề 80 ký tự, mô tả 3 đoạn, 5–9 ảnh, giá = Giá nhập ×3, category ID, weight) → **HTTP Request** POST tới TikTok Shop API `/api/products` (hoặc tạo file theo template bulk-upload → **Google Drive** → founder import 1 nút trong Seller Center) → **Airtable** (cập nhật trạng thái `Đã đăng` + link sản phẩm) → **Telegram** báo danh sách đã đăng.
- **Quy tắc:** API chỉ nhận sản phẩm founder đã tick `Duyệt IP` (cột ở bảng SKU); thiếu ảnh thật → chặn.

### WF3 — `03-video-lich-dang` (AI编导)
- **Trigger:** Schedule Trigger mỗi 15 phút.
- **Chuỗi:** **Airtable** (lọc bảng `Video`: `Trạng thái = Duyệt` AND `Lịch đăng <= now`) → **If** (có video đến giờ) → **Telegram** nhắc founder: `📹 Đến giờ đăng: <tên> — file: <link Drive> — caption: <đã soạn sẵn>` (kèm nút mở file) → chờ founder đăng tay → founder nhắn lại `done <video_id>` qua Telegram Trigger → **Airtable** (trạng thái `Đã đăng`, lưu link video).
- **Giai đoạn 2:** nếu được cấp quyền Content Posting API của TikTok (đối tác, cần duyệt ⚠️) → thay bước nhắc tay bằng HTTP Request đăng tự động.

### WF4 — `04-cskh-coze-zalo` (AI客服)
- **Trigger:** Zalo OA Webhook (cấu hình trong OA: Settings → Webhook → URL `https://n8n.../webhook/zalo`; verify token).
- **Chuỗi:** Webhook → **Code** (lấy user_id + nội dung tin) → **HTTP Request** tới Coze API `POST https://api.coze.com/v3/chat` (header `Authorization: Bearer <PAT>`, body: `bot_id`, `user_id=zalo_<id>`, `stream=true`, `auto_save_history=true`) → **Code** (ráp câu trả lời, gắn cờ nếu bot trả `[HUMAN]`) → **If** (`[HUMAN]` → **Telegram** cho founder kèm ngữ cảnh; ngược lại → **Zalo OA Send Message**) → **Airtable** (lưu log hội thoại: user, thời gian, chủ đề phân loại).
- **Quy tắc theo kế hoạch 01:** bot chỉ tự xử lý ship/đổi trả/bảo hành; khách đòi bồi thường >100k → luôn chuyển người.

### WF5 — `05-bao-cao-sang-6h` (AI法务财务)
- **Trigger:** Schedule Trigger `0 6 * * *` (Cron, Asia/Ho_Chi_Minh).
- **Chuỗi:** **Airtable** (đơn hôm qua + hoàn hôm qua + video có CTR) → **Code** (tổng hợp số: GMV, đơn, hoàn, tỷ lệ hoàn, CTR trung bình, top 3 SKU) → **HTTP Request** DeepSeek (`deepseek-chat`, prompt: "viết báo cáo sáng 10 dòng tiếng Việt + 3 việc founder cần duyệt hôm nay") → **Telegram** gửi bản tin.
- **Output mẫu:** `☀️ 10/09: GMV 2.4tr (8 đơn) · hoàn 1 (12%) · CTR top 4,2% · Cần duyệt: 3 listing + 2 video`.

### WF6 — `06-canh-bao-hoan` (AI法务财务)
- **Trigger:** Schedule Trigger mỗi 30 phút.
- **Chuỗi:** **Airtable** (lọc đơn `Yêu cầu hoàn` chưa xử lý) → **If** (giá trị >100k HOẶC tỷ lệ hoàn hôm nay >5%) → **Telegram** cảnh báo đỏ kèm link đơn + video mở hàng (nếu có) → **Airtable** tạo task trong bảng `Hoàn` trạng thái `Chờ founder`.
- **Kèm chính sách:** mọi đơn hoàn phải có ảnh/video bằng chứng đóng gói (bài học 光年易达 — mục 8 kế hoạch 01).

## 4. Coze quốc tế: bot CSKH — cài từng màn hình

1. **Màn đăng ký:** https://www.coze.com → Sign up bằng Google → tạo Workspace `OPC-Shop`.
2. **Màn tạo bot:** Create Bot → tên `AI客服-ShopX` → chọn model (DeepSeek nếu có trong danh sách, không thì GPT/Coze default — kiểm tra mục "Model" của bot ⚠️).
3. **Màn Persona & Prompt** — dán prompt dưới đây vào ô "Persona and Prompt":
   ```
   Bạn là nhân viên chăm sóc khách hàng 24/7 của shop [Tên shop] trên TikTok Shop VN.
   - Chỉ trả lời tiếng Việt, thân thiện, ngắn gọn ≤80 từ/lượt.
   - Việc được tự xử lý: phí ship, thời gian giao (3–5 ngày), đổi trả trong 7 ngày khi lỗi do shop,
     bảo hành 30 ngày, cách dùng sản phẩm (dùng kiến thức trong Knowledge).
   - KHÔNG hứa: hoàn tiền >100.000đ, bồi thường, ngày giao chính xác, hàng có sẵn 100%.
   - Khi khách đòi bồi thường >100.000đ, tức giận, đe doạ, hoặc hỏi pháp lý →
     trả lời đúng chuỗi: "[HUMAN]" (không thêm gì khác).
   - Không bịa chính sách. Không có trong Knowledge thì nói "Em kiểm tra lại với bộ phận chuyên môn nhé".
   - Không yêu cầu/tiết lộ dữ liệu cá nhân nhạy cảm ngoài SĐT & địa chỉ giao hàng (tuân thủ NĐ 13/2023/NĐ-CP).
   ```
4. **Màn Knowledge:** tab Knowledge → Create Knowledge → upload 3 file (PDF/Markdown): `SOP-chinh-sach-shop.md` (ship, đổi trả, bảo hành, giờ CSKH), `FAQ-20-cau.md`, `thong-tin-san-pham.md` (tên, chất liệu, kích thước, cách dùng từng SKU) → chờ indexing → bật "Knowledge" trong bot → test: hỏi "đổi hàng mất phí không?" phải trích đúng SOP.
5. **Màn Workflow (nâng cao):** Build Workflow kéo-thả: `Start (input: câu hỏi) → LLM (phân loại: ship/đổi trả/spam/bồi thường) → Condition (nhánh bồi thường → Output "[HUMAN]") → Knowledge Search → LLM (soạn câu trả lời theo SOP) → End`. Gắn workflow vào bot thay cho chat thuần khi muốn kiểm soát chặt.
6. **Màn kênh:** Publish → Channels:
   - **Web Chat / Telegram / WhatsApp (nếu có)** — mở trực tiếp được.
   - **Zalo: Coze quốc tế KHÔNG có channel Zalo chính thức** ⚠️ → dùng cầu n8n (WF4, mục 3): Zalo OA Webhook → gọi Coze API `POST https://api.coze.com/v3/chat` bằng **Personal Access Token** (Coze → Account → API Token). Đây là thay đổi so với baseline (xem cuối file).
7. **Màn kiểm thử:** Preview panel thử 20 câu FAQ + 3 câu "bẫy" (đòi bồi thường, chửi bời, hỏi hàng giả) → chỉnh prompt/knowledge.
8. **Màn vận hành:** Logs theo dõi lượt chat; hằng tuần founder đọc 10 hội thoại thất bại → cập nhật Knowledge (vòng lặp dữ liệu của kế hoạch 01).

## 5. DeepSeek API — đăng ký, nạp, curl, ước lượng token

1. **Đăng ký:** https://platform.deepseek.com/sign_up (email + SĐT xác thực).
2. **Nạp tiền:** Settings → Billing → Top up bằng thẻ Visa/Mastercard quốc tế; mức tối thiểu ⚠️ (xem trang nạp hiện hành). Nạp thử $10 cho tháng 1.
3. **Tạo key:** API Keys → Create → copy `sk-...` → lưu vào n8n Credential (HTTP Header Auth) + vault.
4. **Gọi mẫu (curl thật):**
   ```bash
   curl https://api.deepseek.com/chat/completions \
     -H "Content-Type: application/json" \
     -H "Authorization: Bearer sk-THAT-THAT-CUA-BAN" \
     -d '{
       "model": "deepseek-chat",
       "messages": [
         {"role": "system", "content": "Bạn là AI上架师 viết listing TikTok Shop VN."},
         {"role": "user", "content": "Viết tiêu đề 80 ký tự + mô tả 3 đoạn cho hộp đựng gia vị xoay 360 độ."}
       ],
       "temperature": 0.7,
       "response_format": {"type": "json_object"}
     }'
   ```
   Trả về JSON: `choices[0].message.content` + `usage.prompt_tokens/completion_tokens`.
5. **Giá tham chiếu:** deepseek-chat ≈ **$0,27/1M token input (cache miss) · $1,10/1M output**; deepseek-reasoner cao hơn — ⚠️ số tham khảo, đối chiếu bảng giá https://api-docs.deepseek.com/quick_start/pricing hiện hành. Có thể đi qua **OpenRouter** để đổi model khi cần (theo stack của kế hoạch 01).
6. **Ước lượng token cho 100 đơn/tháng** ⚠️ (tự tính, có buffer):

| Việc | Lượt/tháng | Token/lượt | Tổng token |
|---|---|---|---|
| CSKH qua bot (trung bình 6 lượt/đơn) | 600 lượt | 800 | 480.000 |
| Sinh 20 listing mới (tiêu đề + mô tả + dịch) | 20 | 3.000 | 60.000 |
| Kịch bản video + caption | 30 | 2.000 | 60.000 |
| Báo cáo sáng + phân loại hội thoại | 60 | 1.500 | 90.000 |
| Retry, prompt dài, test | buffer ×2 | — | 700.000 |
| **Tổng** | | | **≈ 1,4M token ≈ $1–2/tháng (~30–50k VND)** |

   → Chi phí DeepSeek không phải rào cản; chi phí thật nằm ở Kling credits, CapCut Pro và ads.
7. **Best practice:** bật cache hệ thống prompt (giảm giá input tới 10×), dùng `response_format=json_object` cho listing, stream cho CSKH, đặt temperature 0,3 cho việc "đối soát/trích xuất" và 0,8 cho việc "viết content".

## 6. Airtable schema CHI TIẾT (6 bảng — từng cột)

> Base: `OPC-TTS`. Quy ước: khách hàng chỉ lưu dữ liệu tối thiểu (NĐ13 — xem 07 mục 3); SĐT/địa chỉ để riêng trường ẩn quyền.

### 6.1. Bảng `SKU` (chọn hàng → đăng bán)

| Cột | Kiểu | Ví dụ | Công thức |
|---|---|---|---|
| SKU ID | Formula (primary) | `SKU-001` | `"SKU-" & RIGHT("000"&AUTO,3)` ⚠️ hoặc tự đánh |
| Tên sản phẩm | Single line | Hộp đựng gia vị xoay 360° | — |
| Link 1688 | URL | https://detail.1688.com/... | — |
| Giá nhập (VND) | Currency | 85.000 | — |
| Giá bán đề xuất | Currency | 255.000 | `Giá nhập × 3` |
| Biên gộp ước | Percent | 33% | `(Giá bán − Giá nhập − Giá bán×16%) / Giá bán` |
| Cân nặng (kg) | Number | 0,35 | — |
| Ngách | Single select | Bếp thông minh mini | — |
| Trạng thái | Single select | Nghiên cứu / Chờ duyệt / Duyệt IP / Đã đăng / Ngừng | — |
| Check IP (người duyệt) | Checkbox | ✅ | — |
| Ảnh (đã xử lý nền sạch) | Attachment | 9 file | — |
| Link TikTok | URL | https://vt.tiktok.com/... | — |
| Ngày đăng | Date | 15/09/2026 | — |
| Doanh số luỹ kế | Rollup (từ Đơn) | 1.200.000 | `SUM(values)` |

### 6.2. Bảng `Đơn`

| Cột | Kiểu | Ví dụ | Công thức |
|---|---|---|---|
| Order ID | Single line (primary) | `5772...9301` | — |
| Ngày đặt | Date | 10/09/2026 | — |
| SKU | Link to SKU | SKU-003 | — |
| Khách | Link to Khách | KH-012 | — |
| Số lượng | Number | 1 | — |
| Giá bán | Currency | 255.000 | — |
| Phí sàn + phụ phí | Currency | 40.800 | `Giá bán × 16%` |
| Doanh thu thuần | Currency | 214.200 | `Giá bán − Phí sàn` |
| Trạng thái | Single select | Mới / Đóng gói / Đã gửi / Đã giao / Yêu cầu hoàn / Hoàn | — |
| Video mở hàng | Attachment | file đóng gói + dán mã vận đơn | — |
| Mã vận đơn | Single line | VN123456789 | — |
| Ngày giao dự kiến | Date | 14/09/2026 | — |
| Ghi chú | Long text | khách nhắn Zalo hỏi ship | — |

### 6.3. Bảng `Hoàn`

| Cột | Kiểu | Ví dụ | Công thức |
|---|---|---|---|
| Refund ID | Autonumber (primary) | 17 | — |
| Đơn | Link to Đơn | 5772...9301 | — |
| Ngày yêu cầu | Date | 12/09/2026 | — |
| Lý do | Single select | Lỗi sản phẩm / Không đúng mô tả / Đổi ý / Gian lận nghi ngờ | — |
| Giá trị | Currency | 255.000 | — |
| Bằng chứng (video/ảnh) | Attachment | video mở hàng của shop | — |
| Trạng thái | Single select | Chờ xử lý / Đồng ý hoàn / Từ chối / Đã chuyển người | — |
| Quyết định | Long text | hoàn 50%, giữ hàng | — |
| Ngày xử lý | Date | 13/09/2026 | — |
| Kết quả cuối | Single select | Hoàn tiền / Đổi hàng / Khách huỷ | — |

### 6.4. Bảng `Khách` (tuân thủ NĐ13)

| Cột | Kiểu | Ví dụ | Ghi chú |
|---|---|---|---|
| Khach ID | Formula (primary) | `KH-012` | `"KH-" & RIGHT("000"&AUTO,3)` |
| Tên (rút gọn) | Single line | T. Linh | ⚠️ không lưu họ tên đầy đủ nếu không cần |
| SĐT | Phone | 09xx... | ẩn với user không phải founder |
| Địa chỉ giao | Long text | Q.7, TP.HCM | chỉ lưu khi cần giao |
| Số đơn | Rollup (từ Đơn) | 3 | `COUNTALL` |
| Tổng chi tiêu | Rollup (từ Đơn) | 640.000 | `SUM` |
| Đánh giá rủi ro | Single select | Thường / Theo dõi / Blacklist | khách từng hoàn gian lận → Blacklist |
| Ngày xoá dữ liệu | Date | 10/09/2027 | tự động xoá sau 12 tháng hết khiếu nại |

### 6.5. Bảng `Video`

| Cột | Kiểu | Ví dụ | Công thức |
|---|---|---|---|
| Video ID | Autonumber (primary) | 42 | — |
| SKU | Link to SKU | SKU-003 | — |
| Loại | Single select | AI sinh / Quay tay / Ghép | — |
| Kịch bản | Long text | Hook 2s → mở hộp → demo → CTA | — |
| Prompt Kling | Long text | (xem mục 7) | — |
| File video | Attachment | .mp4 | — |
| Caption TikTok | Long text | đã viết sẵn kèm hashtag | — |
| Trạng thái | Single select | Nháp / Chờ duyệt / Duyệt / Đã đăng / Gỡ | — |
| Lịch đăng | Date time | 17/09/2026 19:30 | — |
| Link đã đăng | URL | https://vt.tiktok.com/... | — |
| Views | Number | 12.400 | — |
| CTR | Percent | 4,2% | — |
| Đơn quy về video | Rollup | 2 | đơn khách mua từ video này |
| Ghi chú | Long text | video này đang chạy ads | — |

### 6.6. Bảng `Chi phí`

| Cột | Kiểu | Ví dụ | Công thức |
|---|---|---|---|
| Chi phí ID | Autonumber | 105 | — |
| Ngày | Date | 08/09/2026 | — |
| Loại | Single select | Hàng nhập / Phí order / Vận chuyển TQ–VN / Kho-đóng gói / Ads / Affiliate / Tools / Thuế / Khác | — |
| Số tiền | Currency | 4.250.000 | — |
| Đơn liên quan | Link to Đơn | (trống) | — |
| Nhà cung cấp | Single line | DV order A | — |
| Hoá đơn/chứng từ | Attachment | PDF | — |
| Ghi chú | Long text | lô 1: 50 hộp gia vị | — |

**Views (không phải bảng mới):** `Cần duyệt` (SKU + Video trạng thái chờ), `Đơn hôm nay`, `Hoàn tồn`, `Lợi nhuận tháng` (grid + summary). Automation trong Airtable: khi Đơn trạng thái `Hoàn` → tự tạo dòng bảng Hoàn.

## 7. Kling + CapCut: quy trình sinh video (prompt nối tiếp)

**Chuỗi đầy đủ cho 1 SKU (ví dụ "hộp đựng gia vị xoay 360°"):**

1. **Kịch bản (DeepSeek)** — prompt:
   ```
   Viết 3 kịch bản video TikTok Shop VN 15–30 giây cho "hộp đựng gia vị xoay 360°",
   khách nữ 20–30 tuổi, bối cảnh bếp nhỏ. Mỗi kịch bản: hook 2s (đau đúng nỗi bếp lộn xộn),
   demo góc máy cận, CTA "mua ở giỏ vàng". Kèm 1 câu caption ≤100 ký tự + 5 hashtag.
   ```
2. **Prompt Kling (text-to-video / image-to-video)** — sinh 3–5 clip 5s cho mỗi cảnh:
   ```
   Vertical 9:16, realistic kitchen counter, warm morning light, a young woman's hand
   rotates a 360° spice rack organizer with 12 clear bottles, spices visible,
   slow smooth camera push-in, shallow depth of field, no text, no watermark,
   photorealistic, 5 seconds
   ```
   Mẹo: ảnh sản phẩm đã xử lý nền (Airtable cột Ảnh) → Image-to-Video giữ đúng mẫu thật; mỗi cảnh sinh 2–3 lần, chọn 1. ⚠️ Kling quốc tế (https://app.klingai.com) tính theo credit/giây video — kiểm tra gói hiện hành; tắt "AI watermark" nếu có tuỳ chọn, và **gắn nhãn nội dung AI** theo policy TikTok Shop VN hiện hành (policy thay đổi nhanh — câu hỏi mở của kế hoạch 01).
3. **Dựng trong CapCut Pro (https://www.capcut.com):** import 3 clip → timeline theo kịch bản (hook 2s → demo 10s → CTA 3s) → TTS giọng nữ VN (CapCut Text-to-Speech) đọc lời kịch bản → phụ đề tự động (sửa lỗi) → nhạc từ **thư viện CapCut** (nhạc trending TikTok có thể bị claim — chỉ dùng nhạc có license thương mại của CapCut) → hiệu ứng chuyển cảnh → xuất **1080×1920, 30fps, <100MB**.
4. **Nộp về Airtable** bảng `Video` trạng thái `Chờ duyệt` kèm caption → founder duyệt (tối 3 buổi/tuần) → WF3 lên lịch đăng.
5. **Ngưỡng chất lượng tối thiểu:** 5 video AI + 5 video quay tay trong 30 ngày đầu (lộ trình kế hoạch 01); video có ảnh tay thật luôn ưu tiên chạy ads.

## 8. Backup & monitoring

### 8.1. Backup (3 lớp)

| Lớp | Cách làm | Tần suất |
|---|---|---|
| n8n (workflow + credentials) | cron: `docker exec n8n n8n export:workflow --all --output=/backup/wf.json` + tar volume `/home/node/.n8n` → mã hoá (age/gpg) → tải lên Google Drive qua rclone; giữ 30 bản | hằng ngày 3h sáng |
| Postgres | `docker exec postgres pg_dump -U n8n n8n \| gzip > /backup/n8n-db.sql.gz` | hằng ngày |
| Airtable | workflow n8n "backup": đọc 6 bảng qua API → ghi CSV vào Google Drive (Airtable Free không có snapshot lịch sử dài) | hằng tuần |
| Video/ảnh sản phẩm | đã nằm ở Drive/điện thoại — bật Google Photos/Drive sync | liên tục |

Diễn tập khôi phục 1 lần/tháng: dựng lại trên VPS test, import workflow, kiểm tra 1 webhook chạy.

### 8.2. Monitoring

- **UptimeRobot** (https://uptimerobot.com, free): monitor `https://n8n.shopcuatoi.com/healthz` mỗi 5 phút + port 443; cảnh báo Telegram/email khi down.
- **Workflow nội bộ `00-healthcheck`** (Schedule mỗi giờ): gọi `/healthz` → kiểm tra số dư DeepSeek API (`GET /user/balance`, cảnh báo khi < $2 → nhắc nạp) → ping webhook Zalo (gửi tin test cho chính mình) → nếu bất kỳ bước lỗi → Telegram đỏ.
- **Telegram alert (kênh `OPC-alerts`):** danh sách cảnh báo chuẩn — đơn mới / yêu cầu hoàn >100k / lỗi workflow (Error Trigger) / credit thấp / VPS down / video đến giờ đăng / báo cáo sáng.
- **Log:** n8n Execution log (đã prune 7 ngày) + `docker logs`; cấu hình alert khi workflow fail liên tiếp 3 lần.

## 9. Chi phí hạ tầng: tháng 1 vs tháng 6

> ⚠️ Giá tự khai/khảo sát nhanh 09/2026 — đối chiếu bảng giá chính thức trước khi thanh toán.

| Hạng mục | Tháng 1 | Tháng 6 (đã scale VN) | Ghi chú |
|---|---|---|---|
| VPS 2GB (n8n + Caddy) | $6 ≈ 156k | $12 ≈ 312k | nâng RAM khi thêm workflow |
| Domain .com | ~260k/năm (≈22k/tháng) | như cũ | Cloudflare Registrar |
| Airtable | 0đ | 0–620k ($24/team) nếu vượt giới hạn Free | chỉ nâng khi >2.500 record/base |
| DeepSeek API | ~50–100k | ~150–300k | theo mục 5, có buffer |
| Coze quốc tế | 0đ | 0đ (hoặc gói trả phí khi vượt quota ⚠️) | theo dõi usage |
| Kling credits | ~260–520k ($10–20) | ~1,3tr ($50) | 15–30 video/tháng |
| CapCut Pro | ~199–499k ⚠️ | ~499k | kiểm tra giá VN hiện hành |
| Zalo OA | 0đ | 0–500k (gói gửi tin khi CSKH nhiều ⚠️) | gói trả phí tuỳ lượt |
| Telegram + Cloudflare + UptimeRobot | 0đ | 0đ | free tier |
| **Tổng/tháng** | **≈ 700k – 1,4tr VND** | **≈ 2,5 – 4tr VND** | khớp mức "phí cố định ~3tr" của kế hoạch 01 |

## 10. Checklist cài đặt 14 ngày (dán lên tường)

- [ ] Ngày 1–2: mở 10 tài khoản mục 1 theo đúng thứ tự; lưu mọi mật khẩu vào vault.
- [ ] Ngày 3–4: VPS + domain + Cloudflare; `docker compose up -d`; đăng nhập n8n lần đầu.
- [ ] Ngày 4–5: tạo credentials (Airtable, DeepSeek, Telegram, Zalo OA, Drive); gửi tin Telegram test.
- [ ] Ngày 5–6: dựng 6 bảng Airtable theo mục 6 + views; nhập 10 SKU nghiên cứu đầu.
- [ ] Ngày 6–8: cài WF1 + WF5 + WF6 (đơn, báo cáo, hoàn) — chạy thử bằng CSV giả.
- [ ] Ngày 8–10: dựng bot Coze (mục 4) + WF4 cầu Zalo; test 20 câu FAQ.
- [ ] Ngày 10–12: chạy thử pipeline listing (DeepSeek → Airtable → WF2 duyệt → file batch).
- [ ] Ngày 12–14: Kling+CapCut ra 2 video mẫu → bảng Video → WF3 lịch đăng; cài backup + UptimeRobot.
- [ ] Mốc: một đơn giả chạy end-to-end từ CSV → Airtable → Telegram trong <5 phút.

## 11. Thay đổi so với baseline & câu hỏi mở

**Thay đổi so với kế hoạch 01 (baseline):**
1. **Coze → Zalo:** baseline ngầm định Coze nối thẳng Zalo OA; thực tế Coze quốc tế không có channel Zalo → phải cầu qua n8n webhook (mục 4.6) ⚠️.
2. **TikTok Shop API:** đường API chính thức cần duyệt app partner (1–3 tuần ⚠️) → 30 ngày đầu chạy bằng CSV export, không chờ.
3. **Chi phí DeepSeek:** baseline ghi 300–500k/tháng; ước lượng thực tế cho 100 đơn chỉ ~50–100k — phần dư ngân sách chuyển sang Kling/ads.

**Câu hỏi mở:** (1) TikTok Shop VN Open Platform hiện cấp webhook Order cho seller cá nhân/hộ KD chưa hay chỉ đối tác? (2) Giá Kling quốc tế 2026 theo credit bao nhiêu VND/video 5s? (3) Zalo OA có sắp có channel chính thức trên Coze quốc tế? (4) Policy gắn nhãn AI cho video sinh bằng Kling trên TikTok Shop VN hiện hành?

## 12. Nguồn tham khảo

- [Cổng DVC quốc gia — Đăng ký thành lập hộ kinh doanh (thủ tục 102614)](https://thutuc.dichvucong.gov.vn/p/home/dvc-tthc-thu-tuc-hanh-chinh-chi-tiet.html?ma_thu_tuc=102614) — truy cập 10/09/2026 (trang bận 503 lúc tra cứu, thử lại).
- [Báo Chính phủ — Hướng dẫn đăng ký hộ kinh doanh trực tuyến toàn trình (03/12/2025)](https://thanglong.baochinhphu.vn/huong-dan-nguoi-dan-lam-thu-tuc-dang-ky-thanh-lap-ho-kinh-doanh-ngay-tai-nha-103251224041608715.htm) — truy cập 10/09/2026.
- [n8n docs — Self-hosting Docker](https://docs.n8n.io/hosting/installation/docker/) · [n8n — n8n Form](https://docs.n8n.io/hosting/securing/set-up-login/) · [Coze docs (quốc tế)](https://www.coze.com/docs/guides) · [Coze API v3 chat](https://www.coze.com/open/docs) — truy cập 10/09/2026.
- [DeepSeek API docs — Pricing](https://api-docs.deepseek.com/quick_start/pricing) · [DeepSeek Platform](https://platform.deepseek.com) — truy cập 10/09/2026.
- [TikTok Shop Seller Center VN](https://seller-vn.tiktok.com) · [TikTok Shop Partner/Open Platform](https://partner.tiktokshop.com) ⚠️ — truy cập 10/09/2026.
- [Airtable — Pricing & API](https://airtable.com/pricing) · [Zalo OA](https://oa.zalo.me) · [Kling AI](https://app.klingai.com) · [CapCut](https://www.capcut.com) · [UptimeRobot](https://uptimerobot.com) — truy cập 10/09/2026.
