# SKILL - Mission Logger（任務日誌管理員）

## 描述
負責管理 `./missions/` 目錄下的所有任務文件。確保每個任務都有結構化的指令、日誌與產出記錄。

## 工具指令

### 1. `init_mission`
**參數**：`mission_name`、`instructions`
**動作**：
- 建立 `./missions/[mission_name]-report/` 目錄。
- 建立 `outputs/` 子目錄。
- 寫入 `Mission_Instruction.md`，包含使用者目標與任務拆解。

### 2. `log_activity`
**參數**：`mission_name`、`agent_role`、`content`、`reviewer_feedback`（可選）
**動作**：
- 以追加模式寫入 `Mission_Log.md`。
- 格式：
  ```markdown
  ## [時間戳] - [角色名稱] 產出
  內容: ...
  Reviewer 審核意見: ...
  ```

### 3. `save_output`
**參數**：`mission_name`、`filename`、`content`
**動作**：將 `content` 寫入 `./missions/[mission_name]-report/outputs/[filename]`。

## 使用範例
`Main` 在啟動任務後調用 `init_mission`，並在每個 Sub-agent 完成工作後調用 `log_activity` 與 `save_output`。
