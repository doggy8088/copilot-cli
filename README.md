# GitHub Copilot CLI

GitHub Copilot 的強大能力，現在就在你的終端機中。

GitHub Copilot CLI 將 AI 驅動的程式設計協助直接帶進你的命令列，讓你能透過自然語言對話來建置、除錯並理解程式碼。它由與 GitHub 的 Copilot coding agent 相同的代理式執行框架驅動，在與 GitHub 工作流程深度整合的同時，提供智慧協助。

更多資訊請參閱 [我們的官方文件](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)。

![Copilot CLI 啟動畫面的圖片](https://github.com/user-attachments/assets/f40aa23d-09dd-499e-9457-1d57d3368887)


## 🚀 介紹與概覽

我們正將 GitHub Copilot coding agent 的能力直接帶進你的終端機。透過 GitHub Copilot CLI，你可以在本機同步與一位理解你的程式碼與 GitHub 脈絡的 AI 代理協作。

- **終端機原生開發：** 直接在命令列中與 Copilot coding agent 協作，無需切換情境。
- **開箱即用的 GitHub 整合：** 使用自然語言存取你的儲存庫、issues 與 pull requests，並以你現有的 GitHub 帳號完成驗證。
- **代理式能力：** 與能規劃並執行複雜任務的 AI 協作者一起建置、編輯、除錯與重構程式碼。
- **MCP 驅動的可擴充性：** 善用 coding agent 預設隨附的 GitHub MCP server，並透過自訂 MCP servers 擴充能力。
- **完整控制：** 在執行前預覽每一個動作，未經你明確核准，任何事情都不會發生。

我們仍處於發展早期，但在你的回饋幫助下，我們正快速迭代，致力讓 GitHub Copilot CLI 成為你終端機中最理想的夥伴。

## 📦 開始使用

### 支援平台

- **Linux**
- **macOS**
- **Windows**

### 必要條件

- （Windows）**PowerShell** v6 或更高版本
- 需要 **有效的 Copilot 訂閱**。請參閱 [Copilot plans](https://github.com/features/copilot/plans?ref_cta=Copilot+plans+signup&ref_loc=install-copilot-cli&ref_page=docs)。

如果你是透過組織或企業取得 GitHub Copilot 的使用權限，而你的組織擁有者或企業管理員已在組織或企業設定中將其停用，就無法使用 GitHub Copilot CLI。更多資訊請參閱 [Managing policies and features for GitHub Copilot in your organization](http://docs.github.com/copilot/managing-copilot/managing-github-copilot-in-your-organization/managing-github-copilot-features-in-your-organization/managing-policies-for-copilot-in-your-organization)。

### 安裝

使用安裝腳本安裝（macOS 和 Linux）：

```bash
curl -fsSL https://gh.io/copilot-install | bash
```

或

```bash
wget -qO- https://gh.io/copilot-install | bash
```

使用 `| sudo bash` 可在 root 身分下執行，並安裝到 `/usr/local/bin`。

將 `PREFIX` 設為安裝到 `$PREFIX/bin/` 目錄。以 root 身分執行時，預設為 `/usr/local`；以非 root 使用者身分執行時，預設為 `$HOME/.local`。

將 `VERSION` 設為安裝指定版本。預設為最新版本。

例如，若要將版本 `v0.0.369` 安裝到自訂目錄：

```bash
curl -fsSL https://gh.io/copilot-install | VERSION="v0.0.369" PREFIX="$HOME/custom" bash
```

使用 [Homebrew](https://formulae.brew.sh/cask/copilot-cli) 安裝（macOS 和 Linux）：

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


使用 [npm](https://www.npmjs.com/package/@github/copilot) 安裝（macOS、Linux 和 Windows）：

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

第一次啟動時，你會看到我們可愛的動畫橫幅！如果你想再次看到這個橫幅，請在啟動 `copilot` 時加上 `--banner` 旗標。

如果你目前尚未登入 GitHub，系統會提示你使用 `/login` 斜線指令。輸入這個指令並依照畫面上的說明完成驗證。

#### 使用 Personal Access Token (PAT) 驗證

你也可以使用已啟用 "Copilot Requests" 權限的細粒度 PAT 進行驗證。

1. 前往 https://github.com/settings/personal-access-tokens/new
2. 在 "Permissions" 下，點選 "add permissions" 並選擇 "Copilot Requests"
3. 產生你的 token
4. 透過環境變數 `GH_TOKEN` 或 `GITHUB_TOKEN`（依優先順序）將 token 加入你的環境

### 使用 CLI

在包含你想處理程式碼的資料夾中啟動 `copilot`。

預設情況下，`copilot` 使用 Claude Sonnet 4.5。執行 `/model` 斜線指令，即可從其他可用模型中選擇，包括 Claude Sonnet 4 和 GPT-5。

### 實驗模式

實驗模式可讓你使用仍在開發中的新功能。你可以透過以下方式啟用實驗模式：

- 啟動時加上 `--experimental` 旗標：`copilot --experimental`
- 在 CLI 內使用 `/experimental` 斜線指令

啟用後，這項設定會保存在你的設定中，因此後續再次啟動時就不需要再加上 `--experimental` 旗標。

#### 實驗功能

- **Autopilot mode:** Autopilot 是一種新模式（按 `Shift+Tab` 可循環切換模式），會鼓勵代理持續工作直到完成任務。

每次你向 GitHub Copilot CLI 提交提示時，你每月的 premium requests 配額都會減少一次。關於 premium requests 的資訊，請參閱 [About premium requests](https://docs.github.com/copilot/managing-copilot/monitoring-usage-and-entitlements/about-premium-requests)。

如需更多關於如何使用 GitHub Copilot CLI 的資訊，請參閱 [我們的官方文件](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)。

## 🔧 設定 LSP 伺服器

GitHub Copilot CLI 支援 Language Server Protocol (LSP)，以提供更強的程式碼智慧功能。此功能提供像是跳至定義、懸停資訊與診斷等智慧程式碼能力。

### 安裝語言伺服器

Copilot CLI 不會內建 LSP servers。你需要另外安裝它們。例如，若要設定 TypeScript 支援：

```bash
npm install -g typescript-language-server
```

對於其他語言，請安裝對應的 LSP server，並依照下方所示的相同模式進行設定。

### 設定 LSP 伺服器

LSP servers 是透過專用的 LSP 設定檔來設定。你可以在使用者層級或儲存庫層級設定 LSP servers：

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

### 檢視 LSP Server 狀態

你可以在互動式工作階段中使用 `/lsp` 指令檢查已設定的 LSP servers，或直接查看你的設定檔。

如需更多資訊，請參閱 [changelog](./changelog.md)。

## 📢 回饋與參與

很高興你在 Copilot CLI 發展早期就加入我們。

我們正在快速開發。更新會很頻繁，請讓你的用戶端保持在最新版本，以取得最新功能與修正！

你的意見非常重要！歡迎在這個 repo 建立 issue、加入 Discussions，並從 CLI 執行 `/feedback` 提交一份保密的回饋問卷！
