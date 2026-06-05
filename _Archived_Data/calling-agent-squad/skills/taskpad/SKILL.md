# taskpad — George's Personal Task Tracker

**Triggers:**
- `/todos` — 原有命令（仍可用）
- `todo` — 直接說不用斜線
- 自然語言 — 「幫我記一下...」「有個任務...」

**Purpose:** Lightweight personal task management with priority triage

**人機共用：** TaskPad 是 George 和 AI Agent 共用的任務介面。
- **George** 在 Obsidian 直接編輯 `~/Documents/Georges/04 📋 Tasks/taskpad.md`
- **AI Agent** 讀寫同一個 Markdown 檔，透過自然語言幫 George 新增/完成/查詢任務
- **PostgreSQL** 備份（`taskdb.tasks`）— 程式查詢用，不當事實來源

---

## Task Format

每個任務：
- **ID** — 唯一代碼（T001, T002..., zt001...）
- **事情** — 要做什麼
- **下一步** — 下一個具體動作
- **追誰** — 負責跟進的人（預設：自己）
- **優先級** — 🔴H / 🟡M / 🟢L
- **建立時間** — YYYY-MM-DD

---

## Priority Levels

| 等級 | 意義 |
|------|------|
| 🔴 **H** | High — 盡快追（>1 週） |
| 🟡 **M** | Medium — 1-2 週內 |
| 🟢 **L** | Low — 不急 |

---

## Commands

### 自然語言（首選）

直接說就可以，AI 自動解析並寫入 taskpad.md：

```
幫我記一下「CA131 模組報價」，等潘望達報價
有個任務：NuGROWS 網站更新，先確認文案需求
```

### `done "task"` 或 `完成 Txxx`

標記任務完成。完成後出現在一次回覆裡，然後歸檔到 Done 區。

### `tasks H|M|L|all`

按優先級列出任務。

---

## File Location

**主要儲存（人機共用）：**
```
~/Documents/Georges/04 📋 Tasks/taskpad.md
```

**PostgreSQL 備份（程式查詢用）：**
```
~/.openclaw/workspace/tasks/sync_tasks_to_sql.py  →  postgresql://localhost/taskdb
```
- sync script 從 Obsidian vault 讀取，向 PostgreSQL 寫入
- 路徑：`TASKS_DIR = ~/Documents/Georges/04 📋 Tasks`
- **手動觸發：** `python3 ~/.openclaw/workspace/tasks/sync_tasks_to_sql.py`
- **自動同步：** 透過 Hermes cron job（每天 06:00 Asia/Taipei）

---

## Task States

| State | Meaning |
|-------|---------|
| 🟡 Active | 開放任務 |
| 🟢 Done | 已完成（歸檔） |

---

## Rules

- 完成任務時：一次顯示在回覆裡，然後移入 Done 區
- 用 `tasks done` 或直接去 Obsidian 看歸檔
- 優先級：🔴H（>1 週）/ 🟡M（1-2 週）/ 🟢L（不急）
- 時間戳記：Asia/Taipei
- **ID 格式：** T 系列（正式任務）/ zt 系列（興趣案子，自動下沉）
