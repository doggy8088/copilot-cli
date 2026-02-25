# GitHub Copilot CLI

GitHub Copilot 的力量，現在就在你的終端機。

GitHub Copilot CLI 將 AI 驅動的程式碼輔助直接帶到你的命令列，讓你能透過自然語言對話來建置、除錯並理解程式碼。它由與 GitHub 的 Copilot 編碼代理相同的代理式框架驅動，在深度整合你的 GitHub 工作流程的同時提供智慧協助。

更多資訊請參考[官方文件](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)。

![Copilot CLI 啟動畫面的圖片](https://github.com/user-attachments/assets/f40aa23d-09dd-499e-9457-1d57d3368887)


## 🚀 介紹與總覽

我們把 GitHub Copilot 編碼代理的力量直接帶到你的終端機。透過 GitHub Copilot CLI，你可以在本機與理解你的程式碼與 GitHub 情境的 AI 代理同步協作。

- **原生終端開發：** 直接在命令列與 Copilot 編碼代理協作 — 無需切換情境。
- **開箱即用的 GitHub 整合：** 使用自然語言存取你的儲存庫、議題與 Pull Request，全部以現有 GitHub 帳號完成驗證。
- **代理式能力：** 與能規劃並執行複雜任務的 AI 夥伴一起建置、編輯、除錯與重構程式碼。
- **MCP 驅動的可擴充性：** 編碼代理預設內建 GitHub 的 MCP 伺服器，也支援自訂 MCP 伺服器來擴充能力。
- **完全掌控：** 每個動作都會在執行前預覽 — 未經明確核准不會有任何動作。

我們仍處於早期階段，但在你的回饋下，我們正快速迭代，讓 GitHub Copilot CLI 成為你終端機中最好的夥伴。

## 📦 入門

### 支援平台

- **Linux**
- **macOS**
- **Windows**

### 先決條件

- （Windows）**PowerShell** v6 或以上
- 有效的 **Copilot 訂閱**。請參考 [Copilot 方案](https://github.com/features/copilot/plans?ref_cta=Copilot+plans+signup&ref_loc=install-copilot-cli&ref_page=docs)。

如果你透過組織或企業取得 GitHub Copilot 存取權，當組織擁有者或企業管理員在組織或企業設定中停用時，你將無法使用 GitHub Copilot CLI。更多資訊請參考[在組織中管理 GitHub Copilot 的政策與功能](http://docs.github.com/copilot/managing-copilot/managing-github-copilot-in-your-organization/managing-github-copilot-features-in-your-organization/managing-policies-for-copilot-in-your-organization)。

### 安裝

使用安裝腳本（macOS 與 Linux）：

```bash
curl -fsSL https://gh.io/copilot-install | bash
```

或

```bash
wget -qO- https://gh.io/copilot-install | bash
```

使用 `| sudo bash` 以 root 身分執行並安裝到 `/usr/local/bin`。

將 `PREFIX` 設為安裝到 `$PREFIX/bin/` 目錄。以 root 身分執行時預設為 `/usr/local`，以非 root 使用者執行時預設為 `$HOME/.local`。

將 `VERSION` 設為安裝特定版本。預設為最新版本。

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

首次啟動時，你會看到可愛的動畫橫幅！如果你想再次看到這個橫幅，使用 `--banner` 旗標啟動 `copilot`。

如果你目前未登入 GitHub，系統會提示你使用 `/login` 斜線指令。輸入該指令並依照畫面上的步驟完成驗證。

#### 使用個人存取權杖（PAT）驗證

你也可以使用已啟用「Copilot Requests」權限的細粒度 PAT 進行驗證。

1. 前往 https://github.com/settings/personal-access-tokens/new
2. 在「Permissions」下，點選「add permissions」並選擇「Copilot Requests」
3. 產生你的權杖
4. 透過環境變數 `GH_TOKEN` 或 `GITHUB_TOKEN` 將權杖加入環境（依優先順序）

### 使用 CLI

在包含你要處理程式碼的資料夾中啟動 `copilot`。

預設情況下，`copilot` 使用 Claude Sonnet 4.5。可透過 `/model` 斜線指令選擇其他可用模型，包括 Claude Sonnet 4 與 GPT-5。

### 實驗模式

實驗模式可讓你使用仍在開發中的新功能。你可以透過以下方式啟用實驗模式：

- 使用 `--experimental` 旗標啟動：`copilot --experimental`
- 在 CLI 內使用 `/experimental` 斜線指令

啟用後設定會寫入你的設定檔，因此之後啟動不再需要 `--experimental` 旗標。

#### 實驗功能

- **Autopilot mode：** Autopilot 是一個新模式（按 `Shift+Tab` 可切換模式），鼓勵代理持續工作直到任務完成。

每次你在 GitHub Copilot CLI 提交提示時，你的每月進階請求配額都會減少 1。關於進階請求的資訊，請參考[進階請求說明](https://docs.github.com/copilot/managing-copilot/monitoring-usage-and-entitlements/about-premium-requests)。

更多關於如何使用 GitHub Copilot CLI 的資訊，請參考[官方文件](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)。

## 🔧 設定 LSP 伺服器

GitHub Copilot CLI 支援語言伺服器協定（LSP）以增強程式碼智慧。此功能提供如「跳轉到定義」、懸浮資訊與診斷等智慧化程式碼能力。

### 安裝語言伺服器

Copilot CLI 不會內建 LSP 伺服器，你需要另外安裝。例如，要設定 TypeScript 支援：

```bash
npm install -g typescript-language-server
```

其他語言則安裝相對應的 LSP 伺服器，並依照下方相同模式進行設定。

### 設定 LSP 伺服器

LSP 伺服器透過專用的 LSP 設定檔進行設定。你可以在使用者層級或儲存庫層級設定 LSP 伺服器：

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

在互動式會話中使用 `/lsp` 指令查看已設定的 LSP 伺服器，或直接檢視設定檔。

更多資訊請參考[變更日誌](./changelog.md)。

## 📢 回饋與參與

很高興你在 Copilot CLI 的早期旅程中加入我們。

我們正在快速建置。預期會有頻繁更新--請保持用戶端為最新，以取得最新功能與修正！

你的洞見非常珍貴！請在這個儲存庫開啟 issue、加入 Discussions，並在 CLI 中執行 `/feedback` 以提交保密的回饋調查！
