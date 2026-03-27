# GitHub Copilot CLI

GitHub Copilot 的威力，現在就在你的終端機裡。

GitHub Copilot CLI 將 AI 驅動的程式設計協助直接帶到你的命令列，讓你透過自然語言對話來建置、除錯並理解程式碼。它採用與 GitHub Copilot coding agent 相同的代理式架構，在深度整合 GitHub 工作流程的同時提供智慧協助。

更多資訊請參閱[官方文件](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)。

![Copilot CLI 啟動畫面截圖](https://github.com/user-attachments/assets/f40aa23d-09dd-499e-9457-1d57d3368887)


## 🚀 簡介與總覽

我們正把 GitHub Copilot coding agent 的威力直接帶進你的終端機。透過 GitHub Copilot CLI，你可以在本機、同步地與理解你程式碼與 GitHub 情境的 AI 代理協作。

- **終端機原生開發：** 直接在命令列與 Copilot coding agent 協作，不需要切換上下文。
- **開箱即用的 GitHub 整合：** 使用自然語言存取你的儲存庫、議題與 PR，並以既有 GitHub 帳號完成驗證。
- **代理式能力：** 與能規劃並執行複雜任務的 AI 協作者一起建置、編輯、除錯與重構程式碼。
- **MCP 驅動的擴充性：** coding agent 預設內建 GitHub 的 MCP 伺服器，也支援自訂 MCP 伺服器以擴充能力。
- **完全可控：** 每個動作都先預覽再執行——未經你明確核可不會發生任何事。

我們仍在早期階段，但在你的回饋下，我們正快速迭代，讓 GitHub Copilot CLI 成為你在終端機裡最好的夥伴。

## 📦 快速開始

### 支援平台

- **Linux**
- **macOS**
- **Windows**

### 必要條件

- （Windows）**PowerShell** v6 或更新版本
- **有效的 Copilot 訂閱**。請參閱 [Copilot 方案](https://github.com/features/copilot/plans?ref_cta=Copilot+plans+signup&ref_loc=install-copilot-cli&ref_page=docs)。

如果你是透過組織或企業取得 GitHub Copilot 存取權，當組織擁有者或企業管理員在組織或企業設定中停用 GitHub Copilot CLI 時就無法使用。詳情請參閱[在你的組織中管理 GitHub Copilot 的政策與功能](http://docs.github.com/copilot/managing-copilot/managing-github-copilot-in-your-organization/managing-github-copilot-features-in-your-organization/managing-policies-for-copilot-in-your-organization)。

### 安裝

使用安裝腳本（macOS 與 Linux）：

```bash
curl -fsSL https://gh.io/copilot-install | bash
```

或

```bash
wget -qO- https://gh.io/copilot-install | bash
```

使用 `| sudo bash` 以 root 執行並安裝到 `/usr/local/bin`。

設定 `PREFIX` 以安裝到 `$PREFIX/bin/` 目錄。以 root 執行時預設為 `/usr/local`，以非 root 使用者執行時預設為 `$HOME/.local`。

設定 `VERSION` 以安裝指定版本。預設為最新版本。

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

首次啟動時，你會看到我們可愛的動畫橫幅！如果想再次看到此橫幅，請使用 `--banner` 旗標啟動 `copilot`。

如果你尚未登入 GitHub，系統會提示你使用 `/login` 斜線指令。輸入此指令並依畫面指示完成驗證。

#### 使用個人存取權杖（PAT）驗證

你也可以使用啟用「Copilot Requests」權限的細粒度 PAT 進行驗證。

1. 前往 https://github.com/settings/personal-access-tokens/new
2. 在「Permissions」底下，點選「add permissions」並選擇「Copilot Requests」
3. 產生你的權杖
4. 透過環境變數 `GH_TOKEN` 或 `GITHUB_TOKEN`（依優先順序）將權杖加入環境

### 使用 CLI

在包含你要處理程式碼的資料夾中啟動 `copilot`。

預設情況下，`copilot` 使用 Claude Sonnet 4.5。請執行 `/model` 斜線指令以選擇其他可用模型，包括 Claude Sonnet 4 與 GPT-5。

### 實驗模式

實驗模式可讓你使用仍在開發中的新功能。你可以透過以下方式啟用實驗模式：

- 以 `--experimental` 旗標啟動：`copilot --experimental`
- 在 CLI 內使用 `/experimental` 斜線指令

啟用後，這項設定會保存到你的組態中，因此之後啟動時就不需要再加 `--experimental` 旗標。

#### 實驗功能

- **Autopilot 模式：** Autopilot 是一種新模式（按 `Shift+Tab` 可在模式間切換），鼓勵代理持續工作直到任務完成。

每次你向 GitHub Copilot CLI 提交提示，你的每月進階請求配額就會減少一次。關於進階請求的資訊，請參閱[關於進階請求](https://docs.github.com/copilot/managing-copilot/monitoring-usage-and-entitlements/about-premium-requests)。

更多關於如何使用 GitHub Copilot CLI 的資訊，請參閱[官方文件](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)。

## 🔧 設定 LSP 伺服器

GitHub Copilot CLI 支援 Language Server Protocol (LSP) 以提升程式碼智慧功能。此功能可提供前往定義、游標懸停資訊與診斷等智慧功能。

### 安裝語言伺服器

Copilot CLI 不會內建 LSP 伺服器，需要自行安裝。例如，要設定 TypeScript 支援：

```bash
npm install -g typescript-language-server
```

其他語言請安裝對應的 LSP 伺服器，並依照下方範例的模式完成設定。

### 設定 LSP 伺服器

LSP 伺服器透過專用的 LSP 組態檔進行設定。你可以在使用者層級或儲存庫層級設定 LSP 伺服器：

**使用者層級設定**（適用於所有專案）：
編輯 `~/.copilot/lsp-config.json`

**儲存庫層級設定**（適用於特定專案）：
在儲存庫根目錄建立 `.github/lsp.json`

範例設定：

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

在互動式工作階段中使用 `/lsp` 指令檢查已設定的 LSP 伺服器，或直接檢視你的組態檔。

更多資訊請參閱[變更記錄](./changelog.md)。

## 📢 回饋與參與

我們很高興你在 Copilot CLI 旅程的早期就加入我們。

我們正快速建置，更新頻繁——請保持你的用戶端為最新版本，以取得最新功能與修正！

你的洞見非常寶貴！歡迎在此儲存庫開 issue、加入 Discussions，並在 CLI 中執行 `/feedback` 提交機密的回饋問卷！
