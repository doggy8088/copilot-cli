# GitHub Copilot CLI（公開預覽版）

GitHub Copilot 的強大功能，現在帶到你的終端機。

GitHub Copilot CLI 將 AI 驅動的程式設計協作直接帶到你的命令列，讓你可以透過自然語言對話來建構、除錯與理解程式碼。它採用了與 GitHub Copilot 程式設計代理相同的 agentic 框架，提供聰明的協作並且深度整合進你的 GitHub 工作流程。

詳情請參閱［官方文件］(https://docs.github.com/copilot/concepts/agents/about-copilot-cli)。

![Copilot CLI 的啟動畫面圖片](https://github.com/user-attachments/assets/f40aa23d-09dd-499e-9457-1d57d3368887)


## 🚀 介紹與概覽

我們將 GitHub Copilot 程式設計代理直接帶到你的終端機。有了 GitHub Copilot CLI，你可以在本地端與可以理解你的程式碼和 GitHub 情境的 AI 代理同步協作。

- **終端機原生開發：** 直接在命令列使用 Copilot 程式設計代理——無須切換情境。
- **GitHub 原生整合：** 使用自然語言存取你的儲存庫、issue 及 pull request，並透過你現有的 GitHub 帳戶進行驗證。
- **Agentic 能力：** 與能夠規劃和執行複雜任務的 AI 夥伴一起建構、編輯、除錯與重構程式碼。
- **MCP 強化擴充性：** 內建 GitHub 的 MCP 伺服器，並支援自訂 MCP 伺服器，擴展功能。
- **完全掌控：** 每個動作執行前都可預覽——所有操作都需你明確同意後才會發生。

我們還在初期階段，但隨著你的回饋，我們正快速迭代，希望將 GitHub Copilot CLI 打造成你終端機中最棒的助理。

## 📦 入門指南

### 支援平台

- **Linux**
- **macOS**
- **Windows**

### 先決條件

- （Windows 上）**PowerShell** v6 或更高版本
- **有效的 Copilot 訂閱**。請參考［Copilot 方案］(https://github.com/features/copilot/plans?ref_cta=Copilot+plans+signup&ref_loc=install-copilot-cli&ref_page=docs) 。

如果你是透過組織或企業取得 GitHub Copilot 存取權，且你的組織擁有者或企業管理員在組織／企業設定中停用了 Copilot CLI，你將無法使用 GitHub Copilot CLI。詳情請見［在你的組織管理 GitHub Copilot 的政策與功能］(http://docs.github.com/copilot/managing-copilot/managing-github-copilot-in-your-organization/managing-github-copilot-features-in-your-organization/managing-policies-for-copilot-in-your-organization)。

### 安裝方式

以 [WinGet](https://github.com/microsoft/winget-cli)（Windows）安裝：

```bash
winget install GitHub.Copilot
```

```bash
winget install GitHub.Copilot.Prerelease
```

以 [Homebrew](https://formulae.brew.sh/cask/copilot-cli)（macOS 與 Linux）安裝：

```bash
brew install copilot-cli
```

```bash
brew install copilot-cli@prerelease
```

以 [npm](https://www.npmjs.com/package/@github/copilot)（macOS、Linux 及 Windows）安裝：

```bash
npm install -g @github/copilot
```

```bash
npm install -g @github/copilot@prerelease
```

以安裝腳本（macOS 與 Linux）安裝：

```bash
curl -fsSL https://gh.io/copilot-install | bash
```

或

```bash
wget -qO- https://gh.io/copilot-install | bash
```

如需以 root 執行並安裝至 `/usr/local/bin`，請使用 `| sudo bash`。

可設定 `PREFIX` 以安裝至 `$PREFIX/bin/` 目錄。以 root 執行時預設為 `/usr/local`，非 root 使用者預設為 `$HOME/.local`。

可設定 `VERSION` 以安裝特定版本，預設為最新版。

例如，將 `v0.0.369` 安裝到自訂目錄：

```bash
curl -fsSL https://gh.io/copilot-install | VERSION="v0.0.369" PREFIX="$HOME/custom" bash
```

### 啟動 CLI

```bash
copilot
```

首次啟動時，你會看到我們可愛的動畫橫幅！如果想再次看到此橫幅，請加上 `--banner` 旗標啟動 `copilot`。

如果你尚未登入 GitHub，系統將提示你使用 `/login` 指令。輸入該指令並依畫面指示完成驗證。

#### 以個人存取權杖（PAT）驗證

你也可以使用已啟用「Copilot Requests」權限的精細權限 PAT 進行驗證。

1. 瀏覽 https://github.com/settings/personal-access-tokens/new
2. 在「Permissions」下點選「add permissions」，選擇「Copilot Requests」
3. 產生你的權杖
4. 透過 `GH_TOKEN` 或 `GITHUB_TOKEN` 環境變數（優先順序）將權杖加入你的環境

### 使用 CLI

在包含你要操作程式碼的資料夾中啟動 `copilot`。

預設狀態下，`copilot` 使用 Claude Sonnet 4.5。可執行 `/model` 指令切換其他可用模型，包括 Claude Sonnet 4 與 GPT-5。

每次你向 GitHub Copilot CLI 提交提示時，你的每月進階請求額度將扣除一次。關於進階請求的資訊請參見［關於進階請求］(https://docs.github.com/copilot/managing-copilot/monitoring-usage-and-entitlements/about-premium-requests)。

更多有關 GitHub Copilot CLI 的使用說明，請參見［官方文件］(https://docs.github.com/copilot/concepts/agents/about-copilot-cli)。

## 📢 意見回饋與參與

我們非常高興在 Copilot CLI 的早期邀請你加入旅程！

這是早期預覽版本，我們正快速開發中。請期待頻繁更新——並保持你的用戶端隨時更新，以獲得最新功能和修正！

你的意見非常重要！歡迎在本專案回報 issue、加入討論區，或在 CLI 執行 `/feedback` 來提交匿名回饋問卷！
