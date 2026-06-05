# MEMORY.md — George 的長期記憶

## AstroScript 🌙（商業化想法）

**建立的skill：**
- GitHub: https://github.com/arbiger/astroscript
- 基於 Swiss Ephemeris 的本地星盤計算工具
- 特點：本地運行、NASA 精度、支援 200+ 城市、OpenClaw skill 整合

**商業模式 v2.0（2026-04-05）：西方占卜平台**

產品定位：**鉤子 → 深度價值 → 持續黏著**

| 階段 | 產品 | 功能 | 目的 |
|------|------|------|------|
| 鉤子 | 每日/每週小運勢 | 幸運色、數字、星座洞察 | 免費接觸、引發興趣 |
| 深度價值 | 完整星盤報告 | 雙語行星、相位、宮位、深度解析 | 建立信任、展現專業 |
| Premium | 高級功能 | Minor Aspects、Dignities、Arabic Parts、Multiple House Systems | 變現 |
| 新產品 | 塔羅牌 | 每日一抽、牌陣展開 | 增加互動、擴大客群 |

**流量變現路徑：**
Landing Page（收集 Email）→ 每週運勢 Email（鉤子）→ 完整報告（第一次轉化）→ Premium 訂閱（變現）

**商業化進展（2026-04-04）：**
- Funnel Marketing 布局：Landing page + Google Sheets + email 自動化
- Landing page (`~/.openclaw/workspace/astroscript-landing/`)：HTML 表單收集 birth data
- Google Apps Script 後端：表單提交存進 Google Sheet
- Megan 負責：定時檢查新 row → AstroScript 計算 → email 回覆結果

**新增 Premium 功能（2026-04-04）：**
- ✅ Minor Aspects（五分相、補十二分相等 8 種）
- ✅ Dignities System（入廟、旺、失勢、陷）
- ✅ Arabic Parts（Part of Fortune、Spirit、Eros 等 5 個）
- ✅ Multiple House Systems（Placidus、Whole Sign、Equal、Koch、Porphyrius）
- 功能分層：Free（基本功能）vs Premium（付費功能）
- GitHub 已更新：commit 8cbe9f1

**測試案例：**
- Ching（1981/02/25 09:30 台中）→ 已寄出 HTML 報告
- 鄧小妹（2026/05/27 12:00 台中）→ 已寄出 HTML 報告給 George

**HTML 報告結構（2026-04-05 更新）：**
- ✅ 雙語行星名稱（☉ Sun 太陽、☽ Moon 月亮...）
- ✅ 雙語相位名稱（△ 三分相、✺ 六分相...）
- ✅ 唐湘琪風格總評語（300字，模仿口吻）
- ✅ 深度分析區段（重要相位、挑戰建議）
- ✅ 完整 12 宮顯示
- ✅ 詳細分析含：整體結構、重要相位解析、挑戰建議、事業方向

**GitHub 已更新（2026-04-04）：**
- commit `57cc1a2`：中英文雙語 README
- Premium 功能已完整文件化

**Landing page 已雙語化：**
- `~/.openclaw/workspace/astroscript-landing/index.html`
- 中文/English 切換按鈕
- GitHub README 也已更新為中英文雙語


**每週小運勢功能（2026-04-07 完成）:**
- ✅ `scripts/weekly_fortune.py` — 每週運勢產生器，使用 Swiss Ephemeris
- ✅ `members.csv` — 會員資料格式（name, email, birthdate）
- ✅ 每週一 09:00 cron job 已設定
- ✅ email 寄送：改用 gog（OAuth，不需要 SMTP 密碼）
- ⚠️ 目前用 CSV，日後需升級為 Google Sheet

功能：產生 12 星座每週運勢，含幸運色/數字、行星動態、主要相位、行動建議。

**待建構（2026-04-05 更新）：**
- George 申請網站 + 空間
- 設定 Google Sheet + Apps Script（George 需做一次）
- 將 SCRIPT_URL 填入 landing page
- 設定每小時 cron 檢查新 row
- 每週小運勢功能（cron job + email）- ✅ [2026-04-08]
- 塔羅牌模組 - 🆕

---

## Ruten Cookie Backup Skill（2026-03-31）

**建立的 skill：** `~/.openclaw/workspace/skills/ruten-cookie-backup/`

**功能：**
- 備份露天（Ruten）登入 cookies 到 JSON 檔案
- 從 JSON 檔案還原 session

**腳本：**
- `backup.sh` - 從瀏覽器提取 cookies 並保存
- `restore.sh` - 從 JSON 檔案還原 cookies

