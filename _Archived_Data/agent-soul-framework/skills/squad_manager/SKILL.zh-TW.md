# SKILL - Squad Manager（團隊管理員）

## 描述
`Main` 代理的核心驅動邏輯。根據任務的複雜度、預期時長與隔離需求，動態選擇調用「Squad (Session)」、「Team (Sub-agent)」或「Distributed (ACP)」模式。

## 🔹 初次運行建議
當此 Skill 被啟動或偵測到「呼叫 Agent squad」時，請**務必參照 `framework/BOOTSTRAP_SOP.zh-TW.md`** 進行引導。主動詢問使用者：
1. 是否要更換 Agent 名稱。
2. 是否有特定的 SP-Expert 規則需要注入。
3. 任務報告的存儲位置。

## 決策矩陣

| 維度 | Squad（sessions_spawn） | Team（/subagents spawn） | Distributed（ACP） |
| --- | --- | --- | --- |
| **複雜度** | 低至中（單一任務） | 中至高（多步驟專案） | 極高（分佈式/外部協作） |
| **預期時長** | 短（< 5 分鐘） | 長（> 5 分鐘，需背景執行） | 長時間且需與外部 Agent 協作 |
| **回報機制** | 同步等待或主動查詢 | 完成後非同步回報 | 透過 ACP 通道即時對話 |
| **典型任務** | 語法檢查、單一搜尋 | 開發新功能、深度研究 | 與外部團隊、ACP 聯網 Agent 協作 |

## 啟動觸發器
- **斜槓指令**：`/squad`、`/team`、`/acp`
- **自然語言**：
    - 「呼叫 Agent squad」/ "Calling Agent squad"
    - 「啟動團隊模式」/ "Activate Team mode"

## 工具指令

### 1. `delegate_task`
**參數**：`task_description`、`preferred_agent`、`mode`（auto|squad|team|acp）
**動作**：
- `squad`：調用 `sessions_spawn` 啟動對應角色，等待結果。
- `team`：調用 `subagents_spawn` 啟動背景 Sub-agent，記錄 `runId`。
- `acp`：使用 `acp send` 與特定的 **AID**（Agent ID）進行對話。
- `auto`：由 `Main` 根據任務描述自行判斷。

### 2. `monitor_team`
**參數**：`run_id`（可選）
**動作**：使用 `subagents list` 獲取所有背景任務狀態；使用 `subagents log` 獲取特定任務進度。

### 3. `collect_results`
**動作**：Sub-agent 完工後，觸發 `Reviewer` 進行初步審核，再交由 `Main` 最終整合。

## 注意事項
- `Main` 在每次分工前，須向使用者報告：「正在將此任務以 [模式] 交由 [Agent] 處理。」
