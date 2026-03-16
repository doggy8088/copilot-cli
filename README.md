# GitHub Copilot CLI

GitHub Copilot 的強大能力，現在就在你的終端機。

GitHub Copilot CLI 會把 AI 驅動的程式設計協助直接帶到你的命令列，讓你能透過自然語言對話建置、除錯並理解程式碼。它由與 GitHub 的 Copilot coding agent 相同的代理框架驅動，在深度整合你的 GitHub 工作流程的同時提供智慧協助。

更多資訊請參閱[官方文件](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)。

![Copilot CLI 啟動畫面的示意圖片](https://github.com/user-attachments/assets/f40aa23d-09dd-499e-9457-1d57d3368887)


## 🚀 介紹與概覽

我們把 GitHub Copilot coding agent 的能力直接帶進你的終端機。有了 GitHub Copilot CLI，你可以在本機同步與懂得你的程式碼與 GitHub 情境的 AI 代理合作。

- **終端機原生開發：** 直接在命令列與 Copilot coding agent 協作——不需切換情境。
- **開箱即用的 GitHub 整合：** 使用自然語言存取你的儲存庫、議題與 Pull Request，並以現有 GitHub 帳號完成驗證。
- **代理式能力：** 與能規劃並執行複雜任務的 AI 協作，完成建置、編輯、除錯與重構。
- **MCP 驅動的可延伸性：** 代理預設隨附 GitHub 的 MCP 伺服器，並支援自訂 MCP 伺服器以擴充能力。
- **完全掌控：** 每個動作都可在執行前預覽——沒有你的明確同意就不會發生。

我們仍在旅程初期，但有了你的回饋，我們正快速迭代，讓 GitHub Copilot CLI 成為你終端機中最可靠的夥伴。

## 📦 開始使用

### 支援平台

- **Linux**
- **macOS**
- **Windows**

### 先決條件

- （Windows）**PowerShell** v6 或更高版本
- **有效的 Copilot 訂閱**。請參考 [Copilot 方案](https://github.com/features/copilot/plans?ref_cta=Copilot+plans+signup&ref_loc=install-copilot-cli&ref_page=docs)。

如果你是透過組織或企業存取 GitHub Copilot，而組織擁有者或企業管理員在組織或企業設定中停用了它，則無法使用 GitHub Copilot CLI。更多資訊請參閱[在組織中管理 GitHub Copilot 的政策與功能](http://docs.github.com/copilot/managing-copilot/managing-github-copilot-in-your-organization/managing-github-copilot-features-in-your-organization/managing-policies-for-copilot-in-your-organization)。

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

設定 `PREFIX` 以安裝到 `$PREFIX/bin/` 目錄。當以 root 身分執行時預設為 `/usr/local`
非 root 使用者則為 `$HOME/.local`。

設定 `VERSION` 以安裝指定版本。預設為最新版本。

例如，安裝版本 `v0.0.369` 到自訂目錄：

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

首次啟動時，你會看到我們可愛的動畫橫幅！若想再次看到它，請以 `--banner` 旗標啟動 `copilot`。

如果你尚未登入 GitHub，系統會提示使用 `/login` 斜線指令。輸入該指令並依照畫面指示完成驗證。

#### 使用 Personal Access Token (PAT) 驗證

你也可以使用已啟用「Copilot Requests」權限的細粒度 PAT 進行驗證。

1. 前往 https://github.com/settings/personal-access-tokens/new
2. 在「Permissions」下，點選「add permissions」並選擇「Copilot Requests」
3. 產生你的 token
4. 透過環境變數 `GH_TOKEN` 或 `GITHUB_TOKEN`（依優先順序）將 token 加入環境

### 使用 CLI

在包含你要處理程式碼的資料夾中啟動 `copilot`。

`copilot` 預設使用 Claude Sonnet 4.5。請執行 `/model` 斜線指令以選擇其他可用模型，包括 Claude Sonnet 4 與 GPT-5。

### 實驗模式

實驗模式可讓你存取仍在開發中的新功能。你可以透過以下方式啟用實驗模式：

- 以 `--experimental` 旗標啟動：`copilot --experimental`
- 在 CLI 中使用 `/experimental` 斜線指令

啟用後，設定會持久化於你的設定檔，因此之後啟動不再需要 `--experimental` 旗標。

#### 實驗性功能

- **Autopilot 模式：** Autopilot 是一種新模式（按 `Shift+Tab` 在模式間切換），鼓勵代理持續工作直到完成任務。

每次你向 GitHub Copilot CLI 提交提示，當月的 premium requests 配額就會減少一次。關於 premium requests，請參閱[關於 premium requests](https://docs.github.com/copilot/managing-copilot/monitoring-usage-and-entitlements/about-premium-requests)。

若要了解更多 GitHub Copilot CLI 的使用方式，請參閱[官方文件](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)。

## 🔧 設定 LSP 伺服器

GitHub Copilot CLI 支援 Language Server Protocol (LSP)，可強化程式碼智慧功能，例如跳轉到定義、懸停資訊與診斷。

### 安裝語言伺服器

Copilot CLI 不會內建 LSP 伺服器，你需要自行安裝。例如，要設定 TypeScript 支援：

```bash
npm install -g typescript-language-server
```

其他語言請安裝對應的 LSP 伺服器，並依下方相同模式進行設定。

### 設定 LSP 伺服器

LSP 伺服器透過專用的 LSP 設定檔進行配置。你可以在使用者層級或儲存庫層級設定 LSP 伺服器：

**使用者層級設定**（套用到所有專案）：
編輯 `~/.copilot/lsp-config.json`

**儲存庫層級設定**（套用到特定專案）：
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

### 檢視 LSP 伺服器狀態

在互動式會話中使用 `/lsp` 指令來檢查已設定的 LSP 伺服器，或直接查看你的設定檔。

更多資訊請參閱[變更紀錄](./changelog.md)。

## 📢 回饋與參與

我們很興奮能在 Copilot CLI 的早期旅程中與你同行。

我們正在快速建置中。更新會很頻繁--請讓你的用戶端保持最新，以取得最新功能與修正！

你的洞見對我們非常重要！請在這個儲存庫開 issue、加入 Discussions，並在 CLI 中執行 `/feedback` 提交保密回饋調查！
