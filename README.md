# GitHub Copilot CLI

GitHub Copilot 的強大能力，現在就在你的終端機中。

GitHub Copilot CLI 將 AI 驅動的程式設計協助直接帶到你的命令列，讓你能透過自然語言對話來建置、除錯並理解程式碼。它由與 GitHub 的 Copilot coding agent 相同的代理式框架驅動，在深度整合你的 GitHub 工作流程的同時提供智慧協助。

更多資訊請參閱 [我們的官方文件](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)。

![Copilot CLI 啟動畫面的圖片](https://github.com/user-attachments/assets/f40aa23d-09dd-499e-9457-1d57d3368887)


## 🚀 簡介與總覽

我們正將 GitHub Copilot coding agent 的能力直接帶進你的終端機。透過 GitHub Copilot CLI，你可以在本機與一個理解你的程式碼與 GitHub 情境的 AI 代理同步協作。

- **終端機原生開發：** 直接在命令列中與 Copilot coding agent 協作，不需要切換上下文。
- **開箱即用的 GitHub 整合：** 使用自然語言存取你的儲存庫、議題與拉取請求，全部都透過你現有的 GitHub 帳號完成驗證。
- **代理式能力：** 與可規劃並執行複雜任務的 AI 協作者一起建置、編輯、除錯與重構程式碼。
- **由 MCP 驅動的可擴充性：** 善用 coding agent 預設隨附 GitHub MCP 伺服器的能力，並透過支援自訂 MCP 伺服器來擴充功能。
- **完整控制權：** 每個動作在執行前都可先預覽，沒有任何事情會在未經你明確核准的情況下發生。

我們仍處於早期階段，但有了你的回饋，我們正快速迭代，讓 GitHub Copilot CLI 成為你終端機中最好的夥伴。

## 📦 開始使用

### 支援平台

- **Linux**
- **macOS**
- **Windows**

### 先決條件

- （在 Windows 上）**PowerShell** v6 或更新版本
- 一個**有效的 Copilot 訂閱**。請參閱 [Copilot 方案](https://github.com/features/copilot/plans?ref_cta=Copilot+plans+signup&ref_loc=install-copilot-cli&ref_page=docs)。

如果你是透過組織或企業取得 GitHub Copilot 的存取權，而你的組織擁有者或企業管理員已在組織或企業設定中停用 GitHub Copilot CLI，則你無法使用它。更多資訊請參閱 [在你的組織中管理 GitHub Copilot 的政策與功能](http://docs.github.com/copilot/managing-copilot/managing-github-copilot-in-your-organization/managing-github-copilot-features-in-your-organization/managing-policies-for-copilot-in-your-organization)。

### 安裝

使用安裝腳本安裝（macOS 與 Linux）：

```bash
curl -fsSL https://gh.io/copilot-install | bash
```

或者

```bash
wget -qO- https://gh.io/copilot-install | bash
```

使用 `| sudo bash` 以 root 身分執行，並安裝到 `/usr/local/bin`。

設定 `PREFIX` 可安裝到 `$PREFIX/bin/` 目錄。若以 root 執行，預設為 `/usr/local`；若以非 root 使用者執行，預設為 `$HOME/.local`。

設定 `VERSION` 可安裝特定版本。預設為最新版本。

例如，若要將版本 `v0.0.369` 安裝到自訂目錄：

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

第一次啟動時，你會看到我們可愛的動畫橫幅！如果你想再次看到這個橫幅，請使用 `--banner` 旗標啟動 `copilot`。

如果你目前尚未登入 GitHub，系統會提示你使用 `/login` 斜線指令。輸入這個指令並依照畫面上的說明完成驗證。

#### 使用 Personal Access Token (PAT) 進行驗證

你也可以使用已啟用 "Copilot Requests" 權限的細粒度 PAT 進行驗證。

1. 前往 https://github.com/settings/personal-access-tokens/new
2. 在 "Permissions" 下，點擊 "add permissions" 並選取 "Copilot Requests"
3. 產生你的 token
4. 透過環境變數 `GH_TOKEN` 或 `GITHUB_TOKEN`（依此優先順序）將 token 加入你的環境

### 使用 CLI

在包含你想處理程式碼的資料夾中啟動 `copilot`。

預設情況下，`copilot` 會使用 Claude Sonnet 4.5。執行 `/model` 斜線指令可從其他可用模型中選擇，包括 Claude Sonnet 4 與 GPT-5。

### 實驗模式

實驗模式可讓你使用仍在開發中的新功能。你可以透過以下方式啟用實驗模式：

- 使用 `--experimental` 旗標啟動：`copilot --experimental`
- 在 CLI 內使用 `/experimental` 斜線指令

啟用後，這項設定會保留在你的設定中，因此後續再次啟動時就不再需要 `--experimental` 旗標。

#### 實驗功能

- **Autopilot mode：** Autopilot 是一種新模式（按 `Shift+Tab` 可在模式間切換），會鼓勵代理持續工作直到任務完成。

每次你向 GitHub Copilot CLI 提交提示時，你每月的 premium requests 配額都會減少一次。關於 premium requests 的資訊，請參閱 [About premium requests](https://docs.github.com/copilot/managing-copilot/monitoring-usage-and-entitlements/about-premium-requests)。

若要了解更多關於如何使用 GitHub Copilot CLI 的資訊，請參閱 [我們的官方文件](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)。

## 🔧 設定 LSP 伺服器

GitHub Copilot CLI 支援 Language Server Protocol (LSP)，以增強程式碼智慧。這項功能提供像是跳至定義、懸停資訊與診斷等智慧程式碼功能。

### 安裝 Language Server

Copilot CLI 不會內建 LSP 伺服器。你需要另外安裝它們。以設定 TypeScript 支援為例：

```bash
npm install -g typescript-language-server
```

對於其他語言，請安裝對應的 LSP 伺服器，並依照下方顯示的相同模式進行設定。

### 設定 LSP 伺服器

LSP 伺服器是透過專用的 LSP 設定檔來設定的。你可以在使用者層級或儲存庫層級設定 LSP 伺服器：

**使用者層級設定**（套用到所有專案）：
編輯 `~/.copilot/lsp-config.json`

**儲存庫層級設定**（套用到特定專案）：
在你的儲存庫根目錄建立 `.github/lsp.json`

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

你可以在互動式會話中使用 `/lsp` 指令檢查已設定的 LSP 伺服器，或直接查看你的設定檔。

更多資訊請參閱 [changelog](./changelog.md)。

## 📢 回饋與參與

很高興你能在 Copilot CLI 的早期旅程中加入我們。

我們開發得很快。預期會有頻繁更新，請讓你的客戶端保持最新狀態，以取得最新功能與修正！

你的意見非常寶貴！請在這個儲存庫中開 issue、加入 Discussions，並從 CLI 執行 `/feedback` 來提交一份保密的回饋問卷！
