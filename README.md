# GitHub Copilot CLI（公開預覽）

GitHub Copilot 的能力，現在進駐你的終端機。

GitHub Copilot CLI 將 AI 驅動的程式協作直接帶入命令列，讓你透過自然語言對話來建立、除錯並理解程式碼。它使用與 GitHub Copilot 程式代理相同的 agentic 架構，並在深度整合 GitHub 工作流程的同時，提供智慧型協作。

更多資訊請參考[官方文件](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)。

![Copilot CLI 啟動畫面示意圖](https://github.com/user-attachments/assets/51ac25d2-c074-467a-9c88-38a8d76690e3)

## 🚀 介紹與總覽

我們將 GitHub Copilot 程式代理的能力直接帶到你的終端機。使用 GitHub Copilot CLI，你可以在本機、同步地與一個理解你程式碼與 GitHub 脈絡的 AI 代理協作。

- **終端機原生開發**：直接在命令列中與 Copilot 程式代理協作，無需切換環境。
- **原生 GitHub 整合**：透過自然語言存取你的儲存庫、議題與拉取請求，並使用你既有的 GitHub 帳號完成驗證。
- **Agentic 能力**：建構、編輯、除錯與重構程式碼，讓 AI 協作者能規劃並執行複雜任務。
- **MCP 延展性**：內建 GitHub MCP server，並支援自訂 MCP server 用於能力擴充。
- **完整掌控**：每次動作皆會預先預覽，不會在未經你明確允許的情況下執行。

我們仍處於早期階段，但會持續依據回饋快速迭代，打造最適合作為你終端機夥伴的 GitHub Copilot CLI。

## 📦 快速開始

### 支援平台

- **Linux**
- **macOS**
- **Windows**

### 前置需求

- **Node.js** v22 或以上
- **npm** v10 或以上
- （Windows）**PowerShell** v6 或以上
- **有效的 Copilot 訂閱**。參考 [Copilot 方案](https://github.com/features/copilot/plans?ref_cta=Copilot+plans+signup&ref_loc=install-copilot-cli&ref_page=docs)。

若你的組織或企業透過授權提供 GitHub Copilot，而管理者停用了 Copilot CLI，則無法使用。詳見[在組織中管理 GitHub Copilot 的原則與功能](http://docs.github.com/copilot/managing-copilot/managing-github-copilot-in-your-organization/managing-github-copilot-features-in-your-organization/managing-policies-for-copilot-in-your-organization)。

### 安裝方式

使用 npm 全域安裝：

```bash
npm install -g @github/copilot
```

使用 [Homebrew](https://formulae.brew.sh/cask/copilot-cli) 安裝：

```bash
brew install copilot-cli
```

使用 [WinGet](https://github.com/microsoft/winget-cli) 安裝：

```bash
winget install GitHub.Copilot
```

### 啟動 CLI

```bash
copilot
```

首次啟動會看到可愛的動畫橫幅。若想再次觀看，可加上 `--banner` 旗標啟動。

若尚未登入 GitHub，系統將提示使用 `/login` 指令。輸入該指令並依畫面指示完成驗證。

#### 使用個人存取權杖（PAT）驗證

你也可以使用具備「Copilot Requests」權限的細粒度 PAT 進行驗證。

1. 前往 https://github.com/settings/personal-access-tokens/new
2. 在「Permissions」中點選「add permissions」，選取「Copilot Requests」
3. 產生權杖
4. 將權杖加入環境變數 `GH_TOKEN` 或 `GITHUB_TOKEN`（依優先順序）

### 使用 CLI

在包含你要處理的程式碼的資料夾中啟動 `copilot`。

預設使用 Claude Sonnet 4.5。可執行 `/model` 指令切換至其他可用模型，例如 Claude Sonnet 4 或 GPT-5。

每次向 GitHub Copilot CLI 提交提示，會扣除一次每月的進階請求額度。關於進階請求的資訊請參考[進階請求說明](https://docs.github.com/copilot/managing-copilot/monitoring-usage-and-entitlements/about-premium-requests)。

更多使用方式請參考[官方文件](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)。

## 📢 回饋與參與

我們期待你加入 Copilot CLI 的早期使用旅程。

這是早期預覽版本，我們正在快速開發中。更新頻繁，請保持你的客戶端在最新版本以取得最新功能與修正。

你的洞察十分重要。可在此儲存庫開 issue、加入 Discussions，或在 CLI 中執行 `/feedback` 送出機密回饋問卷。
