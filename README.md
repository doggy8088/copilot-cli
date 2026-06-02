# GitHub Copilot CLI

GitHub Copilot 的強大能力，現在進入你的終端機。

GitHub Copilot CLI 將 AI 驅動的程式開發協助直接帶到你的命令列，讓你能透過自然語言對話來建置、除錯並理解程式碼。它由與 GitHub Copilot coding agent 相同的 agentic harness 驅動，在與 GitHub 工作流程深度整合的同時，提供智慧輔助。

更多資訊請參閱[官方文件](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)。

![Copilot CLI 啟動畫面的圖片](https://github.com/user-attachments/assets/f40aa23d-09dd-499e-9457-1d57d3368887)


## 🚀 Introduction and Overview

我們將 GitHub Copilot coding agent 的能力直接帶到你的終端機。使用 GitHub Copilot CLI，你可以在本機以同步方式與理解你的程式碼和 GitHub 情境的 AI agent 協作。

- **原生終端機開發：** 直接在命令列中使用 Copilot coding agent，不必切換工作情境。
- **開箱即用的 GitHub 整合：** 使用自然語言存取你的 repositories、issues 與 pull requests，並直接沿用你現有的 GitHub 帳號完成驗證。
- **Agentic 能力：** 與能規劃並執行複雜任務的 AI 協作者一起建置、編輯、除錯與重構程式碼。
- **MCP 驅動的可延伸性：** coding agent 預設隨附 GitHub 的 MCP server，並支援自訂 MCP servers 來擴充能力。
- **完整掌控：** 執行前可預覽每個動作，未經你明確同意，任何操作都不會發生。

我們還在這段旅程的早期階段，但在你的回饋協助下，我們正快速迭代，讓 GitHub Copilot CLI 成為你終端機中最可靠的夥伴。

## 📦 Getting Started

### Supported Platforms

- **Linux**
- **macOS**
- **Windows**

### Prerequisites

- (在 Windows 上) **PowerShell** v6 或以上版本
- 需要有效的 **Copilot 訂閱**。請參閱 [Copilot plans](https://github.com/features/copilot/plans?ref_cta=Copilot+plans+signup&ref_loc=install-copilot-cli&ref_page=docs)。

如果你是透過組織或企業取得 GitHub Copilot 的使用權，而你的組織擁有者或企業管理員已在組織或企業設定中停用 GitHub Copilot CLI，則你無法使用 GitHub Copilot CLI。更多資訊請參閱 [Managing policies and features for GitHub Copilot in your organization](http://docs.github.com/copilot/managing-copilot/managing-github-copilot-in-your-organization/managing-github-copilot-features-in-your-organization/managing-policies-for-copilot-in-your-organization)。

### Installation

使用安裝腳本安裝（macOS 與 Linux）：

```bash
curl -fsSL https://gh.io/copilot-install | bash
```

或

```bash
wget -qO- https://gh.io/copilot-install | bash
```

使用 `| sudo bash` 可用 root 身分執行，並安裝到 `/usr/local/bin`。

設定 `PREFIX` 可安裝到 `$PREFIX/bin/` 目錄。以 root 執行時預設為 `/usr/local`，以非 root 使用者執行時預設為 `$HOME/.local`。

設定 `VERSION` 可安裝指定版本。預設為最新版本。

例如，要將 `v0.0.369` 安裝到自訂目錄：

```bash
curl -fsSL https://gh.io/copilot-install | VERSION="v0.0.369" PREFIX="$HOME/custom" bash
```

使用 [Homebrew](https://formulae.brew.sh/cask/copilot-cli) 安裝（macOS 與 Linux）：

```bash
brew install copilot-cli
```

```bash
brew install copilot-cli@prerelease
```


使用 [WinGet](https://github.com/microsoft/winget-cli) 安裝（Windows）：

```bash
winget install GitHub.Copilot
```

```bash
winget install GitHub.Copilot.Prerelease
```


使用 [npm](https://www.npmjs.com/package/@github/copilot) 安裝（macOS、Linux 與 Windows）：

```bash
npm install -g @github/copilot
```

```bash
npm install -g @github/copilot@prerelease
```


### Launching the CLI

```bash
copilot
```

首次啟動時，你會看到我們可愛的動畫橫幅。如果你想再次查看，請使用 `--banner` 旗標啟動 `copilot`。

如果你目前尚未登入 GitHub，系統會提示你使用 `/login` 斜線指令。輸入該指令並依照畫面上的說明完成驗證。

#### Authenticate with a Personal Access Token (PAT)

你也可以使用已啟用 "Copilot Requests" 權限的細粒度 PAT 進行驗證。

1. 前往 https://github.com/settings/personal-access-tokens/new
2. 在 "Permissions" 底下點選 "add permissions"，並選擇 "Copilot Requests"
3. 產生你的 token
4. 透過環境變數 `GH_TOKEN` 或 `GITHUB_TOKEN`（依此前後順序優先）將 token 加入你的環境

### Using the CLI

在包含你要處理程式碼的資料夾中啟動 `copilot`。

預設情況下，`copilot` 會使用 Claude Sonnet 4.5。執行 `/model` 斜線指令，可從其他可用模型中選擇，包括 Claude Sonnet 4 與 GPT-5。

### Experimental Mode

Experimental mode 可讓你使用仍在開發中的新功能。你可以透過以下方式啟用：

- 使用 `--experimental` 旗標啟動：`copilot --experimental`
- 在 CLI 內使用 `/experimental` 斜線指令

啟用後，該設定會持久化到你的 config 中，因此後續啟動時不再需要 `--experimental` 旗標。

#### Experimental Features

- **Autopilot mode：** Autopilot 是一種新模式（按 `Shift+Tab` 可循環切換模式），會鼓勵 agent 持續工作直到任務完成。

每次你向 GitHub Copilot CLI 提交提示時，每月的 premium requests 配額都會減少一個。如需了解 premium requests，請參閱 [About premium requests](https://docs.github.com/copilot/managing-copilot/monitoring-usage-and-entitlements/about-premium-requests)。

如需更多關於 GitHub Copilot CLI 使用方式的資訊，請參閱[官方文件](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)。

## 🔧 Configuring LSP Servers

GitHub Copilot CLI 支援 Language Server Protocol（LSP），可提供更強的程式碼智慧功能。這項功能提供如 go-to-definition、hover 資訊與 diagnostics 等智慧程式碼能力。

### Installing Language Servers

Copilot CLI 不會內建 LSP servers。你需要另外安裝。例如，要設定 TypeScript 支援：

```bash
npm install -g typescript-language-server
```

對於其他語言，請安裝對應的 LSP server，並依照下方示範的相同模式完成設定。

### Configuring LSP Servers

LSP servers 透過專用的 LSP 設定檔進行設定。你可以在使用者層級或儲存庫層級設定 LSP servers：

**使用者層級設定**（套用到所有專案）：
編輯 `~/.copilot/lsp-config.json`

**儲存庫層級設定**（套用到特定專案）：
在你的儲存庫根目錄建立 `.github/lsp.json`

設定範例：

```json
{
  "lspServers": {
    "typescript": {
      "command": "typescript-language-server",
      "args": ["--stdio"],
      "fileExtensions": {
        ".ts": "typescript",
        ".tsx": "typescript"
      }
    }
  }
}
```

### Viewing LSP Server Status

你可以在互動式工作階段中使用 `/lsp` 指令檢查已設定的 LSP servers，或直接查看你的設定檔。

更多資訊請參閱 [changelog](./changelog.md)。

## 📢 Feedback and Participation

很高興能在 Copilot CLI 的早期階段與你一起前進。

我們正在快速建置中。請預期會有頻繁更新，並讓你的 client 保持最新，以取得最新功能與修正。

你的觀點非常重要。歡迎在這個 repo 開 issue、參與 Discussions，並在 CLI 中執行 `/feedback` 提交保密的意見回饋問卷。
