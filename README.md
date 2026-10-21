# GitHub Copilot CLI

GitHub Copilot 的強大能力，現在來到你的終端機。

GitHub Copilot CLI 將 AI 驅動的程式設計協助直接帶到你的命令列，讓你能透過自然語言對話來建置、除錯與理解程式碼。它由與 GitHub 的 Copilot coding agent 相同的 agentic harness 驅動，在深度整合 GitHub 工作流程的同時，也提供智慧協助。

更多資訊請參閱[官方文件](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)。

![Copilot CLI 啟動畫面的圖片](https://github.com/user-attachments/assets/f40aa23d-09dd-499e-9457-1d57d3368887)


## 🚀 簡介與總覽

我們正把 GitHub Copilot coding agent 的強大能力直接帶到你的終端機。使用 GitHub Copilot CLI，你可以在本機與一個理解你的程式碼與 GitHub 情境的 AI agent 同步協作。

- **原生終端機開發：** 直接在命令列中與 Copilot coding agent 協作——不需要切換上下文。
- **開箱即用的 GitHub 整合：** 使用自然語言存取你的儲存庫、議題與拉取請求，並以你現有的 GitHub 帳號完成驗證。
- **Agentic 能力：** 與能規劃並執行複雜任務的 AI 協作者一起建置、編輯、除錯與重構程式碼。
- **由 MCP 驅動的可擴充性：** 利用 coding agent 預設隨附 GitHub 的 MCP server，並支援自訂 MCP servers 來擴充能力。
- **完整掌控：** 執行前預覽每一個動作——沒有你的明確核准，任何事情都不會發生。

我們仍處於早期階段，但在你的回饋協助下，我們正快速迭代，致力讓 GitHub Copilot CLI 成為終端機中最好的夥伴。

## 📦 開始使用

### 支援平台

- **Linux**
- **macOS**
- **Windows**

### 先決條件

- （Windows）**PowerShell** v6 或更新版本
- **有效的 Copilot 訂閱**。請參閱 [Copilot plans](https://github.com/features/copilot/plans?ref_cta=Copilot+plans+signup&ref_loc=install-copilot-cli&ref_page=docs)。

如果你是透過組織或企業取得 GitHub Copilot 的存取權，而你的組織擁有者或企業管理員已在組織或企業設定中停用 GitHub Copilot CLI，則你無法使用 GitHub Copilot CLI。更多資訊請參閱 [Managing policies and features for GitHub Copilot in your organization](http://docs.github.com/copilot/managing-copilot/managing-github-copilot-in-your-organization/managing-github-copilot-features-in-your-organization/managing-policies-for-copilot-in-your-organization)。

### 安裝

使用安裝腳本安裝（macOS 與 Linux）：

```bash
curl -fsSL https://gh.io/copilot-install | bash
```

或

```bash
wget -qO- https://gh.io/copilot-install | bash
```

可使用 `| sudo bash` 以 root 身分執行，並安裝到 `/usr/local/bin`。

設定 `PREFIX` 可安裝到 `$PREFIX/bin/` 目錄。以 root 身分執行時，預設為 `/usr/local`；以非 root 使用者執行時，預設為 `$HOME/.local`。

設定 `VERSION` 可安裝特定版本。預設為最新版本。

例如，若要將 `v0.0.369` 安裝到自訂目錄：

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

第一次啟動時，你會看到我們可愛的動畫橫幅！如果你想再次看到這個橫幅，請在啟動 `copilot` 時加上 `--banner` 旗標。

若你目前尚未登入 GitHub，系統會提示你使用 `/login` 斜線指令。輸入此指令並依照畫面上的說明完成驗證。

#### 使用個人存取權杖（PAT）驗證

你也可以使用已啟用「Copilot Requests」權限的細粒度 PAT 進行驗證。

1. 前往 https://github.com/settings/personal-access-tokens/new
2. 在「Permissions」下，按一下「add permissions」，並選擇「Copilot Requests」
3. 產生你的 token
4. 透過環境變數 `GH_TOKEN` 或 `GITHUB_TOKEN`（依優先順序）將 token 加入你的環境

### 使用 CLI

在包含你想操作程式碼的資料夾中啟動 `copilot`。

預設情況下，`copilot` 使用 Claude Sonnet 4.5。執行 `/model` 斜線指令可從其他可用模型中選擇，包括 Claude Sonnet 4 與 GPT-5。

### 實驗模式

實驗模式可讓你使用仍在開發中的新功能。你可以透過以下方式啟用實驗模式：

- 以 `--experimental` 旗標啟動：`copilot --experimental`
- 在 CLI 內使用 `/experimental` 斜線指令

啟用後，此設定會持久化寫入你的設定中，因此之後再次啟動時就不再需要 `--experimental` 旗標。

#### 實驗功能

- **Autopilot 模式：** Autopilot 是一種新模式（按 `Shift+Tab` 可在模式間切換），會鼓勵 agent 持續工作直到任務完成。

每當你向 GitHub Copilot CLI 提交一個 prompt，你每月的 premium requests 配額就會減少一次。關於 premium requests 的資訊，請參閱 [About premium requests](https://docs.github.com/copilot/managing-copilot/monitoring-usage-and-entitlements/about-premium-requests)。

關於如何使用 GitHub Copilot CLI 的更多資訊，請參閱[官方文件](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)。

## 🔧 設定 LSP Servers

GitHub Copilot CLI 支援 Language Server Protocol（LSP），可提供更強大的程式碼智慧功能。此功能提供像是前往定義、懸停資訊與診斷等智慧程式碼能力。

### 安裝 Language Servers

Copilot CLI 不會內建 LSP servers。你需要另外安裝它們。例如，若要設定 TypeScript 支援：

```bash
npm install -g typescript-language-server
```

對於其他語言，請安裝對應的 LSP server，並依照下方示範的相同模式進行設定。

### 設定 LSP Servers

LSP servers 透過專用的 LSP 設定檔進行設定。你可以在使用者層級或儲存庫層級設定 LSP servers：

**使用者層級設定**（套用至所有專案）：
編輯 `~/.copilot/lsp-config.json`

**儲存庫層級設定**（套用至特定專案）：
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

### 檢視 LSP Server 狀態

使用互動式工作階段中的 `/lsp` 指令檢查已設定的 LSP servers，或直接檢視你的設定檔。

更多資訊請參閱 [changelog](./changelog.md)。

## 📢 回饋與參與

很高興你在 Copilot CLI 的旅程早期就加入我們。

我們正快速建置。預期會有頻繁更新——請讓你的用戶端保持最新，以取得最新功能與修正！

你的洞見非常寶貴！請在此儲存庫開啟 issue、加入 Discussions，並在 CLI 中執行 `/feedback` 以提交一份保密的回饋問卷！
