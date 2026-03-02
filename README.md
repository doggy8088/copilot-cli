# GitHub Copilot CLI

GitHub Copilot 的強大能力，現在就在你的終端機。

GitHub Copilot CLI 將 AI 驅動的程式設計輔助直接帶到你的命令列，讓你能透過自然語言對話來建構、除錯與理解程式碼。它採用與 GitHub 的 Copilot coding agent 相同的代理式框架，在與你的 GitHub 工作流程深度整合的同時提供智慧協助。

詳情請參見[官方文件](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)。

![Copilot CLI 啟動畫面的圖片](https://github.com/user-attachments/assets/f40aa23d-09dd-499e-9457-1d57d3368887)


## 🚀 介紹與概覽

我們正把 GitHub Copilot coding agent 的強大能力直接帶到你的終端機。有了 GitHub Copilot CLI，你可以在本機與 AI 代理同步協作，並且它理解你的程式碼與 GitHub 內容。

- **終端機原生開發：** 直接在命令列中與 Copilot coding agent 協作——不需要切換上下文。
- **開箱即用的 GitHub 整合：** 使用自然語言存取你的儲存庫、issues 與 pull requests，全程使用你現有的 GitHub 帳號完成驗證。
- **代理式能力：** 與能規劃並執行複雜任務的 AI 協作者一起建置、編輯、除錯與重構程式碼。
- **MCP 驅動的可擴充性：** 受益於 coding agent 預設隨附 GitHub 的 MCP 伺服器，並支援自訂 MCP 伺服器來擴充能力。
- **完全掌控：** 在執行前預覽每個動作——沒有你的明確同意就不會發生任何事。

我們仍在早期階段，但有了你的回饋，我們正在快速迭代，致力於讓 GitHub Copilot CLI 成為你終端機中的最佳夥伴。

## 📦 入門

### 支援平台

- **Linux**
- **macOS**
- **Windows**

### 先決條件

- （Windows）**PowerShell** v6 以上
- 具備**有效的 Copilot 訂閱**。請參見[Copilot 方案](https://github.com/features/copilot/plans?ref_cta=Copilot+plans+signup&ref_loc=install-copilot-cli&ref_page=docs)。

如果你是透過組織或企業取得 GitHub Copilot 的存取權，且你的組織擁有者或企業管理員在組織或企業設定中停用了它，你將無法使用 GitHub Copilot CLI。詳情請見[在你的組織中管理 GitHub Copilot 的政策與功能](http://docs.github.com/copilot/managing-copilot/managing-github-copilot-in-your-organization/managing-github-copilot-features-in-your-organization/managing-policies-for-copilot-in-your-organization)。

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

設定 `PREFIX` 以安裝到 `$PREFIX/bin/` 目錄。以 root 執行時預設為 `/usr/local`，非 root 使用者則預設為 `$HOME/.local`。

設定 `VERSION` 以安裝指定版本。預設為最新版本。

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

第一次啟動時，你會看到可愛的動畫橫幅！若想再次看到它，請使用 `--banner` 旗標啟動 `copilot`。

如果你尚未登入 GitHub，系統會提示你使用 `/login` 斜線指令。輸入此指令並依畫面指示完成驗證。

#### 使用 Personal Access Token (PAT) 驗證

你也可以使用啟用「Copilot Requests」權限的細粒度 PAT 進行驗證。

1. 前往 https://github.com/settings/personal-access-tokens/new
2. 在「Permissions」下，點擊「add permissions」並選擇「Copilot Requests」
3. 產生你的 token
4. 透過環境變數 `GH_TOKEN` 或 `GITHUB_TOKEN` 將 token 加入環境（依優先順序）

### 使用 CLI

在包含你想處理程式碼的資料夾中啟動 `copilot`。

預設情況下，`copilot` 會使用 Claude Sonnet 4.5。執行 `/model` 斜線指令可選擇其他可用模型，包括 Claude Sonnet 4 與 GPT-5。

### 實驗模式

實驗模式可讓你使用仍在開發中的新功能。你可以透過以下方式啟用實驗模式：

- 使用 `--experimental` 旗標啟動：`copilot --experimental`
- 在 CLI 內使用 `/experimental` 斜線指令

啟用後，這個設定會保存到你的設定檔中，因此之後啟動時不再需要 `--experimental` 旗標。

#### 實驗性功能

- **Autopilot 模式：** Autopilot 是一種新模式（按 `Shift+Tab` 可在模式間切換），會鼓勵代理持續工作直到任務完成。

每次你向 GitHub Copilot CLI 提交提示，你的每月 premium request 配額會減少 1。關於 premium requests，請參見[關於 premium requests](https://docs.github.com/copilot/managing-copilot/monitoring-usage-and-entitlements/about-premium-requests)。

更多 GitHub Copilot CLI 使用方式，請參見[官方文件](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)。

## 🔧 設定 LSP 伺服器

GitHub Copilot CLI 支援 Language Server Protocol (LSP)，以增強程式碼智慧功能。這項功能提供像是跳轉到定義、滑鼠懸停資訊與診斷等智慧程式碼能力。

### 安裝語言伺服器

Copilot CLI 不會隨附 LSP 伺服器，你需要另外安裝。例如，要設定 TypeScript 支援：

```bash
npm install -g typescript-language-server
```

其他語言請安裝對應的 LSP 伺服器，並依照下方相同的模式進行設定。

### 設定 LSP 伺服器

LSP 伺服器透過專用的 LSP 設定檔進行設定。你可以在使用者層級或儲存庫層級設定 LSP 伺服器：

**使用者層級設定**（適用所有專案）：
編輯 `~/.copilot/lsp-config.json`

**儲存庫層級設定**（適用特定專案）：
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

在互動式會話中使用 `/lsp` 指令檢查已設定的 LSP 伺服器，或直接檢視你的設定檔。

更多資訊請參見[changelog](./changelog.md)。

## 📢 回饋與參與

我們很期待你能在 Copilot CLI 的早期旅程中加入我們。

我們正在快速打造中。預期會有頻繁更新——請保持你的用戶端在最新狀態，以取得最新功能與修正！

你的洞見非常寶貴！歡迎在此儲存庫開啟 issue、加入 Discussions，並在 CLI 中執行 `/feedback` 提交保密的回饋問卷！
