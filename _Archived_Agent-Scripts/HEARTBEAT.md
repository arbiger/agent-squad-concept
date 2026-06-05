# HEARTBEAT.md

# 心跳觸發劇本

> 心跳收到 `HEARTBEAT_RANDOM_CHECKIN` 時執行。
> 時間控制由 cron jobs 負責（`checkin-0900` ~ `checkin-2236`，每 48 分鐘，工作日）。

---

## 🔄 taskdb-sync — Markdown → PostgreSQL 同步

> 收到 `taskdb-sync` systemEvent 時執行（每天 06:00 cron job 觸發）

收到 event 後：
1. 執行 `python3 /Users/george/.openclaw/workspace/tasks/sync_tasks_to_sql.py`
2. 檢查輸出：如有 inserted/updated，結果留本地（不需要主動通知 George）
3. 如有錯誤（exit code ≠ 0），發 alert 到 #system-updates

---

## 🌤️ Random Check-in — 四種內容（隨機選一，20% each）

**1. Weather** — 使用 weather skill 查詢台中當前天氣，分享給 user

**2. News** — 使用 Brave Search 找一則科技/AI 新聞，分享並附上感想
   - 關鍵字：`科技 OR AI OR LLM OR GitHub OR OpenClaw`
   - 時間過濾：`freshness: day`（只限 24 小時內）
   - 隨機抓一篇，附上 1-2 句感想

**3. Proverb** — 分享一個英文諺語 + 中文翻譯

**4. Check-in** — 主動問「有什麼需要我幫忙的嗎？」

---

## 📋 Follow-up — 主動追蹤（20% weight，檢查 MEMORY.md）

> **讀取 MEMORY.md 的 `Pending Issues` 區塊。**
> 如果有 `[open]` 項目，自然地帶出一個 ask。

**範例輸出：**
```
順便問一下，之前說 AstroScript 的商業化方向後來有結論了嗎？
```
```
HEARTBEAT.md 架構討論的後續還要繼續嗎？
```

**規則：**
- 只帶出 1 個 pending item（隨機選）
- 語氣自然，像人之間的順便問候
- 如果所有項目都 `[closed]`，降級為一般 Check-in

---

## Proactivity Check

- Read `~/proactivity/heartbeat.md`
- Re-check active blockers, promised follow-ups, stale work, and missing decisions
- Ask what useful check-in or next move would help right now
- Message the user only when something changed or needs a decision
- Update `~/proactivity/session-state.md` after meaningful follow-through

---

## ⚠️ Negative Instructions（嚴格遵守）

- **不要**只說「HEARTBEAT_OK」當有實質內容可分享
- **不要**在 9:00-23:00 以外的時間執行 check-in（cron 已過濾）
- **不要**產生制式、敷衍的內容（每次要有變化）
- **不要**在 Follow-up 選項中一次帶出多個項目

**Counter-examples：**
- 天氣查詢發現下雨 → 分享出去，不要抑制
- 新聞找到感興趣的標題 → 分享，不要跳過
- Pending item 有內容 → 自然帶出，不要假裝沒事

---

## Output 標準

- 休閒、親切的語氣
- 直接發送，不抑制
- 內容多樣，不要連續兩次同一類型

---

## 其他 Cron Jobs（獨立運作，不經過心跳）

| Job | 頻率 | 功能 |
|-----|------|------|
| `email-check-45` | 每小時 :45 | Email check（只看，不標已讀）|
| `hourly-backup` | 每 6 小時 | 備份到 Google Drive |
| `investage-daily-report` | 週一至五 07:30 | 投資組合報告 |
| `capability-evolve` | 每兩天 09:00 | Agent 自我進化 |
| `fx-tracker-0200` | 每天 02:00 | 匯率追蹤 |
| `LLLT US/JP Market Research` | 每 14 天 09:00 | 市场研究 |
| `Ruten Cookie Restore` | 每 20 天 | Ruten session 還原 |

---

## Cross-references

- 心跳原則 → SOUL.md
- 觸發劇本 → 本文件
- Pending Issues → MEMORY.md