**備份檔案：** `~/.openclaw/workspace/ruten_cookies.json`

**Cron Job：** 每 20 天自動還原一次（Ruten Cookie Restore, ID: 29ada6ac-fdbc-469d-8bce-82d2acb4f640）

**觸發關鍵字：**
- 「備份露天 cookies」
- 「還原露天 cookies」
- 「Ruten session 過期了」

---

## Pending Issues / 需要追蹤

> 心跳 check-in 時會自動帶出這些項目
> 結案後用 `[closed]` 標記，不要刪除

- [open] **AstroScript 商業化方向** — ✅ v2.0 已確認：西方占卜平台（星盤 + 每週運勢 + 塔羅牌），待建構每週運勢 + 塔羅模組
- [open] **SOUL.md / IDENTITY.md / HEARTBEAT.md 架構整合** — 2026-04-01 討論中
- [open] **CAD 圖檔 Skill 開發**（🆕, priority: low, 2026-04-18）— cad-compositor skill 已刪除（不符合需求）。公司內部使用版本重新開發中，需求：收到廠商原圖 → 套入仲陽企業標準圖框 → 輸出 PDF
- [open] **Multi-Agent 實作驗證** — 2026-04-15：Per-agent sandbox + broadcast groups 文件已找到，待實際測試binding 路由和 per-agent tool 限制

---

## 2026-04-08 重要更新

### Agent 自我進化（2026-04-21 更新）
- capability-evolve 每兩天 09:00 自動跑
- Cycle #0031 (2026-04-21)：confidence 0.75 → 1.0，系統進化成功 ✅

### Cron Jobs 重構
- checkin jobs：改為11個，每88分鐘（5:48-23:24），跳過9-11點
- `capability-evolve` 和 `hourly-backup` 改用 `omlx` model（防止 timeout）
- `AstroScript` 和 `CCI Q1` cron jobs 已停用/刪除
- `fx-tracker` 從 cron job 改為直接 Python script

### Google Drive 整理
- Megan Drive：NuGROWS Markdown (`1XAw8nIRKQDq0LIDDix29Kz67ZXfkTDWQ`) 和 OpenClaw Backup (`1axrmStIpyFSAee1eiNe3TvY2l3ONt2JQ`) 已分享給 george@ (writer)
- Backup folder ID: `1oNWT8WkayHi0tx-NXQVl0vHawtEBYAsV`
- 所有備份統一用 megan@ Google Drive
- george@ OAuth 已不需要

### OMLX 模型更新
- 主力本地模型：`gemma-4-31b-it-4bit`（不再是 Huihui-Qwen3.5-35B）
- Qwen3.5-35B VLM 已不在清單
- 實際已載入（22.8GB / 50.4GB）：gemma-4-31b（18GB）、Qwen3-TTS（2.36GB）、Qwen3-ASR（2.41GB）
- 存在但未載入：Qwen3.5-9B、bge-m3（可用時機觸發自動載入）

### 共享知識庫共識（2026-04-08）
- **TOOLS.md** = 所有 session 共享的知識庫（事實、設定、技術值）
- **MEMORY.md** = 主要 session 長期記憶
- **memory/YYYY-MM-DD.md** = 每日日誌

---

## 2026-04-15 OpenClaw CLI Skill 更新

### openclaw-cli skill command-map.md 已同步
- 更新至 OpenClaw 2026.4.14 版本
- 新增命令：`backup *`, `capability *`, `exec-policy *`, `infer *`, `mcp *`, `proxy *`, `qa *`, `secrets *`, `tasks *`
- 修正：`agents *` 和 `sessions *` 都有 subcommands（之前漏標 *）

### Multi-Agent 新發現（2026-04-15）

**1. Binding 路由優先順序：**
1. Exact peer match（peer.kind + peer.id）
2. Parent peer match（執行緒繼承）
3. Guild + roles match（Discord 特定角色）
4. Guild match（Discord 特定伺服器）
5. Team match（Slack 特定 team）
6. Account match（特定帳號）
7. Channel match（該頻道任何帳號）
8. Default agent

**2. Per-Agent Sandbox + Tool 權限：**
每個 Agent 可以有不同的 sandbox 和工具權限：
```json
{
  "agents": {
    "list": [
      { "id": "main", "sandbox": { "mode": "off" } },
      { "id": "family", "sandbox": { "mode": "all", "scope": "agent" },
               "tools": { "allow": ["read"], "deny": ["exec", "write"] }}
    ]
  }
}
```

**3. Broadcast Groups（新功能）：**
可以讓多個 Agent 同時回應同一個 peer：
```json
{
  "broadcast": {
    "strategy": "parallel",
    "#channel": ["agent1", "agent2"]
  }
}
```

