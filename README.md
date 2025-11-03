# GitHub Copilot CLI (公開預覽版)

GitHub Copilot 的強大功能，現在就在您的終端機中。

GitHub Copilot CLI 將 AI 驅動的程式碼輔助功能直接帶到您的命令列，讓您能夠透過自然語言對話來建置、除錯和理解程式碼。採用與 GitHub Copilot 程式碼代理相同的代理框架，它提供智慧輔助，同時與您的 GitHub 工作流程深度整合。

詳情請參閱[官方文件](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)。

![Copilot CLI 啟動畫面圖片](https://github.com/user-attachments/assets/51ac25d2-c074-467a-9c88-38a8d76690e3)

## 🚀 介紹與概述

我們將 GitHub Copilot 程式碼代理的強大功能直接帶到您的終端機。透過 GitHub Copilot CLI，您可以在本地與了解您的程式碼和 GitHub 情境的 AI 代理同步工作。

- **終端機原生開發：** 直接在命令列中與 Copilot 程式碼代理一起工作——無需切換環境。
- **內建 GitHub 整合：** 使用自然語言存取您的儲存庫、議題和拉取請求，所有操作都使用您現有的 GitHub 帳號進行驗證。
- **代理能力：** 與能夠規劃和執行複雜任務的 AI 協作者一起建置、編輯、除錯和重構程式碼。
- **MCP 驅動的擴充性：** 利用程式碼代理預設搭載 GitHub 的 MCP 伺服器，並支援自訂 MCP 伺服器以擴充功能。
- **完全掌控：** 在執行前預覽每個動作——未經您明確批准，不會執行任何操作。

我們仍處於旅程的早期階段，但在您的回饋下，我們正快速迭代，致力於讓 GitHub Copilot CLI 成為您終端機中最好的夥伴。

## 📦 開始使用

### 支援的平台

- **Linux**
- **macOS**
- **Windows**

### 必要條件

- **Node.js** v22 或更高版本
- **npm** v10 或更高版本
- （在 Windows 上）**PowerShell** v6 或更高版本
- **有效的 Copilot 訂閱**。請參閱 [Copilot 方案](https://github.com/features/copilot/plans?ref_cta=Copilot+plans+signup&ref_loc=install-copilot-cli&ref_page=docs)。

如果您透過組織或企業存取 GitHub Copilot，且組織擁有者或企業管理員已在組織或企業設定中停用 GitHub Copilot CLI，則您將無法使用。詳情請參閱[管理組織中 GitHub Copilot 的政策和功能](http://docs.github.com/copilot/managing-copilot/managing-github-copilot-in-your-organization/managing-github-copilot-features-in-your-organization/managing-policies-for-copilot-in-your-organization)。

### 安裝

使用 npm 全域安裝：
```bash
npm install -g @github/copilot
```

### 啟動 CLI

```bash
copilot
```

首次啟動時，您會看到我們可愛的動畫橫幅！如果您想再次看到此橫幅，請使用 `--banner` 旗標啟動 `copilot`。

如果您目前未登入 GitHub，系統會提示您使用 `/login` 斜線命令。輸入此命令並按照螢幕上的指示進行驗證。

#### 使用個人存取權杖 (PAT) 進行驗證

您也可以使用啟用了「Copilot Requests」權限的細粒度 PAT 進行驗證。

1. 訪問 https://github.com/settings/personal-access-tokens/new
2. 在「Permissions」（權限）下，點擊「add permissions」（新增權限）並選擇「Copilot Requests」
3. 產生您的權杖
4. 透過環境變數 `GH_TOKEN` 或 `GITHUB_TOKEN`（依優先順序）將權杖新增到您的環境中

### 使用 CLI

在包含您要處理的程式碼的資料夾中啟動 `copilot`。

預設情況下，`copilot` 使用 Claude Sonnet 4.5。執行 `/model` 斜線命令可從其他可用模型中選擇，包括 Claude Sonnet 4 和 GPT-5

每次向 GitHub Copilot CLI 提交提示時，您的每月進階請求配額會減少一次。有關進階請求的資訊，請參閱[關於進階請求](https://docs.github.com/copilot/managing-copilot/monitoring-usage-and-entitlements/about-premium-requests)。

有關如何使用 GitHub Copilot CLI 的更多資訊，請參閱[官方文件](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)。


## 📢 回饋與參與

我們很高興您能在 Copilot CLI 旅程的早期加入我們。

這是早期階段的預覽版，我們正在快速建置中。預期會有頻繁的更新——請保持您的用戶端為最新版本，以獲得最新功能和修復！

您的見解非常寶貴！請在此儲存庫中開啟議題、加入討論，並從 CLI 執行 `/feedback` 提交機密回饋調查！
