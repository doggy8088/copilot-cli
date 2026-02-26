# GitHub Copilot CLI

GitHub Copilot 的強大能力，現在就在你的終端機。

GitHub Copilot CLI 將 AI 驅動的程式設計輔助直接帶到你的命令列，讓你能透過自然語言對話來建置、除錯並理解程式碼。它使用與 GitHub Copilot coding agent 相同的代理式框架，在深度整合 GitHub 工作流程的同時提供智慧協助。

更多資訊請參閱[我們的官方文件](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)。

![Copilot CLI 啟動畫面的圖片](https://github.com/user-attachments/assets/f40aa23d-09dd-499e-9457-1d57d3368887)


## 🚀 簡介與概覽

我們把 GitHub Copilot coding agent 的強大能力直接帶到你的終端機。有了 GitHub Copilot CLI，你可以在本機、同步地與一位理解你的程式碼與 GitHub 情境的 AI 代理協作。

- **終端機原生開發：** 直接在命令列中與 Copilot coding agent 協作 — 無需在不同工具之間切換。
- **開箱即用的 GitHub 整合：** 使用自然語言存取你的儲存庫、Issue 與 Pull Request，並使用現有的 GitHub 帳號完成驗證。
- **代理能力：** 與可規劃並執行複雜任務的 AI 協作者一起建置、編輯、除錯與重構程式碼。
- **MCP 驅動的擴充性：** 代理預設隨附 GitHub 的 MCP 伺服器，並支援自訂 MCP 伺服器以擴充能力。
- **完全掌控：** 每個動作都會在執行前預覽 — 沒有你的明確核准就不會執行。

我們仍在早期階段，但在你的回饋之下，我們正快速迭代，讓 GitHub Copilot CLI 成為你終端機中最棒的夥伴。

## 📦 開始使用

### 支援平台

- **Linux**
- **macOS**
- **Windows**

### 前置需求

- （在 Windows 上）**PowerShell** v6 或更新版本
- 具有**有效的 Copilot 訂閱**。請參閱 [Copilot 方案](https://github.com/features/copilot/plans?ref_cta=Copilot+plans+signup&ref_loc=install-copilot-cli&ref_page=docs)。

如果你是透過組織或企業使用 GitHub Copilot，且你的組織擁有者或企業管理員在組織或企業設定中停用它，就無法使用 GitHub Copilot CLI。更多資訊請參閱[在你的組織中管理 GitHub Copilot 的政策與功能](http://docs.github.com/copilot/managing-copilot/managing-github-copilot-in-your-organization/managing-github-copilot-features-in-your-organization/managing-policies-for-copilot-in-your-organization)。

### 安裝

使用安裝腳本（macOS 與 Linux）：

```bash
curl -fsSL https://gh.io/copilot-install | bash
```

或

```bash
wget -qO- https://gh.io/copilot-install | bash
```

使用 `| sudo bash` 以 root 身分執行，並安裝到 `/usr/local/bin`。

將 `PREFIX` 設為安裝到 `$PREFIX/bin/` 目錄。以 root 執行時預設為 `/usr/local`，
非 root 使用者則預設為 `$HOME/.local`。

將 `VERSION` 設為安裝指定版本。預設為最新版本。

例如，要安裝 `v0.0.369` 到自訂目錄：

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

第一次啟動時，你會看到我們可愛的動畫橫幅！如果想再次看到這個橫幅，請使用 `--banner` 旗標啟動 `copilot`。

如果你尚未登入 GitHub，系統會提示你使用 `/login` 斜線指令。輸入該指令並依照畫面指示完成驗證。

#### 使用個人存取權杖（PAT）驗證

你也可以使用啟用「Copilot Requests」權限的細粒度 PAT 進行驗證。

1. 前往 https://github.com/settings/personal-access-tokens/new
2. 在「Permissions」底下點選「add permissions」，並選擇「Copilot Requests」
3. 產生你的權杖
4. 透過環境變數 `GH_TOKEN` 或 `GITHUB_TOKEN`（依優先順序）加入權杖

### 使用 CLI

在包含你要處理程式碼的資料夾中啟動 `copilot`。

預設情況下，`copilot` 使用 Claude Sonnet 4.5。執行 `/model` 斜線指令可從其他可用模型中選擇，包括 Claude Sonnet 4 與 GPT-5。

### 實驗模式

實驗模式可讓你使用仍在開發中的新功能。你可以透過以下方式啟用實驗模式：

- 使用 `--experimental` 旗標啟動：`copilot --experimental`
- 在 CLI 內使用 `/experimental` 斜線指令

啟用後，設定會持久化到你的設定中，因此後續啟動不再需要 `--experimental` 旗標。

#### 實驗功能

- **Autopilot 模式：** Autopilot 是一種新模式（按 `Shift+Tab` 可在模式間切換），它會鼓勵代理持續工作直到任務完成。

每次你向 GitHub Copilot CLI 提交提示，都會扣除一次每月的 premium request 配額。關於 premium requests 的資訊，請參閱[關於 premium requests](https://docs.github.com/copilot/managing-copilot/monitoring-usage-and-entitlements/about-premium-requests)。

如需更多使用 GitHub Copilot CLI 的資訊，請參閱[我們的官方文件](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)。

## 🔧 設定 LSP 伺服器

GitHub Copilot CLI 支援 Language Server Protocol（LSP）以強化程式碼智慧功能。這項功能提供 go-to-definition、hover 資訊與診斷等智慧化能力。

### 安裝語言伺服器

Copilot CLI 不會內建 LSP 伺服器，你需要自行安裝。例如，要啟用 TypeScript 支援：

```bash
npm install -g typescript-language-server
```

其他語言請安裝對應的 LSP 伺服器，並依照下方相同的方式進行設定。

### 設定 LSP 伺服器

LSP 伺服器透過專用的 LSP 設定檔進行設定。你可以在使用者層級或儲存庫層級設定 LSP 伺服器：

**使用者層級設定**（適用於所有專案）：
編輯 `~/.copilot/lsp-config.json`

**儲存庫層級設定**（適用於特定專案）：
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

### 檢視 LSP 伺服器狀態

在互動式會話中使用 `/lsp` 指令檢查已設定的 LSP 伺服器，或直接檢視你的設定檔。

如需更多資訊，請參閱[變更日誌](./changelog.md)。

## 📢 意見回饋與參與

我們很高興你能在 Copilot CLI 旅程的早期加入我們。

我們正在快速打造功能。請期待頻繁更新—也請保持你的用戶端為最新版本，以獲得最新功能與修正！

你的想法對我們非常重要！在這個 repo 開啟 issue、加入 Discussions，並在 CLI 中執行 `/feedback` 以提交保密的意見回饋問卷！
