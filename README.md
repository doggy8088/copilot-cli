# GitHub Copilot CLI

GitHub Copilot 的強大能力，現在來到你的終端機。

GitHub Copilot CLI 直接將 AI 驅動的程式設計協助帶到你的命令列，讓你能透過自然語言對話來建置、除錯與理解程式碼。它採用與 GitHub Copilot coding agent 相同的代理式執行框架，在與 GitHub 工作流程深度整合的同時，提供智慧協助。

如需更多資訊，請參閱 [我們的官方文件](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)。

![Image of the splash screen for the Copilot CLI](https://github.com/user-attachments/assets/f40aa23d-09dd-499e-9457-1d57d3368887)


## 🚀 介紹與概覽

我們正把 GitHub Copilot coding agent 的能力直接帶進你的終端機。有了 GitHub Copilot CLI，你可以在本機以同步方式與了解你的程式碼與 GitHub 情境的 AI 代理協作。

- **原生終端機開發：** 直接在命令列中使用 Copilot coding agent，無需切換工作情境。
- **開箱即用的 GitHub 整合：** 使用自然語言存取你的儲存庫、issue 與 pull request，並直接沿用你現有的 GitHub 帳號完成驗證。
- **代理式能力：** 與能規劃並執行複雜任務的 AI 協作者一起建置、編輯、除錯與重構程式碼。
- **由 MCP 驅動的可擴充性：** coding agent 預設隨附 GitHub 的 MCP server，並支援自訂 MCP server 來擴充能力。
- **完整掌控：** 每個動作都會先預覽再執行，未經你明確同意，不會進行任何操作。

我們仍處於早期階段，但在你的回饋協助下，我們正快速迭代，讓 GitHub Copilot CLI 成為終端機中最好的協作夥伴。

## 📦 快速開始

### 支援平台

- **Linux**
- **macOS**
- **Windows**

### 先決條件

- （在 Windows 上）**PowerShell** v6 或更新版本
- 具備**有效的 Copilot 訂閱**。請參閱 [Copilot plans](https://github.com/features/copilot/plans?ref_cta=Copilot+plans+signup&ref_loc=install-copilot-cli&ref_page=docs)。

如果你是透過組織或企業存取 GitHub Copilot，而你的組織擁有者或企業管理員已在組織或企業設定中停用 GitHub Copilot CLI，則你將無法使用 GitHub Copilot CLI。如需更多資訊，請參閱 [Managing policies and features for GitHub Copilot in your organization](http://docs.github.com/copilot/managing-copilot/managing-github-copilot-in-your-organization/managing-github-copilot-features-in-your-organization/managing-policies-for-copilot-in-your-organization)。

### 安裝

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

首次啟動時，你會看到我們可愛的動畫橫幅！如果你想再次顯示這個橫幅，請在啟動 `copilot` 時加上 `--banner` 旗標。

如果你目前尚未登入 GitHub，系統會提示你使用 `/login` slash command。輸入此指令並依照畫面上的說明完成驗證。

#### 使用個人存取權杖（PAT）進行驗證

你也可以使用已啟用 "Copilot Requests" 權限的細粒度 PAT 進行驗證。

1. 前往 https://github.com/settings/personal-access-tokens/new
2. 在 "Permissions" 下，點擊 "add permissions" 並選取 "Copilot Requests"
3. 產生你的權杖
4. 透過環境變數 `GH_TOKEN` 或 `GITHUB_TOKEN` 將權杖加入環境中（依優先順序排列）

### 使用 CLI

在包含你想處理之程式碼的資料夾中啟動 `copilot`。

預設情況下，`copilot` 會使用 Claude Sonnet 4.5。執行 `/model` slash command 可從其他可用模型中選擇，包括 Claude Sonnet 4 與 GPT-5。

### 實驗模式

實驗模式可讓你使用仍在開發中的新功能。你可以透過以下方式啟用實驗模式：

- 使用 `--experimental` 旗標啟動：`copilot --experimental`
- 在 CLI 中使用 `/experimental` slash command

啟用後，這項設定會持久保存於你的設定中，因此後續啟動時就不再需要 `--experimental` 旗標。

#### 實驗功能

- **Autopilot mode：** Autopilot 是一種新模式（按 `Shift+Tab` 可循環切換模式），會鼓勵代理持續工作直到任務完成。

你每次向 GitHub Copilot CLI 提交提示時，每月的 premium requests 配額都會減少一次。如需 premium requests 的資訊，請參閱 [About premium requests](https://docs.github.com/copilot/managing-copilot/monitoring-usage-and-entitlements/about-premium-requests)。

如需更多關於如何使用 GitHub Copilot CLI 的資訊，請參閱 [我們的官方文件](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)。

## 🔧 設定 LSP Servers

GitHub Copilot CLI 支援 Language Server Protocol（LSP），以提供更強的程式碼智慧功能。此功能可提供像是前往定義、hover 資訊與診斷等智慧程式碼功能。

### 安裝 Language Servers

Copilot CLI 不會內建 LSP server。你需要另外安裝。例如，若要設定 TypeScript 支援：

```bash
npm install -g typescript-language-server
```

對於其他語言，請安裝對應的 LSP server，並依照下方示範的相同模式完成設定。

### 設定 LSP Servers

LSP server 透過專用的 LSP 設定檔來設定。你可以在使用者層級或儲存庫層級設定 LSP server：

**使用者層級設定**（套用至所有專案）：
編輯 `~/.copilot/lsp-config.json`

**儲存庫層級設定**（套用至特定專案）：
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

可在互動式工作階段中使用 `/lsp` 指令檢查已設定的 LSP server，或直接查看你的設定檔。

如需更多資訊，請參閱 [changelog](./changelog.md)。

## 📢 回饋與參與

我們很高興你能在 Copilot CLI 的早期旅程中加入我們。

我們的開發速度很快。預期會有頻繁更新，請讓你的客戶端保持最新，以取得最新功能與修正。

你的見解非常重要。歡迎在此儲存庫開啟 issue、加入 Discussions，並在 CLI 中執行 `/feedback` 來提交一份保密的回饋問卷！
