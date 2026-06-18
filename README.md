# GitHub Copilot CLI

GitHub Copilot 的強大能力，現在就在你的終端機中。

GitHub Copilot CLI 將 AI 驅動的程式開發協助直接帶到你的命令列中，讓你能透過自然語言對話來建置、除錯並理解程式碼。它採用與 GitHub Copilot 編碼代理相同的 agentic harness，能在與 GitHub 工作流程深度整合的同時，提供智慧協助。

更多資訊請參閱[官方文件](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)。

![Copilot CLI 啟動畫面的圖片](https://github.com/user-attachments/assets/f40aa23d-09dd-499e-9457-1d57d3368887)


## 🚀 介紹與總覽

我們將 GitHub Copilot 編碼代理的能力直接帶到你的終端機。使用 GitHub Copilot CLI，你可以在本機以同步方式與了解你的程式碼和 GitHub 情境的 AI 代理協作。

- **原生終端機開發體驗：** 直接在命令列中使用 Copilot 編碼代理，無需切換工作情境。
- **開箱即用的 GitHub 整合：** 使用自然語言存取你的儲存庫、議題與拉取請求，並直接沿用你現有的 GitHub 帳號完成驗證。
- **Agentic 能力：** 與可規劃並執行複雜任務的 AI 協作夥伴一起建置、編輯、除錯與重構程式碼。
- **由 MCP 驅動的可擴充性：** 編碼代理預設內建 GitHub 的 MCP server，並支援自訂 MCP server 以擴充能力。
- **完整控制權：** 每個動作都能先預覽再執行，未經你明確批准，不會發生任何事。

我們仍處於早期階段，但在你的回饋幫助下，我們正快速迭代，讓 GitHub Copilot CLI 成為你終端機中最理想的協作夥伴。

## 📦 開始使用

### 支援平台

- **Linux**
- **macOS**
- **Windows**

### 先決條件

- (Windows 上) **PowerShell** v6 或以上版本
- 具備**有效的 Copilot 訂閱**。請參閱 [Copilot 方案](https://github.com/features/copilot/plans?ref_cta=Copilot+plans+signup&ref_loc=install-copilot-cli&ref_page=docs)。

如果你是透過組織或企業取得 GitHub Copilot 使用權，而你的組織擁有者或企業管理員已在組織或企業設定中停用 GitHub Copilot CLI，則你將無法使用 GitHub Copilot CLI。更多資訊請參閱[在組織中管理 GitHub Copilot 的政策與功能](http://docs.github.com/copilot/managing-copilot/managing-github-copilot-in-your-organization/managing-github-copilot-features-in-your-organization/managing-policies-for-copilot-in-your-organization)。

### 安裝

使用安裝腳本安裝 (macOS 與 Linux)：

```bash
curl -fsSL https://gh.io/copilot-install | bash
```

或

```bash
wget -qO- https://gh.io/copilot-install | bash
```

使用 `| sudo bash` 可用 root 身分執行，並安裝到 `/usr/local/bin`。

設定 `PREFIX` 可安裝到 `$PREFIX/bin/` 目錄。以 root 身分執行時預設為 `/usr/local`，以非 root 使用者執行時預設為 `$HOME/.local`。

設定 `VERSION` 可安裝指定版本。預設為最新版本。

例如，將 `v0.0.369` 安裝到自訂目錄：

```bash
curl -fsSL https://gh.io/copilot-install | VERSION="v0.0.369" PREFIX="$HOME/custom" bash
```

使用 [Homebrew](https://formulae.brew.sh/cask/copilot-cli) 安裝 (macOS 與 Linux)：

```bash
brew install copilot-cli
```

```bash
brew install copilot-cli@prerelease
```


使用 [WinGet](https://github.com/microsoft/winget-cli) 安裝 (Windows)：

```bash
winget install GitHub.Copilot
```

```bash
winget install GitHub.Copilot.Prerelease
```


使用 [npm](https://www.npmjs.com/package/@github/copilot) 安裝 (macOS、Linux 與 Windows)：

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

第一次啟動時，你會看到我們可愛的動畫橫幅。如果你想再次看到這個橫幅，可使用 `--banner` 旗標啟動 `copilot`。

如果你目前尚未登入 GitHub，系統會提示你使用 `/login` slash command。輸入此指令並依照畫面上的說明完成驗證。

#### 使用 Personal Access Token (PAT) 驗證

你也可以使用已啟用 "Copilot Requests" 權限的細粒度 PAT 來驗證。

1. 前往 https://github.com/settings/personal-access-tokens/new
2. 在 "Permissions" 下，點選 "add permissions" 並選擇 "Copilot Requests"
3. 產生你的 token
4. 透過環境變數 `GH_TOKEN` 或 `GITHUB_TOKEN` (依此優先順序) 將 token 加入你的環境

### 使用 CLI

在包含你想處理之程式碼的資料夾中啟動 `copilot`。

預設情況下，`copilot` 使用 Claude Sonnet 4.5。執行 `/model` slash command 可從其他可用模型中選擇，包括 Claude Sonnet 4 與 GPT-5。

### Experimental Mode

Experimental mode 可讓你使用仍在開發中的新功能。你可以透過以下方式啟用 experimental mode：

- 使用 `--experimental` 旗標啟動：`copilot --experimental`
- 在 CLI 內使用 `/experimental` slash command

啟用後，該設定會持久化寫入你的 config，因此之後再次啟動時不再需要 `--experimental` 旗標。

#### Experimental Features

- **Autopilot mode：** Autopilot 是一種新模式 (按 `Shift+Tab` 可在模式間切換)，會鼓勵代理持續工作直到任務完成。

每次你向 GitHub Copilot CLI 提交提示時，每月的 premium requests 額度就會減少一次。關於 premium requests 的資訊，請參閱[關於 premium requests](https://docs.github.com/copilot/managing-copilot/monitoring-usage-and-entitlements/about-premium-requests)。

更多關於如何使用 GitHub Copilot CLI 的資訊，請參閱[官方文件](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)。

## 🔧 設定 LSP Servers

GitHub Copilot CLI 支援 Language Server Protocol (LSP)，可提供更強的程式碼智慧能力。這項功能可帶來跳至定義、懸停資訊與診斷等智慧程式碼功能。

### 安裝 Language Servers

Copilot CLI 不內建 LSP server。你需要另外安裝。例如，若要設定 TypeScript 支援：

```bash
npm install -g typescript-language-server
```

若使用其他語言，請安裝對應的 LSP server，並依照下方相同模式進行設定。

### 設定 LSP Servers

LSP server 透過專用的 LSP 設定檔來設定。你可以在使用者層級或儲存庫層級設定 LSP server：

**使用者層級設定** (套用至所有專案)：
編輯 `~/.copilot/lsp-config.json`

**儲存庫層級設定** (套用至特定專案)：
在儲存庫根目錄建立 `.github/lsp.json`

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

在互動式工作階段中使用 `/lsp` 指令檢查已設定的 LSP server，或直接查看你的設定檔。

更多資訊請參閱 [changelog](./changelog.md)。

## 📢 意見回饋與參與

很高興你在 Copilot CLI 的早期階段就加入我們。

我們正在快速開發。預期會有頻繁更新，請保持你的客戶端為最新版本，以取得最新功能與修正。

你的洞見非常重要。歡迎在這個儲存庫開 issue、加入 Discussions，並在 CLI 中執行 `/feedback` 提交一份保密的回饋問卷。
