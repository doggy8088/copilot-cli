# GitHub Copilot CLI

GitHub Copilot 的強大能力，現在就在你的終端機中。

GitHub Copilot CLI 將 AI 驅動的程式設計協助直接帶到你的命令列，讓你能透過自然語言對話來建置、除錯與理解程式碼。它由與 GitHub Copilot coding agent 相同的代理式框架驅動，在深度整合 GitHub 工作流程的同時，提供智慧協助。

更多資訊請參閱[官方文件](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)。

![Copilot CLI 啟動畫面的截圖](https://github.com/user-attachments/assets/f40aa23d-09dd-499e-9457-1d57d3368887)


## 🚀 介紹與概覽

我們正把 GitHub Copilot coding agent 的強大能力帶到你的終端機。透過 GitHub Copilot CLI，你可以在本機、同步地與理解你程式碼與 GitHub 情境的 AI 代理協作。

- **終端機原生開發：** 直接在命令列與 Copilot coding agent 協作——無需切換情境。
- **開箱即用的 GitHub 整合：** 使用自然語言存取你的儲存庫、issues 與 pull requests，全部以現有的 GitHub 帳號驗證。
- **代理式能力：** 與可規劃並執行複雜任務的 AI 夥伴一起建置、編輯、除錯與重構程式碼。
- **MCP 驅動的可擴充性：** coding agent 預設附帶 GitHub 的 MCP 伺服器，並支援自訂 MCP 伺服器以延伸能力。
- **完全掌控：** 每個動作在執行前都可預覽——未經你明確核准不會發生任何事。

我們仍在旅程的早期階段，但在你的回饋下，我們正快速迭代，讓 GitHub Copilot CLI 成為你終端機裡最棒的夥伴。

## 📦 開始使用

### 支援平台

- **Linux**
- **macOS**
- **Windows**

### 先決條件

- （Windows）**PowerShell** v6 或以上
- **有效的 Copilot 訂閱**。請參閱 [Copilot 方案](https://github.com/features/copilot/plans?ref_cta=Copilot+plans+signup&ref_loc=install-copilot-cli&ref_page=docs)。

如果你透過組織或企業取得 GitHub Copilot 權限，且組織擁有者或企業管理員在組織或企業設定中停用 GitHub Copilot CLI，則無法使用 GitHub Copilot CLI。更多資訊請參閱[在組織中管理 GitHub Copilot 的政策與功能](http://docs.github.com/copilot/managing-copilot/managing-github-copilot-in-your-organization/managing-github-copilot-features-in-your-organization/managing-policies-for-copilot-in-your-organization)。

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

設定 `PREFIX` 以安裝到 `$PREFIX/bin/` 目錄。預設為 `/usr/local`
（以 root 執行時）或 `$HOME/.local`（以非 root 使用者執行時）。

設定 `VERSION` 以安裝特定版本。預設為最新版本。

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

首次啟動時，你會看到我們可愛的動畫橫幅！如果想再次看到這個橫幅，請以 `--banner` 旗標啟動 `copilot`。

如果你目前尚未登入 GitHub，系統會提示你使用 `/login` 斜線命令。輸入此命令並依照畫面指示完成驗證。

#### 使用個人存取權杖（PAT）驗證

你也可以使用已啟用「Copilot Requests」權限的細緻化 PAT 進行驗證。

1. 造訪 https://github.com/settings/personal-access-tokens/new
2. 在「Permissions」下，點擊「add permissions」並選擇「Copilot Requests」
3. 產生你的權杖
4. 透過環境變數 `GH_TOKEN` 或 `GITHUB_TOKEN`（依優先順序）將權杖加入環境

### 使用 CLI

在包含你要處理的程式碼的資料夾中啟動 `copilot`。

預設情況下，`copilot` 使用 Claude Sonnet 4.5。執行 `/model` 斜線命令可改用其他可用模型，包括 Claude Sonnet 4 與 GPT-5。

### 實驗模式

實驗模式可啟用仍在開發中的新功能。你可以透過以下方式啟用實驗模式：

- 使用 `--experimental` 旗標啟動：`copilot --experimental`
- 在 CLI 中使用 `/experimental` 斜線命令

啟用後，設定會持久化到你的設定檔，因此後續啟動不再需要 `--experimental` 旗標。

#### 實驗性功能

- **Autopilot 模式：** Autopilot 是一種新模式（按 `Shift+Tab` 切換模式），鼓勵代理持續工作直到任務完成。

每次你提交提示給 GitHub Copilot CLI，都會從你每月的進階請求配額中扣除一次。關於進階請求，請參閱[關於進階請求](https://docs.github.com/copilot/managing-copilot/monitoring-usage-and-entitlements/about-premium-requests)。

更多關於 GitHub Copilot CLI 的使用方式，請參閱[官方文件](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)。

## 🔧 設定 LSP 伺服器

GitHub Copilot CLI 支援 Language Server Protocol（LSP），以提供更強的程式碼智慧能力。此功能可提供像是跳至定義、滑鼠懸停資訊與診斷等智慧功能。

### 安裝語言伺服器

Copilot CLI 不會內建 LSP 伺服器。你需要自行安裝。例如，若要設定 TypeScript 支援：

```bash
npm install -g typescript-language-server
```

對於其他語言，請安裝對應的 LSP 伺服器，並依照下方相同的模式進行設定。

### 設定 LSP 伺服器

LSP 伺服器透過專用的 LSP 設定檔來設定。你可以在使用者層級或儲存庫層級設定 LSP 伺服器：

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

### 檢視 LSP 伺服器狀態

你可以在互動式會話中使用 `/lsp` 命令檢查已設定的 LSP 伺服器，或直接檢視你的設定檔。

更多資訊請參閱[變更日誌](./changelog.md)。

## 📢 意見回饋與參與

我們很高興你能在 Copilot CLI 的旅程早期加入我們。

我們正快速打造中。更新頻繁——請保持你的用戶端為最新，以取得最新功能與修復！

你的洞見極為寶貴！請在此 repo 開 issue、加入 Discussions，並在 CLI 中執行 `/feedback` 提交機密回饋問卷！
