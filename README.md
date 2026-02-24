# GitHub Copilot CLI（公開預覽）

GitHub Copilot 的強大能力，現在就在你的終端機。

GitHub Copilot CLI 將 AI 驅動的程式設計協助直接帶到命令列，讓你可以透過自然語言對話來建置、除錯並理解程式碼。它由與 GitHub 的 Copilot coding agent 相同的代理架構驅動，在深度整合你的 GitHub 工作流程的同時提供智慧協助。

更多資訊請參考[官方文件](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)。

![Copilot CLI 啟動畫面的圖片](https://github.com/user-attachments/assets/f40aa23d-09dd-499e-9457-1d57d3368887)


## 🚀 介紹與概覽

我們把 GitHub Copilot coding agent 的強大能力直接帶到你的終端機。透過 GitHub Copilot CLI，你可以在本機與一個理解你程式碼與 GitHub 情境的 AI 代理同步協作。

- **原生終端機開發：** 直接在命令列中與 Copilot coding agent 協作，不需要切換情境。
- **開箱即用的 GitHub 整合：** 使用自然語言存取你的儲存庫、Issue 與 Pull Request，並沿用既有 GitHub 帳號完成驗證。
- **代理能力：** 與能規劃並執行複雜任務的 AI 協作者一起建置、編輯、除錯與重構程式碼。
- **MCP 驅動的可擴充性：** 代理預設隨附 GitHub 的 MCP 伺服器，也支援自訂 MCP 伺服器以擴充能力。
- **完整掌控：** 每一步都可在執行前預覽 —— 沒有你的明確同意不會做任何事。

我們仍在旅程的早期階段，但有你的回饋，我們會快速迭代，讓 GitHub Copilot CLI 成為你終端機裡最好的夥伴。

## 📦 開始使用

### 支援的平台

- **Linux**
- **macOS**
- **Windows**

### 先決條件

- （Windows）**PowerShell** v6 或以上
- 有效的 **Copilot 訂閱**。請參考 [Copilot 方案](https://github.com/features/copilot/plans?ref_cta=Copilot+plans+signup&ref_loc=install-copilot-cli&ref_page=docs)。

如果你透過組織或企業使用 GitHub Copilot，而你的組織擁有者或企業管理員在組織或企業設定中停用了它，你就無法使用 GitHub Copilot CLI。請參考[在組織中管理 GitHub Copilot 的政策與功能](http://docs.github.com/copilot/managing-copilot/managing-github-copilot-in-your-organization/managing-github-copilot-features-in-your-organization/managing-policies-for-copilot-in-your-organization)以取得更多資訊。

### 安裝

使用 [WinGet](https://github.com/microsoft/winget-cli) 安裝（Windows）：

```bash
winget install GitHub.Copilot
```

```bash
winget install GitHub.Copilot.Prerelease
```

使用 [Homebrew](https://formulae.brew.sh/cask/copilot-cli) 安裝（macOS 與 Linux）：

```bash
brew install copilot-cli
```

```bash
brew install copilot-cli@prerelease
```

使用 [npm](https://www.npmjs.com/package/@github/copilot) 安裝（macOS、Linux 與 Windows）：

```bash
npm install -g @github/copilot
```

```bash
npm install -g @github/copilot@prerelease
```

使用安裝腳本（macOS 與 Linux）：

```bash
curl -fsSL https://gh.io/copilot-install | bash
```

或

```bash
wget -qO- https://gh.io/copilot-install | bash
```

使用 `| sudo bash` 以 root 權限執行，並安裝到 `/usr/local/bin`。

設定 `PREFIX` 來安裝到 `$PREFIX/bin/` 目錄。以 root 執行時預設為 `/usr/local`，非 root 使用者預設為 `$HOME/.local`。

設定 `VERSION` 以安裝指定版本。預設為最新版本。

例如，要將 `v0.0.369` 安裝到自訂目錄：

```bash
curl -fsSL https://gh.io/copilot-install | VERSION="v0.0.369" PREFIX="$HOME/custom" bash
```

### 啟動 CLI

```bash
copilot
```

首次啟動時，你會看到可愛的動態橫幅！如果想再次看到它，請以 `--banner` 旗標啟動 `copilot`。

如果你尚未登入 GitHub，系統會提示你使用 `/login` 斜線指令。輸入此指令並依照螢幕指示完成驗證。

#### 使用 Personal Access Token（PAT）驗證

你也可以使用啟用「Copilot Requests」權限的細粒度 PAT 進行驗證。

1. 前往 https://github.com/settings/personal-access-tokens/new
2. 在「Permissions」下，點選「add permissions」，並選擇「Copilot Requests」
3. 產生你的 token
4. 透過環境變數 `GH_TOKEN` 或 `GITHUB_TOKEN`（優先順序由前至後）加入你的 token

### 使用 CLI

在包含你要處理程式碼的資料夾中啟動 `copilot`。

預設情況下，`copilot` 使用 Claude Sonnet 4.5。執行 `/model` 斜線指令即可選擇其他可用模型，包括 Claude Sonnet 4 與 GPT-5。

### 實驗模式

實驗模式可讓你使用仍在開發中的新功能。你可以透過以下方式啟用：

- 使用 `--experimental` 旗標啟動：`copilot --experimental`
- 在 CLI 內使用 `/experimental` 斜線指令

啟用後，設定會持續保存到你的設定檔中，因此之後啟動不需要再加 `--experimental` 旗標。

#### 實驗功能

- **Autopilot 模式：** Autopilot 是一種新模式（按 `Shift+Tab` 以在模式間循環），鼓勵代理持續工作直到任務完成。

每次你向 GitHub Copilot CLI 提交提示，你的每月 premium request 配額就會減少一次。關於 premium request，請參考[關於 premium request](https://docs.github.com/copilot/managing-copilot/monitoring-usage-and-entitlements/about-premium-requests)。

關於 GitHub Copilot CLI 的更多使用方式，請參考[官方文件](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)。

## 🔧 設定 LSP 伺服器

GitHub Copilot CLI 支援 Language Server Protocol（LSP），可提供更強的程式碼智慧。這項功能可提供像是前往定義、提示資訊與診斷等智慧功能。

### 安裝 Language Server

Copilot CLI 不會內建 LSP 伺服器，你需要自行安裝。例如，要設定 TypeScript 支援：

```bash
npm install -g typescript-language-server
```

其他語言請安裝對應的 LSP 伺服器，並依照下方相同的方式設定。

### 設定 LSP 伺服器

LSP 伺服器透過專用的 LSP 設定檔進行設定。你可以在使用者層級或儲存庫層級進行設定：

**使用者層級設定**（適用於所有專案）：
編輯 `~/.copilot/lsp-config.json`

**儲存庫層級設定**（適用於特定專案）：
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

你可以在互動式會話中使用 `/lsp` 指令檢查已設定的 LSP 伺服器，或直接查看你的設定檔。

更多資訊請參考[變更記錄](./changelog.md)。

## 📢 回饋與參與

我們很高興你能在 Copilot CLI 的早期旅程中加入我們。

這是一個早期階段的預覽版，我們正快速開發中。預期會有頻繁更新——請保持用戶端為最新版本，以取得最新功能與修正！

你的回饋非常珍貴！請在此 repo 開啟 Issue、加入 Discussions，並在 CLI 中執行 `/feedback` 以提交機密回饋問卷！