**4. Swarm：不存在** - 搜尋整個 docs 沒有找到 `swarm` 作為 multi-agent 相關命令

---

## Harness Engineering（AI 工程第三次革命）

**來源：** YouTube 影片「最近爆火的 Harness Engineering 到底是个啥？一期讲透！」（code秘密花园，2026-04-02）
**鏈接：** https://youtu.be/3DlXq9nsQOE
**影片描述提到 OpenClaw：** https://my.feishu.cn/wiki/QzGAwOH4LiZOYXktGyhcHoLUnRe

### 三代演化

| 階段 | 時間 | 核心 | 比喻 |
|------|------|------|------|
| Prompt Engineering | 2022-2024 | 優化單次提問 | 寫一封完美的 email |
| Context Engineering | 2025 | 動態上下文管理 | 為 email 加上所有附件 |
| Harness Engineering | 2026 | 建構環境系統 | 架構整個辦公室 |

### 核心公式

**Agent = Model + Harness**

**核心命題（OpenAI + Anthropic 驗證）：**
> *"Agents aren't hard; the Harness is hard."*

### 三大支柱

1. **Guides（feedforward）** — 預防勝於治療
   - Skills、AGENTS.md、程式碼模板
2. **Sensors（feedback）** — 觀察與修正
   - Linters、測試、編譯器反饋
3. **Steering Loop** — 迭代改進
   - Mitchell Hashimoto：*"每當 agent 犯錯，就工程化一個解決方案讓它再也無法犯這個錯"*

### OpenClaw 的對應

| Harness 概念 | OpenClaw 實作 |
|-------------|--------------|
| Guides | Skills、AGENTS.md |
| Sensors | HEARTBEAT.md、Cron Jobs |
| Steering Loop | capability-evolver |
| Harness Framework | OpenClaw Gateway |

### 實踐案例

- **OpenAI Codex**：7 工程師 + GPT-5 → 5 個月 100 萬行代碼、1500 PR（零行人類代碼）
- **Stripe Minions**：每週自動合併 1300+ PR
- **Cursor Self-Driving Codebases**：同一模型，成功率 42% → 78%（只有 runtime environment 不同）

### 反直覺發現

**約束反而提升效率** — 窄化解決空間（邊界、架構規則、有限工具）讓 agent 更快收斂到正確答案。

---

## George 的其他 Project Ideas

（陸續更新）

---

## CAD 圖檔處理流程（2026-04-06 / 更新 2026-04-12）

**標準圖框位置：** `~/.openclaw/workspace/cad-reference/仲陽企業-標準圖框.pdf`

**仲陽企業標準圖框內容：**
- 公司：仲陽企業有限公司
- 地址：台中市南區學府路 170 號 2 樓
- TEL：(04)2223-6000 / FAX：(04)2223-2000
- 欄位：製表、審核、批准、圖名、圖號、機種、材質、比例、單位、版本、日期

**公差標準（未標註時適用）：**
| 尺寸範圍 | 公差 |
|---------|------|
| 0-5 mm | ±0.05 mm |
| 5-30 mm | ±0.10 mm |
| 30-120 mm | ±0.20 mm |
| 120-300 mm | ±0.30 mm |

**工作流程：**
1. 收到廠商/工程師的原圖檔
2. 套入仲陽企業標準圖框
3. 有時候需要改上面的尺寸
4. 存檔輸出

**軟體與格式：**
- 主要軟體：SolidWorks
- 可轉換格式：IGES、STEP、X_T
- 輸出：PDF

**CAD Skill（T013）：** 待建立（流程文件化 + 圖框 template 管理）

**儲存位置：**
- Google Drive（團隊共享）
- 或直接給提出需求的人

**待確認：**
- 圖框 template 原始檔位置（CAD 格式）
- Google Drive 資料夾路徑

---

## Precaster-CS-System（語音客服系統）

**日期：** 2026-04-12
**目的：** 工廠/公司語音客服（TW / UK / USA 三區域）
**位置：** `~/.openclaw/workspace/precaster-cs-system/`

**需求：** 24/7 × 20 並發，三語（台灣中文/英式英語/美式英語）

**方案：** ElevenLabs（TTS）- 評估後費用可接受，暫用雲端

**Pipeline：**
```
來電 → ASR（Whisper）→ LLM → TTS（ElevenLabs）
```

