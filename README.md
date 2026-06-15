# GitHub Copilot CLI

GitHub Copilot 的強大能力，現在就在你的終端機中。

GitHub Copilot CLI 將 AI 驅動的程式設計協助直接帶到你的命令列，讓你能透過自然語言對話來建置、除錯並理解程式碼。它採用與 GitHub Copilot coding agent 相同的 agentic harness，在深度整合 GitHub 工作流程的同時提供智慧協助。

更多資訊請參閱[官方文件](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)。

![Copilot CLI 啟動畫面的圖片](https://github.com/user-attachments/assets/f40aa23d-09dd-499e-9457-1d57d3368887)


## 🚀 介紹與總覽

我們將 GitHub Copilot coding agent 的強大能力直接帶進你的終端機。有了 GitHub Copilot CLI，你可以在本機以同步方式與一個理解你程式碼與 GitHub 情境的 AI agent 協作。

- **終端機原生開發：** 直接在命令列中與 Copilot coding agent 協作，不需要切換情境。
- **開箱即用的 GitHub 整合：** 使用自然語言存取你的 repositories、issues 與 pull requests，並直接使用你既有的 GitHub 帳號完成驗證。
- **Agentic 能力：** 與能規劃並執行複雜任務的 AI 協作者一起建置、編輯、除錯與重構程式碼。
- **MCP 驅動的可擴充性：** 善用 coding agent 預設隨附的 GitHub MCP server，並支援自訂 MCP servers 以擴充能力。
- **完整掌控：** 每個動作在執行前都可先預覽，沒有你的明確批准就不會發生任何事。

我們仍處於發展早期，但在你的回饋協助下，我們正快速迭代，致力讓 GitHub Copilot CLI 成為你終端機中最理想的夥伴。

## 📦 開始使用

### 支援平台

- **Linux**
- **macOS**
- **Windows**

### 先決條件

- (在 Windows 上) **PowerShell** v6 或更新版本
- 需要**有效的 Copilot 訂閱**。請參閱 [Copilot 方案](https://github.com/features/copilot/plans?ref_cta=Copilot+plans+signup&ref_loc=install-copilot-cli&ref_page=docs)。

如果你是透過組織或企業取得 GitHub Copilot 的存取權，而你的組織擁有者或企業管理員已在組織或企業設定中停用 GitHub Copilot CLI，則你無法使用 GitHub Copilot CLI。更多資訊請參閱[在組織中管理 GitHub Copilot 的政策與功能](http://docs.github.com/copilot/managing-copilot/managing-github-copilot-in-your-organization/managing-github-copilot-features-in-your-organization/managing-policies-for-copilot-in-your-organization)。

### 安裝

使用安裝腳本安裝（macOS 與 Linux）：

```bash
curl -fsSL https://gh.io/copilot-install | bash
```

或

```bash
wget -qO- https://gh.io/copilot-install | bash
```

使用 `| sudo bash` 以 root 身分執行，並安裝到 `/usr/local/bin`。

設定 `PREFIX` 可安裝到 `$PREFIX/bin/` 目錄。以 root 執行時預設為 `/usr/local`，
以非 root 使用者執行時預設為 `$HOME/.local`。

設定 `VERSION` 可安裝指定版本。預設會安裝最新版本。

例如，要將版本 `v0.0.369` 安裝到自訂目錄：

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


### 啟動 CLI

```bash
copilot
```

第一次啟動時，你會看到我們可愛的動態橫幅。如果你想再次看到這個橫幅，可在啟動 `copilot` 時加上 `--banner` 旗標。

如果你目前尚未登入 GitHub，系統會提示你使用 `/login` 斜線指令。輸入這個指令並依照畫面上的說明完成驗證。

#### 使用 Personal Access Token (PAT) 驗證

你也可以使用已啟用 "Copilot Requests" 權限的細粒度 PAT 進行驗證。

1. 前往 https://github.com/settings/personal-access-tokens/new
2. 在 "Permissions" 下，點擊 "add permissions" 並選擇 "Copilot Requests"
3. 產生你的 token
4. 透過環境變數 `GH_TOKEN` 或 `GITHUB_TOKEN`（依此優先順序）將 token 加入你的環境

### 使用 CLI

在包含你想處理之程式碼的資料夾中啟動 `copilot`。

預設情況下，`copilot` 會使用 Claude Sonnet 4.5。執行 `/model` 斜線指令即可從其他可用模型中選擇，包括 Claude Sonnet 4 與 GPT-5。

### 實驗模式

實驗模式可讓你使用仍在開發中的新功能。你可以透過以下方式啟用實驗模式：

- 以 `--experimental` 旗標啟動：`copilot --experimental`
- 在 CLI 內使用 `/experimental` 斜線指令

啟用後，此設定會持久化到你的 config 中，因此之後再次啟動時就不需要再加上 `--experimental` 旗標。

#### 實驗功能

- **Autopilot mode:** Autopilot 是一種新模式（按 `Shift+Tab` 可在各模式間切換），會鼓勵 agent 持續工作直到任務完成。

每次你向 GitHub Copilot CLI 提交 prompt，都會讓你每月的 premium requests 配額減少一次。關於 premium requests 的資訊，請參閱 [About premium requests](https://docs.github.com/copilot/managing-copilot/monitoring-usage-and-entitlements/about-premium-requests)。

若要進一步了解如何使用 GitHub Copilot CLI，請參閱[官方文件](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)。

## 🔧 設定 LSP Servers

GitHub Copilot CLI 支援 Language Server Protocol (LSP)，可提供更強的程式碼智慧功能。這項功能可帶來像是前往定義、懸停資訊與診斷等智慧型程式碼能力。

### 安裝 Language Servers

Copilot CLI 並未內建 LSP servers。你需要另外安裝它們。以設定 TypeScript 支援為例：

```bash
npm install -g typescript-language-server
```

對於其他語言，請安裝對應的 LSP server，並依照下方相同模式進行設定。

### 設定 LSP Servers

LSP servers 會透過專用的 LSP 設定檔進行設定。你可以在使用者層級或 repository 層級設定 LSP servers：

**使用者層級設定**（套用至所有專案）：
編輯 `~/.copilot/lsp-config.json`

**Repository 層級設定**（套用至特定專案）：
在 repository 根目錄建立 `.github/lsp.json`

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

### 檢視 LSP Server 狀態

在互動式工作階段中使用 `/lsp` 指令檢查已設定的 LSP servers，或直接檢視你的設定檔。

更多資訊請參閱 [changelog](./changelog.md)。

## 📢 回饋與參與

很高興你在 Copilot CLI 的早期階段加入我們。

我們開發速度很快。預期會有頻繁更新，請保持你的用戶端為最新版本，以取得最新功能與修正。

你的意見非常重要。歡迎在這個 repo 中開 issue、參與 Discussions，並在 CLI 中執行 `/feedback` 以提交保密的回饋問卷。
