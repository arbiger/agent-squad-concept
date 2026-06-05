# 如何自定義你的 Agent Squad

這個框架設計為模組化。你可以輕鬆更換 Agent 名稱或個性，同時保留核心邏輯不變。

## 1. 重新命名 Agent
若要重新命名（例如將 `Reviewer` 改為 `Copper`）：
- **檔案名稱**：將 `framework/Reviewer.md` 和 `framework/Reviewer.zh-TW.md` 重新命名。
- **身份提示詞**：更新檔案中的 `IDENTITY` 區段以符合新名稱。
- **Main 的靈魂**：更新 `framework/Main.md` 使其邏輯指向新的命名。

## 2. 動態個性化
若你想要特定的「語氣」（例如：積極型 vs. 外交型），可以替換 `IDENTITY` 區段，同時保留 `SOUL`（核心邏輯）不動。

## 3. 加入領域專家
在 `framework/` 中依照 `SP-Expert.md` 的模板建立新檔案，注入特定的限制條件或專業知識到你的 Squad 中。
