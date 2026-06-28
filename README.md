# GitHub Copilot CLI

GitHub Copilot 的強大能力，現在也進入你的終端機。

GitHub Copilot CLI 將 AI 驅動的程式設計協助直接帶到你的命令列，讓你能透過自然語言對話來建置、除錯並理解程式碼。它採用與 GitHub Copilot coding agent 相同的代理式執行框架，在與你的 GitHub 工作流程深度整合的同時，提供智慧化協助。

如需更多資訊，請參閱[官方文件](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)。

![Copilot CLI 啟動畫面的圖片](https://github.com/user-attachments/assets/f40aa23d-09dd-499e-9457-1d57d3368887)


## 🚀 簡介與總覽

我們將 GitHub Copilot coding agent 的能力直接帶進你的終端機。透過 GitHub Copilot CLI，你可以在本機以同步方式與一個理解你程式碼與 GitHub 情境的 AI 代理協作。

- **原生終端機開發：** 直接在命令列中使用 Copilot coding agent，無須切換上下文。
- **開箱即用的 GitHub 整合：** 使用自然語言存取你的儲存庫、議題與拉取請求，並沿用你現有的 GitHub 帳號完成驗證。
- **代理式能力：** 與可規劃並執行複雜任務的 AI 協作者一起建置、編輯、除錯與重構程式碼。
- **由 MCP 驅動的可擴充性：** coding agent 預設隨附 GitHub 的 MCP server，並支援自訂 MCP server 來擴充能力。
- **完整掌控：** 執行前可預覽每個動作，未經你明確同意，不會執行任何操作。

我們仍處於發展早期，但在你的回饋幫助下，我們正快速迭代，致力讓 GitHub Copilot CLI 成為終端機中最理想的協作夥伴。

## 📦 快速開始

### 支援平台

- **Linux**
- **macOS**
- **Windows**

### 先決條件

- （在 Windows 上）**PowerShell** v6 或更高版本
- 具備**有效的 Copilot 訂閱**。請參閱 [Copilot 方案](https://github.com/features/copilot/plans?ref_cta=Copilot+plans+signup&ref_loc=install-copilot-cli&ref_page=docs)。

如果你是透過組織或企業取得 GitHub Copilot 存取權，而你的組織擁有者或企業管理員已在組織或企業設定中停用 GitHub Copilot CLI，則你無法使用 GitHub Copilot CLI。詳情請參閱[在組織中管理 GitHub Copilot 的原則與功能](http://docs.github.com/copilot/managing-copilot/managing-github-copilot-in-your-organization/managing-github-copilot-features-in-your-organization/managing-policies-for-copilot-in-your-organization)。

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

設定 `PREFIX` 可安裝到 `$PREFIX/bin/` 目錄。以 root 執行時預設為 `/usr/local`，
以非 root 使用者執行時預設為 `$HOME/.local`。

設定 `VERSION` 可安裝指定版本。預設為最新版本。

例如，將版本 `v0.0.369` 安裝到自訂目錄：

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

首次啟動時，你會看到我們可愛的動畫橫幅！如果你想再次看到這個橫幅，可以在啟動 `copilot` 時加上 `--banner` 旗標。

如果你目前尚未登入 GitHub，系統會提示你使用 `/login` slash command。輸入此指令並依照畫面上的說明完成驗證。

#### 使用 Personal Access Token（PAT）驗證

你也可以使用已啟用「Copilot Requests」權限的細粒度 PAT 進行驗證。

1. 前往 https://github.com/settings/personal-access-tokens/new
2. 在「Permissions」下，點選「add permissions」並選擇「Copilot Requests」
3. 產生你的 token
4. 透過環境變數 `GH_TOKEN` 或 `GITHUB_TOKEN`（依優先順序）將 token 加入環境中

### 使用 CLI

在包含你想處理之程式碼的資料夾中啟動 `copilot`。

預設情況下，`copilot` 使用 Claude Sonnet 4.5。執行 `/model` slash command 可從其他可用模型中選擇，包括 Claude Sonnet 4 與 GPT-5。

### 實驗模式

實驗模式可讓你使用仍在開發中的新功能。你可以透過以下方式啟用實驗模式：

- 使用 `--experimental` 旗標啟動：`copilot --experimental`
- 在 CLI 內使用 `/experimental` slash command

啟用後，此設定會保存在你的 config 中，因此後續啟動時不再需要 `--experimental` 旗標。

#### 實驗功能

- **Autopilot 模式：** Autopilot 是一種新模式（按 `Shift+Tab` 可循環切換模式），會鼓勵代理持續工作直到任務完成。

每次你向 GitHub Copilot CLI 提交 prompt，你每月的 premium requests 額度都會減少一次。如需 premium requests 的資訊，請參閱[關於 premium requests](https://docs.github.com/copilot/managing-copilot/monitoring-usage-and-entitlements/about-premium-requests)。

如需更多關於如何使用 GitHub Copilot CLI 的資訊，請參閱[官方文件](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)。

## 🔧 設定 LSP Servers

GitHub Copilot CLI 支援 Language Server Protocol（LSP），以提供更強的程式碼智慧功能。此功能可提供前往定義、懸停資訊與診斷等智慧程式碼能力。

### 安裝 Language Servers

Copilot CLI 不會內建 LSP server。你需要另外安裝。例如，若要設定 TypeScript 支援：

```bash
npm install -g typescript-language-server
```

對於其他語言，請安裝對應的 LSP server，並依照下方相同模式完成設定。

### 設定 LSP Servers

LSP server 透過專用的 LSP 設定檔進行設定。你可以在使用者層級或儲存庫層級設定 LSP server：

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

### 查看 LSP Server 狀態

可在互動式工作階段中使用 `/lsp` 指令檢查已設定的 LSP server，或直接查看你的設定檔。

如需更多資訊，請參閱 [changelog](./changelog.md)。

## 📢 回饋與參與

很高興你在 Copilot CLI 的早期階段就加入我們。

我們正在快速開發中。請預期會有頻繁更新，並請保持你的客戶端為最新版本，以獲得最新功能與修正！

你的意見非常重要！歡迎在這個 repo 中開啟 issue、加入 Discussions，並從 CLI 執行 `/feedback` 提交一份保密的回饋問卷！
