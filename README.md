# GitHub Copilot CLI

GitHub Copilot 的力量，現在就在你的終端機。

GitHub Copilot CLI 將 AI 驅動的程式設計協助直接帶到你的命令列，讓你透過自然語言對話來建置、除錯並理解程式碼。它由與 GitHub Copilot 編碼代理相同的代理式框架驅動，在深度整合你的 GitHub 工作流程的同時提供智慧協助。

更多資訊請參閱[官方文件](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)。

![Copilot CLI 啟動畫面示意圖](https://github.com/user-attachments/assets/f40aa23d-09dd-499e-9457-1d57d3368887)


## 🚀 簡介與概覽

我們把 GitHub Copilot 編碼代理的強大能力直接帶到你的終端機。有了 GitHub Copilot CLI，你可以在本機與一個了解你的程式碼與 GitHub 情境的 AI 代理同步工作。

- **原生終端機開發：** 直接在命令列使用 Copilot 編碼代理 — 無需切換情境。
- **開箱即用的 GitHub 整合：** 透過自然語言存取你的儲存庫、issues 與 pull requests，並使用現有 GitHub 帳號完成驗證。
- **代理式能力：** 透過可規劃並執行複雜任務的 AI 協作者建置、編輯、除錯與重構程式碼。
- **MCP 驅動的可擴充性：** 編碼代理預設隨附 GitHub MCP 伺服器，並支援自訂 MCP 伺服器以擴充能力。
- **完全掌控：** 執行前可預覽每個動作 — 沒有你的明確核准就不會執行。

我們仍在早期階段，但在你的回饋協助下，我們正快速迭代，讓 GitHub Copilot CLI 成為你終端機中最強大的夥伴。

## 📦 快速開始

### 支援平台

- **Linux**
- **macOS**
- **Windows**

### 先決條件

- （Windows）**PowerShell** v6 或以上
- **有效的 Copilot 訂閱**。請參閱 [Copilot 方案](https://github.com/features/copilot/plans?ref_cta=Copilot+plans+signup&ref_loc=install-copilot-cli&ref_page=docs)。

如果你是透過組織或企業取得 GitHub Copilot 存取權，且組織擁有者或企業管理員在組織或企業設定中停用它，你就無法使用 GitHub Copilot CLI。更多資訊請參閱[在組織中管理 GitHub Copilot 的政策與功能](http://docs.github.com/copilot/managing-copilot/managing-github-copilot-in-your-organization/managing-github-copilot-features-in-your-organization/managing-policies-for-copilot-in-your-organization)。

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

設定 `PREFIX` 以安裝到 `$PREFIX/bin/` 目錄。預設在 root 下為 `/usr/local`
非 root 使用者則為 `$HOME/.local`。

設定 `VERSION` 以安裝指定版本。預設為最新版本。

例如，要將 `v0.0.369` 版本安裝到自訂目錄：

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

首次啟動時，你會看到我們可愛的動態橫幅！如果想再次看到它，請使用 `--banner` 旗標啟動 `copilot`。

如果你目前尚未登入 GitHub，系統會提示你使用 `/login` 斜線指令。輸入該指令並依照畫面指示完成驗證。

#### 使用個人存取權杖（PAT）驗證

你也可以使用啟用「Copilot Requests」權限的精細化 PAT 進行驗證。

1. 前往 https://github.com/settings/personal-access-tokens/new
2. 在「Permissions」下，點選「add permissions」並選擇「Copilot Requests」
3. 產生你的權杖
4. 透過環境變數 `GH_TOKEN` 或 `GITHUB_TOKEN` 將權杖加入環境（依優先順序）

### 使用 CLI

在包含你要處理的程式碼的資料夾中啟動 `copilot`。

預設情況下，`copilot` 使用 Claude Sonnet 4.5。執行 `/model` 斜線指令可改用其他可用模型，包括 Claude Sonnet 4 與 GPT-5。

### 實驗模式

實驗模式可啟用仍在開發中的新功能。你可以透過以下方式啟用：

- 以 `--experimental` 旗標啟動：`copilot --experimental`
- 在 CLI 內使用 `/experimental` 斜線指令

一旦啟用，設定會保留在你的設定檔中，因此後續啟動時不再需要 `--experimental` 旗標。

#### 實驗功能

- **Autopilot 模式：** Autopilot 是一種新模式（按下 `Shift+Tab` 可在模式間切換），會鼓勵代理持續工作直到任務完成。

每次你向 GitHub Copilot CLI 提交提示時，你每月的 premium requests 配額都會減少一次。關於 premium requests 的資訊，請參閱[關於 premium requests](https://docs.github.com/copilot/managing-copilot/monitoring-usage-and-entitlements/about-premium-requests)。

如需更多關於 GitHub Copilot CLI 的使用方式，請參閱[官方文件](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)。

## 🔧 設定 LSP 伺服器

GitHub Copilot CLI 支援 Language Server Protocol（LSP）以提升程式碼智慧能力。此功能提供如「前往定義」、「滑鼠懸停資訊」與診斷等智慧程式碼功能。

### 安裝語言伺服器

Copilot CLI 不內建 LSP 伺服器，你需要自行安裝。例如，設定 TypeScript 支援：

```bash
npm install -g typescript-language-server
```

其他語言則請安裝對應的 LSP 伺服器，並依照下方相同的方式進行設定。

### 設定 LSP 伺服器

LSP 伺服器透過專用的 LSP 設定檔進行設定。你可以在使用者層級或儲存庫層級設定：

**使用者層級設定**（適用於所有專案）：
編輯 `~/.copilot/lsp-config.json`

**儲存庫層級設定**（適用於特定專案）：
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

在互動式會話中使用 `/lsp` 指令來檢視已設定的 LSP 伺服器，或直接查看你的設定檔。

更多資訊請參閱[changelog](./changelog.md)。

## 📢 回饋與參與

很高興你能在 Copilot CLI 旅程的早期加入我們。

我們正在快速打造。預期會有頻繁更新——請保持你的用戶端為最新版本，以取得最新功能與修正！

你的洞見非常寶貴！歡迎在此儲存庫開 issue、加入 Discussions，並在 CLI 中執行 `/feedback` 送出機密回饋問卷！