**自托管替代方案：**
- VoxCPM2（RTF 0.13，~7-8並發，30語言、Voice Design、Streaming，NT$ 20-28萬）
- GPT-SoVITS（RTF 0.014，~70並發，5秒克隆，NT$ 12-18萬）
- Mac Mini M4 Pro 可行但 TTS 並發受限（~5-8）
- 詳細規格已記錄在 `~/precaster-cs-system/README.md`

**結論：** 現階段用 ElevenLabs，VoxCPM2/GPT-SoVITS 備查

---

## TQC-Monitor（工廠視覺監控系統）

**日期：** 2026-04-12
**目的：** 工廠流水線 AI 視覺分析
**位置：** `~/.openclaw/workspace/TQC-Monitor/`

**三個核心目標：**
1. Buffer 堆積偵測（定點計數，超過 threshold 警報）
2. 兩箱法則（Gate A → Gate B 流動監控）
3. 人員移動追蹤（人流/物流優化）

**硬體架構：**
- Tapo C200/C310（Tapo CLI: appgotapo 控制）
- RTSP 串流 → Edge 節點（Jetson Orin NX 或工控機）

**軟體堆疊：**
- YOLOv8s（物件偵測）+ ByteTrack（追蹤）
- Supervision library（ROI / Gate 設定）
- Alert：Line Notify / MQTT

**狀態：** 🟡 概念階段，待原型開發

---

## Seena rez × ecom-ai-coach（AI 電商教練技能組）

**背景：** Seena rez 是一個電商項目，需要 AI 技能來輔助尋找藍海市場、暢銷產品、品牌真空分析、病毒行銷腳本生成等。

**建議的技能組結構：**
```
ecom-ai-coach/
├── SKILL.md
├── scripts/
│   ├── blue_ocean_seeker.py    # 第一步：找藍海市場
│   ├── product_hunter.py        # 第二步：找暢銷產品
│   ├── brand_vacuum.py          # 第三步：品牌真空分析
│   ├── user_profiler.py         # 第四步：用戶身份標籤
│   ├── supplier_finder.py       # 第五步：找供應商
│   └── viral_script.py          # 第六步：病毒腳本生成
└── prompts/
    ├── market_analysis.md
    └── ad_copy.md
```

**技能優先級：**
| 優先級 | 技能 | 原因 |
| ------ | ---------------------- | ------------------ |
| 🔴 高 | Blue Ocean Seeker | 整個流程的起點，最關鍵 |
| 🔴 高 | Viral Script Generator | Seena rez 最核心的方法 |
| 🟡 中 | Product Hunter | kb-collector 已能做一半 |
| 🟡 中 | Brand Vacuum Detector | LLM 直接可做 |
| 🟢 低 | Supplier Finder | 較通用，其他工具可替代 |

**與 LLLT 產品的關聯：**
- Blue Ocean Seeker 可以用於 LLLT 產品市場分析
- 與 AstroScript 是完全獨立的項目

**待建構：**
- [open] Blue Ocean Seeker 技能
- [open] Viral Script Generator 技能

---

## taskdb — Markdown Task Tracker → PostgreSQL（2026-04-21）

**位置：** `~/.openclaw/workspace/tasks/`
**目的：** 將 Markdown taskpad 同步到 PostgreSQL，支援 CRM/看板查詢

**架構：**
- Markdown（`tasks/taskpad.md`）= 人類可編輯，人和 AI 共同維護
- PostgreSQL（`taskdb.tasks`）= AI agent 查詢
- Sync script: `tasks/sync_tasks_to_sql.py`

**DB Schema：**
| Column | Type | Notes |
|--------|------|-------|
| task_code | VARCHAR(10) PK | T001, T002... |
| title | TEXT | 任務名稱 |
| source_ref | TEXT | MD 檔案來源 |
| priority | VARCHAR(1) | H/M/L |
| assignee | TEXT | |
| status | VARCHAR(1) | A=Active, D=Done, P=Paused, X=Cancelled |
| updated_at | TIMESTAMPTZ | |
| done_at | TIMESTAMPTZ | |

- 完成偵測：標題含「完工/完成/已搞定」→ status=D
- Remark：留在 Markdown，不進 SQL

**Cron:** `taskdb-daily-sync`（每天 06:00 Asia/Taipei）
**Sync script:** `python3 tasks/sync_tasks_to_sql.py`

**Backup Cron:** `taskdb-daily-backup`（每天 07:00 Asia/Taipei）
**Backup script:** `tasks/backup_taskdb.py`
- pg_dump taskdb → 上傳到 Google Drive（Backup folder）→ 刪除本機副本
- 備份位置：Google Drive `/OpenClawBackups/taskdb_YYYYMMDD_HHMMSS.dump`
- 測試成功：✅ 5.1 KB 上傳正常

