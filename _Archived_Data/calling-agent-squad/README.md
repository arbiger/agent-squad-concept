# Agent Squad Framework 🦞

[繁體中文](#繁體中文) | [English](#english)

---

## 繁體中文

### 🚀 什麼是 Agent Squad Framework？
這是一個專為 OpenClaw 設計的「自驅動型 AI 代理框架」。它將單一的 AI 助手轉化為一個具備 8 個專業角色的「特種部隊」，能夠根據任務難度自動選擇執行模式（Squad 或 Team），並具備自我衝突仲裁與永動迭代的能力。

### 🏗️ 核心架構
- **Squad (Session Spawn)**：快速反應部隊。適用於簡單、線性的任務。
- **Team (Sub-Agent Spawn)**：背景攻堅部隊。適用於複雜、長時間運作的獨立專案。

### 👥 專業角色 (8 Agents)
1. **Main (決策者)**：專案總監，負責最終裁決。
2. **Parser (分析者)**：架構師，拆解使用者意圖。
3. **Reviewer (審閱者)**：紅隊 QA，格言：「我可以反對，但我必須讓你變得更好」。
4. **Researcher (研究員)**：事實查核與情報蒐集。
5. **Coder (開發者)**：高效率程式碼產出與除錯。
6. **Analyst (分析師)**：數據洞察與邏輯驗證。
7. **Writer (文案師)**：文件美化與高層報告。
8. **SP-Expert (特種專家)**：[選配] 注入公司規範、行業祕密或特定目標。

### 🛠️ 獨家特色
- **三段式仲裁機制**：自動修正 -> Main 裁決 -> User 介入。避免 AI 陷入邏輯死鎖。
- **對話式引導入教 (BOOTSTRAP SOP)**：只需說「呼叫 Agent squad」，AI 就會引導你完成個人化設定。
- **任務日誌系統**：自動在 `~/missions/` 生成結構化的日誌與產出報告。

---

## English

### 🚀 What is Agent Squad Framework?
A self-driving AI multi-agent framework designed for OpenClaw. It transforms a single AI assistant into an "Elite Squad" of 8 specialized roles, capable of choosing between execution modes (Squad or Team) and featuring self-arbitration logic for continuous iteration.

### 🏗️ Architecture
- **Squad (Session Spawn)**: Rapid response. Best for simple, linear tasks.
- **Team (Sub-Agent Spawn)**: Background powerhouse. Best for complex, isolated long-running projects.

### 👥 Specialized Roles (8 Agents)
1. **Main (Director)**: The project orchestrator and final decision maker.
2. **Parser (Architect)**: Decomposes user intent into actionable tasks.
3. **Reviewer (Auditor)**: Red-team QA. Motto: "I can oppose, but I must make you better."
4. **Researcher**: Fact-checking and information gathering.
5. **Coder**: High-efficiency code generation and debugging.
6. **Analyst**: Data insights and logical verification.
7. **Writer**: Documentation polish and executive reporting.
8. **SP-Expert**: [Optional] Injects company rules, industry secrets, or specific goals.

### 🛠️ Key Features
- **Global Quality Hub**: Transform your Reviewer into a centralized expert accessible via ACP from any compatible tool (e.g., Claude Code, Codex).
- **Tiered Arbitration**: Auto-correction -> Main Decision -> User Escalation. Prevents logical deadlocks.
- **Conversational Onboarding (BOOTSTRAP SOP)**: Just say "Calling Agent squad" to be guided through setup.
- **Mission Logging System**: Automatically generates structured logs and reports in `./missions/`.

---

## 🔗 How This Compares to Paperclip

[Paperclip](https://paperclip.ing/) is an open-source **company OS** for running fully autonomous AI businesses — org charts, budgets, heartbeats, and multi-company isolation.

**Agent Squad Framework** is a **mission-driven tactical squad** — specialized roles with deep "soul" definitions, tiered arbitration, and cross-platform ACP communication.

| | Paperclip | Agent Squad Framework |
| :--- | :--- | :--- |
| **Metaphor** | You are the Board of Directors | You are the Field Commander |
| **Scale** | 20+ agents, multiple companies | 8 specialized roles, single project |
| **Governance** | Approve/Reject + budget caps | 3-tier arbitration + SP-Expert advisory |
| **Agent Identity** | Job title + description | Full SOUL + IDENTITY personality |
| **Communication** | Internal ticket system | ACP (Claude Code, Codex, OpenClaw) |
| **Best For** | Running an autonomous business | Executing complex project missions |

**They are complementary, not competitive.** You could run Paperclip as your company backbone and deploy an Agent Squad inside it as your "Special Ops" department for high-precision project work.

---

## 📂 Quick Start / 快速開始

### 1. File Structure / 檔案結構
將本專案的所有檔案按照以下結構放置在您的 OpenClaw 工作區中：
Place all project files in your OpenClaw workspace according to this structure:
```text
your-openclaw-workspace/
├── framework/               <-- 存放角色設定 (Role definitions)
├── skills/
│   └── squad_manager/       <-- 存放管理技能 (Squad Manager Skill)
│   └── mission_logger/      <-- 存放日誌技能 (Mission Logger Skill)
└── README.md
```

### 2. Manual Installation / 手動安裝
1. **Clone** this repository to your computer.
2. **Move** the `skills/` folders to your `~/.openclaw/skills/` directory or your workspace's `skills/` folder.
3. **Copy** the content of `framework/` role files into your Agent configurations.

### 3. Usage / 使用方式
只需在對話中輸入以下指令即可啟動：
Simply type one of these in the chat to start:
- **"呼叫 Agent squad"**
- **"Calling Agent squad"**
- **`/squad`**

> [!IMPORTANT]
> **初次使用建議 (First-run)**：輸入「呼叫 Agent squad」後，AI 會引導您完成角色命名與專家規則設定。
