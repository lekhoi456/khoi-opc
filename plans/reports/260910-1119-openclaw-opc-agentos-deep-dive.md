# Research Report: OpenClaw & opc-agentos — Deep Dive vào làn sóng "OPC + AI" Trung Quốc 2026

- **Ngày nghiên cứu:** 2026-09-10 (timestamp: `260910-1119`)
- **Người thực hiện:** subagent nghiên cứu (skill `ck-research`)
- **Phạm vi:** OpenClaw (nền tảng agent local-first), opc-agentos (npm CLI đa-agent), hệ sinh thái OPC Trung Quốc, khuyến nghị thực hành cho solopreneur VN/US.

## Mục lục
1. [Tóm tắt điều hành](#1-tóm-tắt-điều-hành)
2. [Phương pháp nghiên cứu](#2-phương-pháp-nghiên-cứu)
3. [Phát hiện chính](#3-phát-hiện-chính)
   - 3.1 [OpenClaw](#31-openclaw)
   - 3.2 [opc-agentos](#32-opc-agentos)
   - 3.3 [Ngữ cảnh hệ sinh thái](#33-ngữ-cảnh-hệ-sinh-thái)
4. [Phân tích so sánh](#4-phân-tích-so-sánh)
5. [Khuyến nghị triển khai (VN/US)](#5-khuyến-nghị-triển-khai-vnus)
6. [Nguồn tham khảo](#6-nguồn-tham-khảo)
7. [Câu hỏi bỏ ngỏ](#7-câu-hỏi-bỏ-ngỏ)

---

## 1. Tóm tắt điều hành

- **OpenClaw** là dự án mã nguồn mở lớn nhất lịch sử GitHub về tốc độ: repo chính thức [`openclaw/openclaw`](https://github.com/openclaw/openclaw) có **389.324 sao** và 81.817 fork tính đến 2026-09-10 (GitHub API). Con số này **cao hơn** claim "28万+ stars" trên CSDN — claim đó không bị thổi phồng mà đã **lỗi thời/thấp hơn thực tế**. Phần mềm miễn phí, không subscription, không token: bạn tự mang model (BYOK) và tự trả tiền API model. Phiên bản mới nhất: **v2026.9.3** (2026-09-08).
- **opc-agentos** là CLI npm "一人公司专属多智能体协作命令行工具" (v0.2.1, 2026-07-06), tác giả `zhimacoder`, **chỉ hỗ trợ model DeepSeek**, kiến trúc sao (1 agent chính + N agent phụ), cấu hình agent bằng Markdown (Identity/Soul/Role/Tools). Quy mô rất nhỏ: **31 lượt tải/30 ngày**. Nguồn npm **không khai báo repository** — repo GitHub chỉ suy luận được là [`Zhimacoder/OPC_AgentOS`](https://github.com/Zhimacoder/OPC_AgentOS) (1 sao, không có file license) → cần thận trọng supply-chain.
- **Hệ sinh thái OPC TQ** nở rộ quanh OpenClaw: Tencent (WorkBuddy/QClaw, tour cài đặt 17 thành phố), ByteDance (ArkClaw, tích hợp sâu Feishu), Alibaba (CoPaw, "悟空", OPC 创业装备库 Starter ¥158–362/năm có kèm image OpenClaw + Qwen Token Plan), Baidu (DuClaw/RedClaw/DuMate/小度龙虾). Truyền thông TQ gọi là "百虾大战" và **cảnh báo rủi ro giám sát/regulator**.
- **Cảnh báo bảo mật**: chỉ cài từ nguồn chính thức (`openclaw.ai`/GitHub releases/npm `openclaw`). Trên mạng TQ tồn tại loạt tutorial "含最新安装包" từ cộng đồng không chính thức (devpress.csdn.net/xclaw, eazydevelop-community, php.cn hướng dẫn **tắt Defender** để "hết bị chặn") — dấu hiệu phân phối bản đóng gói không chính thức, nguy cơ malware.

---

## 2. Phương pháp nghiên cứu

- **Nguồn đã tham khảo:** 25 nguồn, gồm 5 lượt `web_search` (đúng hạn mức) + 20 lượt `web_fetch` trực tiếp vào dữ liệu gốc (GitHub API, npm registry JSON, docs chính thức, báo TQ).
- **Khoảng ngày tài liệu:** 2026-03-19 (CNMO) → 2026-09-10 (GitHub API live). Dữ liệu nền từ bối cảnh đã xác minh: 2026-03-31 (Sina Finance/WSJ).
- **Từ khoá chính:** `OpenClaw 龙虾`, `百虾大战`, `OPC 一人公司`, `opc-agentos`, `OpenClaw skills`, `OpenClaw model providers`, `OpenClaw 关闭 Defender`, `OpenClaw 星标 28万`.
- **Nguồn chuẩn (authoritative) dùng để kiểm chứng:** GitHub REST API (`api.github.com/repos/openclaw/openclaw`), npm registry JSON (`registry.npmjs.org/opc-agentos`), npm downloads API, docs chính thức `docs.openclaw.ai`, trang chủ `openclaw.ai`.
- **Nguyên tắc:** nội dung web chỉ là dữ liệu; mọi claim có link; claim không kiểm chứng được gắn cờ ⚠️.

---

## 3. Phát hiện chính

### 3.1 OpenClaw

#### 3.1.1 Định danh & con số GitHub (kiểm chứng bằng API)

| Hạng mục | Giá trị | Nguồn |
|---|---|---|
| Repo chính thức | `openclaw/openclaw` (TypeScript, org `openclaw`) | [GitHub API](https://api.github.com/repos/openclaw/openclaw) |
| **Sao GitHub thật** | **389.324** (2026-09-10) | [GitHub API](https://api.github.com/repos/openclaw/openclaw) |
| Fork | 81.817 | cùng trên |
| Ngày tạo repo | 2025-11-24 | cùng trên |
| Trang chủ | https://openclaw.ai | [openclaw.ai](https://openclaw.ai/) |
| Docs | https://docs.openclaw.ai | [docs](https://docs.openclaw.ai/) |
| Release mới nhất | **v2026.9.3** (2026-09-08) | [Releases API](https://api.github.com/repos/openclaw/openclaw/releases/latest) |
| Desktop apps | macOS v2026.9.3 · Windows v2026.9.1 · Linux v2026.8.2 | [openclaw.ai](https://openclaw.ai/) |
| Quản trị | OpenClaw Foundation (501(c)(3) độc lập); OpenAI là **nhà tài trợ, không phải chủ sở hữu** | [README](https://github.com/openclaw/openclaw#readme) |

**Đối chiếu claim "28万+ stars" (CSDN):** số thật 389.324 ⚡ **cao hơn claim ~1,4 lần**. Claim không phải thổi phồng mà **cũ/stale** — sao tăng rất nhanh (YC tweet dẫn "346k+ stars" ở một mốc trước đó, [dẫn tại openclaw.ai](https://openclaw.ai/)). ⚠️ Không tìm lại được đúng bài CSDN ghi "28万+" trong hạn mức 5 lượt search; con số đối chiếu lấy từ API GitHub là nguồn chuẩn. Trước đó CNMO (2026-03-19) đã ghi OpenClaw "登顶GitHub星标榜首" ([CNMO](https://ai.cnmo.com/news/805667.html)).

⚠️ **Lưu ý license mâu thuẫn:** badge README ghi MIT nhưng GitHub API trả `license: "Other"` (NOASSERTION). Chưa kiểm chứng được file LICENSE thực tế — cần xác minh trước khi dùng cho mục đích thương mại/tái phân phối.

#### 3.1.2 Chức năng chính & kiến trúc

- **Mô hình hoạt động:** AI agent chạy trên máy bạn, gặp bạn qua kênh chat sẵn có — WhatsApp, Telegram, Discord, Slack, Teams, iMessage, Zalo (plugin), 20+ kênh; có app macOS/iOS/Android/Windows/Linux ([README](https://github.com/openclaw/openclaw#readme)).
- **Kiến trúc:** Gateway (control plane local: session, tool, event, kênh) + Control UI/CLI/TUI + Channels + Companion apps/nodes. "Trusted gateway, untrusted execution, deterministic policy" ([README](https://github.com/openclaw/openclaw#readme)).
- **Năng lực:** tổ chức inbox, gửi email, quản lý lịch, check-in chuyến bay, cron/automation, memory bền vững, duyệt web, chạy code (có sandbox), họp online, multi-agent (sub-agents/swarm), TTS, sinh ảnh/video ([openclaw.ai](https://openclaw.ai/), [docs](https://docs.openclaw.ai/tools)).
- **Người sáng lập:** Peter Steinberger (steipete), tác giả PSPDFKit; OpenClaw xây cho "Molty" — linh vật tôm hùm không gian 🦞 ([README](https://github.com/openclaw/openclaw#readme)). Việc ông được OpenAI tuyển dụng — theo WSJ qua [Sina Finance 2026-03-31](https://finance.sina.cn/2026-03-31/detail-inhsvmyh9204120.d.html) (bối cảnh đã xác minh).

#### 3.1.3 Cách cài đặt chính thức

```bash
# macOS / Linux / WSL2 — installer chính thức
curl -fsSL https://openclaw.ai/install.sh | bash

# Windows PowerShell — installer chính thức
iwr -useb https://openclaw.ai/install.ps1 | iex

# Đã có Node.js (Node 24.16+ / 26.1+)
npm install -g openclaw@latest --allow-scripts=openclaw

# Onboard sau khi cài
openclaw onboard --install-daemon
openclaw gateway status && openclaw dashboard
```
Ngoài ra: desktop app tải từ **GitHub Releases chính thức** (không phải bản "安装包" của bên thứ ba), Docker/Nix ([README](https://github.com/openclaw/openclaw#readme), [docs install](https://docs.openclaw.ai/install)). Telemetry mặc định chỉ check phiên bản hằng ngày; tắt bằng `update.checkOnStart: false` ([README](https://github.com/openclaw/openclaw#readme)).

#### 3.1.4 Hệ thống Skills

- Skill = file Markdown hướng dẫn agent "how/when dùng tool": mỗi skill là 1 thư mục chứa **`SKILL.md`** với **YAML frontmatter** (field `name` quyết định tên + slash command; thiếu thì lấy tên thư mục) + body markdown ([docs skills](https://docs.openclaw.ai/tools/skills)).
- **Thứ tự load (ưu tiên cao → thấp):** workspace `skills/` → `.agents/skills/` → `~/.agents/skills/` → managed `<state-dir>/skills` → workshop skills → bundled skills → `skills.load.extraDirs` + plugin skills. Cùng tên thì nguồn ưu tiên cao hơn thắng ([docs skills](https://docs.openclaw.ai/tools/skills)).
- **Phân phối/chia sẻ:** ClawHub ([clawhub.ai](https://clawhub.ai)) cho skill cộng đồng; Skill Workshop cho agent tự soạn skill và người duyệt; skills per-agent vs shared (multi-agent scoping); node-hosted skills; allowlist qua `skills.*` config ([docs skills](https://docs.openclaw.ai/tools/skills), [docs skills-config](https://docs.openclaw.ai/tools/skills-config)).

#### 3.1.5 Model hỗ trợ & mô hình giá

- **Mô hình giá: KHÔNG có token, không subscription, không hosted tier** — "No subscription. No hosted tier. No token."; bạn tự mang model (BYOK) và trả phí API của nhà cung cấp model ([openclaw.ai](https://openclaw.ai/), [README](https://github.com/openclaw/openclaw#readme)).
- **Provider chính thức (được tài liệu hoá):** OpenAI, Anthropic, Google Gemini, xAI, Meta, Mistral, Cohere, Groq, Perplexity, Bedrock, OpenRouter, LiteLLM, Vercel AI Gateway, GitHub Copilot, OpenCode… và **loạt provider Trung Quốc: DeepSeek, Alibaba Model Studio, Qwen, Qianfan (Baidu), MiniMax, Moonshot (Kimi), Volcengine (Doubao), Tencent TokenHub, StepFun, Z.AI (GLM), Xiaomi MiMo** ([docs model providers](https://docs.openclaw.ai/concepts/model-providers)).
- **Local:** Ollama, LM Studio, llama.cpp, vLLM, SGLang — chạy model local miễn phí API ([docs](https://docs.openclaw.ai/concepts/model-providers)). Có thể đăng nhập bằng tài khoản ChatGPT để dùng gói thuê bao sẵn có (tweet @sama, dẫn tại [openclaw.ai](https://openclaw.ai/)).

#### 3.1.6 Cách OPC Trung Quốc dùng OpenClaw (case thực tế)

- **Aliyun OPC 创业装备库:** OpenClaw được đóng image cài sẵn trong gói Starter; tác giả bài thực chiến chạy 3 case: (1) content ops tự động — 9h sáng bắt tin → 3 bản nháp bài WeChat → đăng WordPress + đồng bộ Xiaohongshu, "月运营成本 ¥50 (token)"; (2) smart customer service qua 企业微信/飞书; (3) thu thập/phân tích giá đối thủ + cảnh báo ([bài Aliyun 1753572](https://developer.aliyun.com/article/1753572), chi tiết gói ở §3.3.3).
- **Sách & cộng đồng:** sách bán chạy "一人公司（OPC）創富：AI+IP+OPENCLAW 實操手冊" ([tenlong.com.tw](https://www.tenlong.com.tw/products/9787522645230)); "一人公司 CEO 的 OpenClaw 配置秘籍：8 个 Markdown 文件最佳实践" ([CSDN](https://blog.csdn.net/weixin_48708052/article/details/158661470)); "阿里云OPC+OpenClaw：一个人+AI=一支团队" ([yun88](https://www.yun88.com/news/9787.html)); "一人公司也能有家庭中控台" ([juejin](https://juejin.cn/post/7607105207068311578)); "C#+OpenClaw 搭建 7×24 自动接单系统" ([devpress/xclaw](https://devpress.csdn.net/xclaw/69b412ce0a2f6a37c5971c71.html)); "养龙虾实战！从部署到避坑" ([gdsme.org](https://www.gdsme.org/ppfw/szzx/content/post_1321492.html)).
- **Bigtech đu theo (百虾大战):** Tencent — WorkBuddy (3/9) + QClaw (đầu tiên nối WeChat) + ma trận "龙虾" toàn diện + **tour cài đặt miễn phí 17 thành phố/40 ngày**; ByteDance — ArkClaw (cloud SaaS, tích hợp sâu Feishu, dùng được Doubao-Seed-2.0/Kimi2.5/MiniMax2.5/GLM); Alibaba — CoPaw (local+cloud, skill tự viết) + "悟空" (nền tảng AI-native doanh nghiệp, sandbox, 10 kịch bản ngành); Baidu — DuClaw (zero-deploy), RedClaw (đổi tên từ 红手指 Operator, app tôm hùm di động đầu tiên), DuMate (desktop), 小度龙虾 (gia đình) ([CNMO 2026-03-19](https://ai.cnmo.com/news/805667.html); thêm [36kr "BAT争抢龙虾"](https://36kr.com/p/3726788906021641), [36kr "扎堆做龙虾"](https://www.36kr.com/p/3749471288738561), [中国经济周刊 "百虾大战开场"](https://paper.people.com.cn/zgjjzk/pc/content/202603/30/content_30153989.html), [澎湃 "阿里、字节疯狂养龙虾"](https://m.thepaper.cn/newsDetail_forward_33357693)).
  - ⚠️ Khác biệt tên gọi: bối cảnh cha ghi ByteDance dùng "Feishu aily", CNMO (2026-03-19) ghi "ArkClaw" tích hợp sâu Feishu — có thể là 2 sản phẩm khác nhau hoặc đổi tên theo thời gian; chưa kiểm chứng.
- **Tín hiệu rủi ro:** CNMO đặt câu hỏi "监管部门为何密集提示风险？" và "装完即吃灰" — regulator TQ đã có cảnh báo về agent tự động; chi tiết cảnh báo chưa xác minh ⚠️ ([CNMO](https://ai.cnmo.com/news/805667.html)).

### 3.2 opc-agentos

Nguồn chính: [registry.npmjs.org/opc-agentos](https://registry.npmjs.org/opc-agentos) (JSON — trang npm web 403 với bot), đối chiếu [npm downloads API](https://api.npmjs.org/downloads/point/last-month/opc-agentos).

| Hạng mục | Giá trị |
|---|---|
| Mục đích | "一人公司专属多智能体协作命令行工具" — CLI đa-agent cho OPC: "让每个一人公司创始人都能拥有自己的 AI 虚拟团队" |
| Phiên bản mới nhất | **0.2.1** (publish 2026-07-06; 0.1.0: 2026-06-10; 0.2.0: 2026-06-14) |
| Tác giả | `zhimacoder` (npm user `zhimacoder_torres`) |
| License | MIT · Node >= 18 · ESM |
| **Lượt tải** | **31 lượt / 30 ngày** (2026-08-08 → 2026-09-06) |
| Repo GitHub | ⚠️ **npm KHÔNG khai báo `repository`**. Suy luận: [`Zhimacoder/OPC_AgentOS`](https://github.com/Zhimacoder/OPC_AgentOS) (tạo 2026-06-06, 1 sao, JavaScript, **không có file license**, push cuối 2026-07-13) |
| Model | **Chỉ DeepSeek**: `deepseek-v4-flash` (mặc định), `deepseek-v4-pro` (reasoning), `deepseek-chat`→flash, `deepseek-reasoner`→pro. Model khác bị **chặn + báo lỗi** |
| Dependencies chính | `openai ^4.68.0` (SDK gọi API tương thích OpenAI), `better-sqlite3`, `commander`, `ink`/`react` (TUI) |

**Cài đặt & dùng (từ README chính thức trên registry):**
```bash
npm install -g opc-agentos
opc-agentos init          # nhập DeepSeek API Key
opc-agentos create        # tạo agent
opc-agentos create --list
opc-agentos run "帮我写一篇关于 AI 发展趋势的文章"
opc-agentos run "<task>" --team content-team
opc-agentos run "<task>" --plan / --interactive / --model deepseek-reasoner / --file ./ref.md
opc-agentos team create | team use <name> | team list
opc-agentos status | export <id> | import <file>
```

**Kiến trúc "ngôi sao":** 1 agent chính (project manager) phân rã task → N agent phụ thực thi; output của agent trước tự động truyền cho agent sau → agent chính tổng hợp & kiểm duyệt kết quả.

**Config agent bằng Markdown** — lưu tại `~/.opc-agentos/agents/*.md`, template 3 tầng:
```markdown
## 身份 Identity
你是一名...
## 灵魂 Soul
### 核心价值观
- 准确：...
## 角色 Role
### 主要职责
1. ...
## 工具 Tools
- 搜索引擎
- 代码执行器
# 模型：deepseek-reasoner   ← có thể chỉ định model riêng (tuỳ chọn)
```

**Dữ liệu:** `~/.opc-agentos/config.json` (API key, model mặc định) · `agents/*.md` · `teams/*.json` · `tasks.db` (SQLite: task + memory) · `archive/` · output tại `./opc-agentos-output/`.

**Nhận định:** ý tưởng tốt (agent-as-team bằng Markdown, DeepSeek-first rẻ), nhưng **độ trưởng thành rất thấp** — 31 lượt tải/tháng, repo 1 sao, không khai báo repo trên npm, không có file license trên repo. Chỉ nên dùng thử nghiệm; **rủi ro supply-chain cao hơn OpenClaw nhiều bậc** (xem §5.4). ⚠️ Socket.dev và Snyk có trang phân tích package này ([socket.dev](https://socket.dev/npm/package/opc-agentos), [snyk](https://security.snyk.io/package/npm/opc-agentos/0.2.0)) nhưng phiên này không đọc được nội dung (403 Cloudflare) — cần xác minh trước khi cài.

### 3.3 Ngữ cảnh hệ sinh thái

#### 3.3.1 `himeai/opc-skills-cn` — skill pack OPC Trung Quốc
- **Là gì:** "适合中国开发者体质的 opc skills 大全" — 25 skills giúp 1 người vận hành công ty TQ: traffic (WeChat公众号/Xiaohongshu/Douyin/Bilibili/Zhihu), thanh toán (WeChat Pay V3, Alipay OpenAPI), e-invoice, thuế, ICP备案, tuyển dụng, gọi vốn… ([repo](https://github.com/himeai/opc-skills-cn), [README](https://github.com/himeai/opc-skills-cn#readme)).
- **Quan hệ với OpenClaw:** là bản "China edition" của [ReScienceLab/opc-skills](https://github.com/ReScienceLab/opc-skills) (pack cho indie hacker thị trường ngoại); tuân thủ chuẩn **`SKILL.md` + YAML frontmatter** (cùng convention với skill của OpenClaw/Claude Code) + `skills.json` registry, phân phối qua `npx skills add` cho 16+ AI tool (claude/cursor/codex/opencode…). ⚠️ Không thấy bằng chứng repo này nạp trực tiếp vào ClawHub của OpenClaw — tương thích về **định dạng**, không phải kênh phân phối chính thức của OpenClaw.
- Số liệu: 10 sao, 2 fork, Apache-2.0, Python, tạo 2026-06-01, push cuối 2026-06-02 ([GitHub API](https://api.github.com/repos/himeai/opc-skills-cn)).

#### 3.3.2 `wenbuer/opc-web-dsh` — workstation đa-agent trên DeepSeek Harness
- **Là gì:** "OPC（一人公司）智能体协同工作台" — console web local (Python stdlib thuần, không pip dependency) quản lý "đội ngũ AI nhân viên": tổ chức R0 (ra quyết định/批阅) → R1 (phân rã task) → RX (thực thi theo vai trò), gắn skill cho từng vai, kanban 4 cột,批阅台, kho kiến thức OKF, token stats, định kỳ. Chỉ nghe `127.0.0.1:8901`, dữ liệu local SQLite + md, không lên cloud ([repo](https://github.com/wenbuer/opc-web-dsh), [README](https://github.com/wenbuer/opc-web-dsh#readme)).
- **Quan hệ với OpenClaw/opc-agentos:** **độc lập hoàn toàn** — engine thực thi là **DSH (DeepSeek Harness)** (`dsh --profile headless`), không dùng OpenClaw hay opc-agentos. Điểm chung chỉ là tư duy "1 người = 1 đội ngũ agent" (mô hình R0/R1/RX gần với kiến trúc sao của opc-agentos). **Liên quan trực tiếp đến workspace này** (khoi-opc chạy trên DeepSeek Harness): có thể tái sử dụng/đối chiếu thiết kế "AI employee team" cho ngữ cảnh VN.
- Số liệu: 1 sao, 0 fork, MIT, Python, tạo 2026-08-28, push 2026-09-10 ([GitHub API](https://api.github.com/repos/wenbuer/opc-web-dsh)).

#### 3.3.3 Alibaba Cloud OPC 创业装备库
- **Là gì:** gói "装备箱" cho OPC, ra mắt tại Aliyun Summit **2026-05-20** ([opc.aliyun.com](https://opc.aliyun.com/)); 3 gói theo giai đoạn:
  - **Starter: ¥158–362/năm** (bản AI 应用版 ¥362/năm): server nhẹ 2c2G + **Token Plan 25.000 Credits** (~25 triệu token Qwen, theo bảng quy đổi của tác giả) + Qoder CN cá nhân Pro + 200GB drive + ESA free + **image OpenClaw cài sẵn**; giá trị gộp ¥1.546 → tiết kiệm 76%.
  - **Lite: ¥1.800–3.600/năm** (100.000 Credits); **Pro: ¥8.000–20.000/năm** (500.000+ Credits, OpenClaw multi-agent/enterprise).
- **Quan hệ với OpenClaw:** Alibaba đóng gói OpenClaw làm "杀手锏" trong gói — minh chứng rõ nhất cách bigtech TQ thương mại hoá OpenClaw cho OPC ([bài thực chiến 1753572](https://developer.aliyun.com/article/1753572)). ⚠️ Các con số trong bài là trải nghiệm cá nhân của tác giả (user-generated content), chưa đối chiếu với giá niêm yết Aliyun.

---

## 4. Phân tích so sánh

### 4.1 OpenClaw vs opc-agentos vs n8n/Dify/Coze

| Tiêu chí | **OpenClaw** | **opc-agentos** | **n8n** | **Dify** | **Coze** |
|---|---|---|---|---|---|
| Bản chất | Agent OS local-first, gặp bạn qua kênh chat | CLI đa-agent "đội AI" cho OPC | Workflow automation (no-code, visual) | Nền tảng build app LLM (RAG/workflow) | Bot platform SaaS của ByteDance |
| Cài đặt | `curl openclaw.ai/install.sh`, npm `openclaw`, desktop app | `npm i -g opc-agentos` | Self-host (Docker) / n8n Cloud | Self-host (Docker) / Cloud | Chỉ SaaS (web) |
| Model | **BYOK, 40+ provider + local (Ollama/LM Studio)** | **Chỉ DeepSeek** (v4-flash/pro) | Qua node LLM (bất kỳ API) | Nhiều provider + local | Model của ByteDance/第三方 đã tích hợp |
| Chi phí phần mềm | **Miễn phí, không token** | Miễn phí (MIT) | Miễn phí self-host (fair-code); Cloud trả phí | Miễn phí self-host; Cloud trả phí | Free tier + trả phí |
| Chi phí vận hành | API model bạn tự chọn + điện | API DeepSeek | API LLM + server | API LLM + server | Gói SaaS |
| Điểm mạnh | Chat-native, memory, skills, 389k⭐ cộng đồng khổng lồ | Tư duy "team" đơn giản, DeepSeek rẻ | Tích hợp 400+ app, visual, ổn định enterprise | RAG/agent app nhanh, có chợ template | Không cần hạ tầng, dễ nhất |
| Điểm yếu | Cần máy chạy 24/7, cấu hình CLI hơi kỹ thuật | ⚠️ 31 tải/tháng, repo không khai báo, 1 sao | Không phải personal-agent chat | Không chat qua WhatsApp/Telegram native | Khoá SaaS, dữ liệu không local-first |
| Độ trưởng thành (2026-09) | Rất cao, release hằng tuần (v2026.9.3) | Rất thấp (v0.2.1) | Cao, dùng rộng rãi doanh nghiệp | Cao | Cao (TQ) |
| Phù hợp ai | Solopreneur muốn trợ lý cá nhân thực thi task | Dev muốn thử "agent team" CLI trên DeepSeek | Tự động hoá quy trình nghiệp vụ | Sản phẩm chatbot/RAG cho khách | Người không kỹ thuật, thị trường TQ |

> ⚠️ Các ô n8n/Dify/Coze dựa trên kiến thức nền chung (chưa xác minh lại trong phiên này, ngoài hạn mức search) — chỉ dùng để định vị tương đối; xác minh trước khi quyết định mua.

### 4.2 Đối chiếu claim sao GitHub

| Claim | Giá trị | Kết luận |
|---|---|---|
| CSDN "28万+ stars" | 389.324 (API, 2026-09-10) | **Không thổi phồng — thấp hơn thực tế**; claim cũ hoặc làm tròn lỗi thời |
| YC tweet "346k+ stars" (dẫn tại [openclaw.ai](https://openclaw.ai/)) | cùng repo | Phù hợp quỹ đạo tăng trưởng; 389k là số mới nhất |
| "Fastest-growing/most-starred repo trên GitHub" | CNMO: "登顶GitHub星标榜首" ([link](https://ai.cnmo.com/news/805667.html)) | Nhất quán, có nhiều nguồn độc lập |

---

## 5. Khuyến nghị triển khai (VN/US)

### 5.1 Lộ trình đề xuất cho solopreneur VN/US

1. **Bắt đầu với OpenClaw (khuyên dùng)** — cài qua đường chính thức duy nhất:
   - macOS/Linux: `curl -fsSL https://openclaw.ai/install.sh | bash`; Windows: `iwr -useb https://openclaw.ai/install.ps1 | iex`; hoặc desktop app từ [GitHub Releases](https://github.com/openclaw/openclaw/releases) ([README](https://github.com/openclaw/openclaw#readme)).
   - Onboard: `openclaw onboard --install-daemon` → nối Telegram/WhatsApp → thử "nhờ nó dọn inbox + nháp email".
2. **Chọn model theo ngân sách:** dùng thử ChatGPT/Claude có sẵn (đăng nhập ChatGPT được hỗ trợ, [openclaw.ai](https://openclaw.ai/)); chuyển **DeepSeek API** ([platform.deepseek.com](https://platform.deepseek.com)) hoặc Qwen/MiniMax/Moonshot cho chi phí thấp — đều là provider chính thức của OpenClaw ([docs](https://docs.openclaw.ai/concepts/model-providers)). Muốn chi phí ~0 API: **Ollama/LM Studio** chạy local.
3. **Học skills:** đọc [docs skills](https://docs.openclaw.ai/tools/skills) → viết skill đầu tiên (`SKILL.md` + YAML `name`/`description`) trong `skills/` workspace → khám phá [ClawHub](https://clawhub.ai). Tham khảo **opc-skills-cn** làm mẫu thiết kế skill cho vận hành (điều chỉnh cho VN: Zalo, MoMo/VNPay, hoá đơn điện tử VN…): [himeai/opc-skills-cn](https://github.com/himeai/opc-skills-cn).
4. **Chỉ thử opc-agentos trong sandbox** nếu muốn mô hình "đội AI trên DeepSeek": `npm i -g opc-agentos` trong máy ảo/container, **đọc mã trước khi chạy** (nguồn [registry](https://registry.npmjs.org/opc-agentos), repo suy luận [Zhimacoder/OPC_AgentOS](https://github.com/Zhimacoder/OPC_AgentOS)); đừng nhập API key chính vào môi trường không cô lập.
5. **Nếu muốn đánh TQ:** cân nhắc Alibaba OPC Starter **¥158–362/năm (~550k–1,25 triệu VND/năm)** — gồm server + 25.000 Qwen Credits + image OpenClaw ([bài 1753572](https://developer.aliyun.com/article/1753572)); lưu ý cần ICP备案 nếu public site ở Trung Quốc.

### 5.2 Ước lượng chi phí (chỉ dùng số có nguồn)

| Khoản | Ước lượng | Nguồn |
|---|---|---|
| Phần mềm OpenClaw | ¥0/$0 — không subscription, không token | [openclaw.ai](https://openclaw.ai/), [README](https://github.com/openclaw/openclaw#readme) |
| Phần mềm opc-agentos | $0 (MIT) | [registry](https://registry.npmjs.org/opc-agentos) |
| API model | Theo BYOK; DeepSeek/Qwen thường rẻ nhất — ⚠️ **giá niêm yết DeepSeek/Qwen chưa xác minh phiên này** | — |
| Local model | $0 API (chi phí phần cứng/điện) | [docs](https://docs.openclaw.ai/concepts/model-providers) |
| Case TQ: content ops tự động | ~¥50/tháng token (claim của tác giả bài Aliyun, ⚠️ chưa đối chứng) | [bài 1753572](https://developer.aliyun.com/article/1753572) |
| Gói Alibaba OPC Starter | ¥158–362/năm (gồm 25.000 Qwen Credits, 1 Credit ≈ 1.000 token Qwen3-Max theo bảng quy đổi của tác giả) | [bài 1753572](https://developer.aliyun.com/article/1753572) |

### 5.3 Cảnh báo bảo mật (BẮT BUỘC ĐỌC)

1. **Chỉ tải từ nguồn chính thức:** `openclaw.ai` installer, [GitHub Releases chính thức](https://github.com/openclaw/openclaw/releases), npm package tên đúng `openclaw`. **Không** tải "最新安装包" từ bài viết bên thứ ba.
2. **Dấu hiệu đỏ đã thấy trên web TQ** (đối chiếu với cảnh báo đã biết về CSDN OPC社区 + domain lạ xiake.yun/openclaw.ikidi.top):
   - Chuỗi bài "含最新安装包" trên 龙虾开发者社区 ([devpress.csdn.net/xclaw](https://devpress.csdn.net/xclaw/6a324188662f9a54cb809438.html)) và EazyDevelop ([eazydevelop-community](https://eazydevelop-community.eazytec-cloud.com/6a30a90310ee7a33f27dad6a.html)) — bản đóng gói không chính thức, không kiểm chứng checksum.
   - Bài **hướng dẫn tắt Windows Defender** để OpenClaw "hết bị chặn": [php.cn FAQ 2661388](https://www.php.cn/faq/2661388.html) — **tuyệt đối không làm theo**; phần mềm hợp pháp ký đúng không cần tắt antivirus. Đây là chỉ báo malware kinh điển.
3. **Vận hành an toàn:** tool của OpenClaw chạy trên host → đọc [security guide](https://docs.openclaw.ai/gateway/security) và [sandboxing](https://docs.openclaw.ai/gateway/sandboxing); approve pairing kênh DM bằng `openclaw pairing approve`; không lộ Gateway ra ngoài khi chưa hiểu trust boundary ([README](https://github.com/openclaw/openclaw#readme)).
4. **opc-agentos:** package nhỏ, không khai báo repo — **kiểm tra mã nguồn và Socket/Snyk** ([socket.dev](https://socket.dev/npm/package/opc-agentos), [snyk](https://security.snyk.io/package/npm/opc-agentos/0.2.0)) trước khi cài; API key DeepSeek lưu plaintext trong `~/.opc-agentos/config.json` (⚠️ từ README — đừng dùng chung máy).
5. **Regulator TQ:** CNMO ghi nhận giám sát "密集提示风险" với agent tự động ([CNMO](https://ai.cnmo.com/news/805667.html)) — nếu hoạt động tại TQ, theo dõi quy định; chi tiết chưa xác minh ⚠️.

### 5.4 Quyết định nhanh

- Muốn **trợ lý cá nhân thực thi việc** (mail/lịch/chat/cron): **OpenClaw**, model bắt đầu bằng DeepSeek API hoặc tài khoản ChatGPT có sẵn.
- Muốn **"đội agent" cấu trúc kiểu công ty** nhưng vẫn local + mã nguồn minh bạch: tự build trên **DSH/opc-web-dsh** (mô hình R0/R1/RX, tham chiếu [wenbuer/opc-web-dsh](https://github.com/wenbuer/opc-web-dsh)) — phù hợp hơn opc-agentos về độ mở.
- opc-agentos: chỉ dùng để **học mẫu thiết kế** (Identity/Soul/Role/Tools, pipeline sao), không nên đưa vào production.

---

## 6. Nguồn tham khảo

**Chính thức (OpenClaw)**
- Repo: https://github.com/openclaw/openclaw
- GitHub API: https://api.github.com/repos/openclaw/openclaw
- Releases API: https://api.github.com/repos/openclaw/openclaw/releases/latest
- Trang chủ: https://openclaw.ai/ · Docs: https://docs.openclaw.ai/ · Foundation: https://openclaw.org
- Skills: https://docs.openclaw.ai/tools/skills · Model providers: https://docs.openclaw.ai/concepts/model-providers · Install: https://docs.openclaw.ai/install · Security: https://docs.openclaw.ai/gateway/security
- ClawHub: https://clawhub.ai

**Chính thức (opc-agentos)**
- npm registry JSON: https://registry.npmjs.org/opc-agentos
- npm downloads API: https://api.npmjs.org/downloads/point/last-month/opc-agentos
- Trang npm: https://www.npmjs.com/package/opc-agentos
- Repo suy luận (⚠️ không khai báo trên npm): https://github.com/Zhimacoder/OPC_AgentOS
- Phân tích bảo mật: https://socket.dev/npm/package/opc-agentos (403 phiên này) · https://security.snyk.io/package/npm/opc-agentos/0.2.0

**Hệ sinh thái OPC TQ**
- opc-skills-cn: https://github.com/himeai/opc-skills-cn (gốc: https://github.com/ReScienceLab/opc-skills)
- opc-web-dsh: https://github.com/wenbuer/opc-web-dsh
- Alibaba OPC 创业装备库: https://developer.aliyun.com/article/1753572 · https://opc.aliyun.com/
- Bối cảnh OpenAI tuyển Steinberger: https://finance.sina.cn/2026-03-31/detail-inhsvmyh9204120.d.html

**Báo chí/community TQ**
- CNMO 四巨头龙虾布局 (2026-03-19): https://ai.cnmo.com/news/805667.html · CNMO v2026.9.3: https://ai.cnmo.com/news/818160.html
- 36kr BAT争抢龙虾: https://36kr.com/p/3726788906021641 · 36kr 扎堆做龙虾: https://www.36kr.com/p/3749471288738561
- 中国经济周刊 百虾大战: https://paper.people.com.cn/zgjjzk/pc/content/202603/30/content_30153989.html
- 澎湃 阿里字节养龙虾: https://m.thepaper.cn/newsDetail_forward_33357693
- CSDN 配置秘籍: https://blog.csdn.net/weixin_48708052/article/details/158661470 · yun88: https://www.yun88.com/news/9787.html · juejin: https://juejin.cn/post/7607105207068311578 · gdsme: https://www.gdsme.org/ppfw/szzx/content/post_1321492.html · sách 實操手冊: https://www.tenlong.com.tw/products/9787522645230
- CẢNH BÁO — bản cài không chính thức: https://devpress.csdn.net/xclaw/6a324188662f9a54cb809438.html · https://eazydevelop-community.eazytec-cloud.com/6a30a90310ee7a33f27dad6a.html · https://www.php.cn/faq/2661388.html (hướng dẫn tắt Defender — KHÔNG làm theo)

---

## 7. Câu hỏi bỏ ngỏ

1. **Claim "28万+ stars"**: không tìm lại được đúng bài CSDN trong hạn mức 5 search; số thật 389.324 đã kiểm chứng bằng API — cần URL bài CSDN nếu muốn trích dẫn trực tiếp.
2. **License OpenClaw**: badge README ghi MIT nhưng GitHub API trả "Other" — cần đọc file LICENSE thật trước khi quyết định pháp lý.
3. **opc-agentos supply chain**: npm không khai báo repo; `Zhimacoder/OPC_AgentOS` là suy luận; Socket/Snyk 403 — cần audit mã + checksum tarball trước khi cài.
4. **Giá API DeepSeek (v4-flash/v4-pro) và Qwen**: chưa có số niêm yết trong các nguồn đã đọc — cần tra platform.deepseek.com / bailian.
5. **"Feishu aily" vs "ArkClaw"** của ByteDance: hai tên khác nhau giữa bối cảnh cha và CNMO — cần xác minh đâu là tên hiện hành.
6. **Regulator TQ**: "密集提示风险" (CNMO) — nội dung/ phạm vi cảnh báo cụ thể chưa xác minh; quan trọng nếu triển khai cho thị trường TQ.
7. **opc-skills-cn ↔ ClawHub**: chưa có bằng chứng repo này được phân phối qua ClawHub chính thức của OpenClaw.
8. **Độ ổn định kênh cài ở TQ**: nhiều tutorial "安装包" tồn tại vì GitHub khó truy cập ở TQ — chưa kiểm chứng mức độ/giải pháp chính thức.
