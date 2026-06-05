# Calling Agent Squad | 呼叫特工小隊

![OpenClaw Skill](https://img.shields.io/badge/OpenClaw-Skill-blue)
![Version](https://img.shields.io/badge/Version-1.0.0-green)
![License](https://img.shields.io/badge/License-MIT-yellow)

Multi-agent squad workflow skill for OpenClaw. Coordinate a team of specialized agents to handle complex projects with professional rigor.

適用於 OpenClaw 的多智能體團隊工作流 skill。可協調專業特工團隊處理複雜項目。

---

## 功能 | Features

### 兩種模式 | Two Modes

| 指令 | 模式 | 說明 |
|------|------|------|
| `calling squad [題目]` | Standard | 讀取 SOUL/IDENTITY 後扮演各角色 |
| `calling squad full [題目]` | Full | spawn 真的 sub-agents |

### 團隊角色 | Team Roles

- 🦞 **Manager** - 協調與調度
- 📐 **Architect** - 規劃系統藍圖
- 🔍 **Researcher** - 市場與技術情報收集
- ✍️ **Copywriter** - 行銷與技術文案
- 🛡️ **Reviewer** - 品質稽核
- 📋 **Observer** - 任務日誌

---

## 安裝 | Installation

```bash
clawhub install calling-agent-squad
```

或手動複製到你的 skills 目錄：

```bash
cp -r calling-agent-squad ~/.openclaw/workspace/skills/
```

---

## 使用 | Usage

### Standard Mode (快速模式)

```
calling squad [項目] [任務詳情]
```

- 我會扮演所有角色完成任務
- 每個角色前會讀取其 SOUL.md 和 IDENTITY.md
- 任務結束後回歸正常

**Example | 示例:**
```
calling squad laser distance meter US market research
```

### Full Mode (完整模式)

```
calling squad full [項目] [任務詳情]
```

- 真正 spawn sub-agents
- 每個 agent 有獨立的工作區
- 適合複雜任務

---

## 資料夾結構 | Folder Structure

```
calling-agent-squad/
├── SKILL.md                 # Skill 說明
├── squad-init.sh            # 初始化腳本
├── agents/                  # 各角色配置
│   ├── squad-manager/
│   │   ├── SOUL.md
│   │   ├── IDENTITY.md
│   │   └── TOOLS.md
│   ├── researcher/
│   ├── architect/
│   ├── copywriter/
│   └── observer/
└── templates/
```

---

## 輸出 | Output

所有項目保存在：`Documents/squad_projects/[項目]_[年月日]/`

---

## 授權 | License

MIT License

---

## 作者 | Author

Megan (@arbiger)
