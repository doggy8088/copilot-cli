# GitHub Copilot CLI（公開預覽）

GitHub Copilot 的強大功能，現在就在你的終端機。

GitHub Copilot CLI 將 AI 驅動的程式設計輔助直接帶到你的命令列，讓你能透過自然語言對話來建構、除錯並理解程式碼。它由與 GitHub 的 Copilot coding agent 相同的代理式框架提供支援，在深度整合你的 GitHub 工作流程的同時，提供智慧協助。

如需更多資訊，請參閱[官方文件](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)。

![Copilot CLI 啟動畫面圖片](https://github.com/user-attachments/assets/f40aa23d-09dd-499e-9457-1d57d3368887)


## 🚀 簡介與概覽

我們把 GitHub Copilot coding agent 的強大能力直接帶到你的終端機。有了 GitHub Copilot CLI，你可以在本地端與理解你程式碼與 GitHub 情境的 AI 代理同步協作。

- **終端機原生開發：** 直接在命令列中與 Copilot coding agent 協作——不需要切換情境。
- **內建 GitHub 整合：** 透過自然語言存取你的儲存庫、議題與拉取請求，並使用既有的 GitHub 帳號完成驗證。
- **代理式能力：** 與能規劃並執行複雜任務的 AI 合作伙伴一起建置、編輯、除錯與重構程式碼。
- **MCP 驅動的擴充性：** 這個 coding agent 預設附帶 GitHub 的 MCP 伺服器，也支援自訂 MCP 伺服器以擴充能力。
- **完整掌控：** 每個動作都可在執行前預覽——沒有你的明確核准就不會發生任何事。

我們仍在旅程的早期階段，但在你的回饋下，我們正快速迭代，讓 GitHub Copilot CLI 成為你終端機中最好的夥伴。

## 📦 開始使用

### 支援平台

- **Linux**
- **macOS**
- **Windows**

### 先決條件

- （Windows）**PowerShell** v6 或以上
- 需要**有效的 Copilot 訂閱**。請參閱 [Copilot 方案](https://github.com/features/copilot/plans?ref_cta=Copilot+plans+signup&ref_loc=install-copilot-cli&ref_page=docs)。

若你是透過組織或企業使用 GitHub Copilot，且組織擁有者或企業管理員已在組織或企業設定中停用 GitHub Copilot CLI，則你無法使用。詳情請參閱[在你的組織中管理 GitHub Copilot 的政策與功能](http://docs.github.com/copilot/managing-copilot/managing-github-copilot-in-your-organization/managing-github-copilot-features-in-your-organization/managing-policies-for-copilot-in-your-organization)。

### 安裝

使用 [WinGet](https://github.com/microsoft/winget-cli) 安裝（Windows）：

```bash
winget install GitHub.Copilot
```

```bash
winget install GitHub.Copilot.Prerelease
```

使用 [Homebrew](https://formulae.brew.sh/cask/copilot-cli) 安裝（macOS 和 Linux）：

```bash
brew install copilot-cli
```

```bash
brew install copilot-cli@prerelease
```

使用 [npm](https://www.npmjs.com/package/@github/copilot) 安裝（macOS、Linux 和 Windows）：

```bash
npm install -g @github/copilot
```

```bash
npm install -g @github/copilot@prerelease
```

使用安裝腳本（macOS 和 Linux）：

```bash
curl -fsSL https://gh.io/copilot-install | bash
```

或

```bash
wget -qO- https://gh.io/copilot-install | bash
```

使用 `| sudo bash` 以 root 執行並安裝到 `/usr/local/bin`。

將 `PREFIX` 設為安裝到 `$PREFIX/bin/` 目錄。預設為 `/usr/local`
在 root 身分執行時，或非 root 使用者時為 `$HOME/.local`。

將 `VERSION` 設為安裝特定版本。預設為最新版本。

例如，將版本 `v0.0.369` 安裝到自訂目錄：

```bash
curl -fsSL https://gh.io/copilot-install | VERSION="v0.0.369" PREFIX="$HOME/custom" bash
```

### 啟動 CLI

```bash
copilot
```

第一次啟動時，你會看到我們可愛的動畫橫幅！若想再次顯示這個橫幅，請在啟動 `copilot` 時加上 `--banner` 旗標。

若你尚未登入 GitHub，系統會提示你使用 `/login` 斜線命令。輸入該命令並依照畫面指示完成驗證。

#### 使用個人存取權杖（PAT）驗證

你也可以使用啟用「Copilot Requests」權限的精細範圍 PAT 進行驗證。

1. 造訪 https://github.com/settings/personal-access-tokens/new
2. 在「Permissions」下，點選「add permissions」並選擇「Copilot Requests」
3. 產生你的 token
4. 透過環境變數 `GH_TOKEN` 或 `GITHUB_TOKEN`（依優先順序）將 token 加入你的環境

### 使用 CLI

在包含你要處理之程式碼的資料夾中啟動 `copilot`。

預設情況下，`copilot` 使用 Claude Sonnet 4.5。請使用 `/model` 斜線命令選擇其他可用模型，包括 Claude Sonnet 4 與 GPT-5。

### 實驗模式

實驗模式可讓你使用仍在開發中的新功能。你可以透過以下方式啟用實驗模式：

- 使用 `--experimental` 旗標啟動：`copilot --experimental`
- 在 CLI 內使用 `/experimental` 斜線命令

啟用後，該設定會被保存到你的設定中，因此後續啟動不再需要 `--experimental` 旗標。

#### 實驗性功能

- **Autopilot 模式：** Autopilot 是一種新模式（按 `Shift+Tab` 在模式間循環），鼓勵代理持續工作直到任務完成。

每次你在 GitHub Copilot CLI 提交提示時，你的每月進階請求配額就會減少一次。關於進階請求的資訊，請參閱[關於進階請求](https://docs.github.com/copilot/managing-copilot/monitoring-usage-and-entitlements/about-premium-requests)。

更多關於 GitHub Copilot CLI 的使用方式，請參閱[官方文件](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)。

## 🔧 設定 LSP 伺服器

GitHub Copilot CLI 支援 Language Server Protocol（LSP），以增強程式碼智慧。這項功能提供例如跳到定義、懸浮提示與診斷等智慧程式碼特性。

### 安裝語言伺服器

Copilot CLI 不包含 LSP 伺服器，你需要另行安裝。例如，設定 TypeScript 支援：

```bash
npm install -g typescript-language-server
```

對於其他語言，請安裝對應的 LSP 伺服器，並依照下方相同的模式完成設定。

### 設定 LSP 伺服器

LSP 伺服器透過專用的 LSP 設定檔進行配置。你可以在使用者層級或儲存庫層級設定 LSP 伺服器：

**使用者層級設定**（套用於所有專案）：
編輯 `~/.copilot/lsp-config.json`

**儲存庫層級設定**（套用於特定專案）：
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

在互動式會話中使用 `/lsp` 命令檢查已設定的 LSP 伺服器，或直接查看你的設定檔。

更多資訊請參閱[變更日誌](./changelog.md)。

## 📢 意見回饋與參與

很高興你能在 Copilot CLI 的早期旅程中加入我們。

這是一個早期預覽版本，我們正在快速打造。預期會有頻繁更新--請保持你的用戶端為最新狀態，以取得最新功能與修正！

你的洞見非常珍貴！歡迎在此儲存庫開啟 issue、加入 Discussions，並在 CLI 中執行 `/feedback` 提交機密回饋問卷！
