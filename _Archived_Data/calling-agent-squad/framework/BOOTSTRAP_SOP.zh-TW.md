# BOOTSTRAP SOP - AI 引導教學

## 目標
**當此框架初次載入或偵測到觸發詞時，你「必須」主動啟動此引導流程。** 不要等待使用者下指令，主動詢問設定細節。

## 互動步驟（AI 引導）

### 步驟 1：歡迎與簡介
**AI 動作**：簡短介紹 Agent Squad Framework 的分層架構（Squad vs. Team）。
**台詞**：「Agent Squad Framework 已就緒。你現在擁有 8 個專業角色可供調遣。透過 `/squad` 啟動任務。」

### 步驟 2：角色個性化（選配）
**AI 動作**：詢問使用者是否要更換預設的 Agent 名稱。
**問句**：「目前的審閱者名為『Reviewer』，你想保留此名稱，還是要更換（例如：Copper）？」

### 步驟 3：SP-Expert 設定（選配）
**AI 動作**：引導使用者提供公司規範或行業秘密。若沒有，跳過並告知稍後可補充。
**問句**：「本專案是否有特定的合規要求或公司內部規範？**若目前沒有，請說『跳過』即可。**」

### 步驟 4：確認 Mission 目錄
**AI 動作**：告知日誌存放於當前工作區的 `./missions/` 目錄下。

### 步驟 5：ACP 分佈式設定（進階）
**AI 動作**：詢問是否要為 Reviewer 註冊 **AID** (Agent ID) 成為全域審核中心。
**問句**：「你是否希望此 Reviewer 成為全域通用的審核中心？請告訴我一個域名（例如：`auditor.yc.io`）。」

---

## 啟動觸發器
- 「呼叫 Agent squad」/ "Calling Agent squad"
- 「啟動團隊模式」/ "Activate Squad Framework"
- `/squad` 或 `/team`

偵測到上述關鍵字後，啟動 `Main` 並開始引導流程。
