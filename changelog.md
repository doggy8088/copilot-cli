## 0.0.353 - 2025-10-28

- 新增自訂代理支援。自訂代理定義從 `~/.copilot/agents`、儲存庫中的 `.github/agents` 或組織的 `.github` 儲存庫提取。您可以在互動模式下使用 `/agent` 斜線命令明確呼叫代理，或在非互動模式下使用 `--agent <agent>` 參數。代理也會作為工具提供給模型在完成任務時呼叫
- 新增 `/delegate` 命令，可異步委派任務給 Copilot 程式碼代理。任何未暫存的變更將被提交到新分支，並在您的 GitHub 儲存庫中開啟 PR，Copilot 將在背景中完成工作。

## 0.0.352 - 2025-10-27

- 改進包含斜線的 MCP 工具處理
- 改進當使用不支援的模型時 `/model <model>` 命令的錯誤訊息

## 0.0.351 - 2025-10-24

- 改進路徑偵測啟發式演算法，以避免各種煩人且不必要的權限請求：
	- 執行許多已知為唯讀的標準 bash/PowerShell 命令（部分修復 https://github.com/github/sweagentd/issues/7372）
	- PowerShell 中的 `npm test -- --something` 等命令
	- 在您已授予寫入權限的路徑中的 Shell 重導向，如 `> some_file.txt`、`> /dev/null` 和 `2>&1`（修復 https://github.com/github/copilot-cli/issues/211）
	- `gh api` 的參數，如 `gh api /repos/user/repo/ec`（修復 https://github.com/github/copilot-cli/issues/216）
- 改進 Sonnet 4.5 的提示，以減少工作區中留下的中間 markdown 檔案數量
- 👀 ...我們在 [GitHub Universe](https://githubuniverse.com/) 見！

## 0.0.350 - 2025-10-23

- 為了節省情境視窗空間，我們限制了預設 GitHub MCP 伺服器可用的工具清單。在我們的測試中，模型將使用 [GitHub CLI, `gh`](https://github.com/cli/cli)（如果已安裝）來取代缺少的 MCP 工具。如果您希望開啟所有可用工具，我們新增了 `--enable-all-github-mcp-tools` 旗標。
預設可用的工具包括：
	- 程式碼與儲存庫導航
		- get_file_contents
		- search_code
		- search_repositories
		- list_branches
		- list_commits
		- get_commit
	- 議題管理
		- get_issue
		- list_issues
		- get_issue_comments
		- search_issues
	- PR 管理
		- pull_request_read
		- list_pull_requests
		- search_pull_requests
	- 工作流程資訊
		- list_workflows
		- list_workflow_runs
		- get_workflow_run
		- get_job_logs
		- get_workflow_run_logs
	- 其他搜尋
		- user_search
- 將 `sharp` 相依套件整合到 CLI 套件中——我們離實作 https://github.com/github/copilot-cli/issues/16 更近一步，這也修復了 Windows 上的一些啟動阻礙問題（修復 https://github.com/github/copilot-cli/issues/309 和 https://github.com/github/copilot-cli/issues/287）
- 修復輸入權杖未正確追蹤的錯誤（修復 https://github.com/github/copilot-cli/issues/337）
- 修復啟用串流時帶有參數的 MCP 工具會失敗的錯誤
- 新增額外的除錯記錄，有助於我們調查 https://github.com/github/copilot-cli/issues/346

## 0.0.349 - 2025-10-22

- 模型現在可以平行呼叫多個工具。每個工具必須事先確認。此行為可以使用 `--disable-parallel-tools-execution` 旗標停用
- 新增 `/quit` 作為 `/exit` 的別名（修復 https://github.com/github/copilot-cli/issues/357）
- 修復每個串流輸出區塊都被作為對話的一部分傳回模型的錯誤（修復 https://github.com/github/copilot-cli/issues/379）
- 確保在執行路徑權限檢查之前展開環境變數
- 修復 Ctrl+K 刪除到輸入框視覺行結尾而不是邏輯行結尾的錯誤
- 將暫存目錄新增到模型預設可存取的路徑中（修復 https://github.com/github/copilot-cli/issues/306）

## 0.0.348 - 2025-10-21

- Copilot 的輸出現在會逐個權杖串流！可以使用 `--stream off` 停用此功能
- 改進 Copilot CLI 的記憶體佔用，特別是在處理產生大量輸出的 Shell 命令時
- 確保在使用 `/terminal-setup` 時保留 VSCode 設定檔中的註解（修復 https://github.com/github/copilot-cli/issues/325）
- 將 `node-pty` 整合到 CLI 套件中——我們離實作 https://github.com/github/copilot-cli/issues/16 更近一步
- 修復本地工具呼叫中斷會話的問題（修復 https://github.com/github/copilot-cli/issues/365、https://github.com/github/copilot-cli/issues/364、https://github.com/github/copilot-cli/issues/366）
- 將 LICENSE.md 新增到我們的 Node 套件中（修復 https://github.com/github/copilot-cli/issues/371）
- 新增驗證狀態變更的除錯記錄，以找出 https://github.com/github/copilot-cli/issues/346 的根本原因

## 0.0.347 - 2025-10-20

- 修復前端顯示錯誤的 PRU 使用統計資料的更多錯誤
  詳情請參閱 https://github.com/github/copilot-cli/issues/351#issuecomment-3423735333
- 修復貼上後被刪除的輸入內容仍被傳送到模型的錯誤
- 改進渲染檔案差異時的換行和對齊

## 0.0.346 - 2025-10-19

- 修復從設定檔來源的模型在估算進階請求使用時未正確計算的錯誤
  詳情請參閱 https://github.com/github/copilot-cli/issues/351#issuecomment-3419045411

## 0.0.345 - 2025-10-18

- 修復某些使用者的進階請求被過度計算的錯誤（https://github.com/github/copilot-cli/issues/351）。如果您受到影響，我們正在努力退還您被多收的進階請求！

## 0.0.344 - 2025-10-17

- 在提示模式中啟用 GitHub MCP 伺服器
- 新增對 bash 工具執行分離程序的支援
- 在 `copilot help config` 文字中新增支援的模型清單
- 修復會話中止處理，以在按下 <kbd>Esc</kbd> 或強制退出時正確清理孤立的工具呼叫
- 在啟動時強制執行最低 Node 版本要求
- 簡化 `/terminal-setup` 的訊息


## 0.0.343 - 2025-10-16

- ```
  新增模型：
  執行 slash model 命令裝備
  Haiku 4.5。
  ```
- 新增旗標以增強 MCP 伺服器設定，可在每個會話中暫時新增或覆寫伺服器設定：`--additional-mcp-config`（修復 https://github.com/github/copilot-cli/issues/288）
	- 您可以用兩種方式傳遞 MCP 伺服器設定：
		- 內嵌 JSON：`copilot --additional-mcp-config '{"mcpServers": {"my-tool": {...}}}'`
		- 從檔案讀取（前綴為 @）：`copilot --additional-mcp-config @/path/to/config.json`
	- 您也可以多次傳遞此旗標（後面的值會覆寫前面的值）：`copilot --additional-mcp-config @base.json --additional-mcp-config @overrides.json`
- 改進提示以確保代理在 Windows 上使用 Windows 樣式的路徑（修復 https://github.com/github/copilot-cli/issues/261）
- 新增提示，建議使用者在需要啟用多行輸入時執行 `/terminal-setup`
- 各種視覺改進：
	- 在「Thinking...」指示器新增閃爍效果
	- 移除時間軸中使用者訊息周圍的方框
	- 增加差異中已移除行內高亮的對比度
	- 允許在斜線命令中循環瀏覽（從清單底部回到頂部）
	- 對齊權限/確認提示，確保所有提示使用相同的視覺樣式


## 0.0.342 - 2025-10-15

- 全面改版我們的會話記錄格式：
	- 引入新的會話記錄格式，將我們儲存會話的方式與在時間軸中顯示它們的方式分離。新格式更清晰、更簡潔且可擴充，未來將更容易實作新功能。
	- 新會話儲存在 `~/.copilot/session-state`
	- 舊版會話儲存在 `~/.copilot/history-session-state` ——當您從 `copilot --resume` 恢復時，這些會話將遷移到新格式和位置
- 預設啟用 Kitty 協定。支援 Kitty 協定的終端機現在可以透過 Shift+Ctrl 支援多行輸入。透過執行 `/terminal-setup` 命令，在 VSCode 及其分支中也支援多行輸入（修復 https://github.com/github/copilot-cli/issues/14）
- 透過遵循 `GH_HOST` 環境變數來啟用 PAT 和 `gh` 驗證模式的非互動式 GHE 登入（修復 https://github.com/github/copilot-cli/issues/296）
- 透過在 `~/.copilot/config` 中新增持久性的 `log_level` 選項，改進除錯日誌收集的便利性。可能的值：`["none", "error", "warning", "info", "debug", "all", "default"]`
- 在呼叫 `/model` 導致 Copilot API 錯誤時新增除錯記錄。這應該有助於我們診斷一些政策/模型存取邊緣案例，如 https://github.com/github/copilot-cli/issues/268 和 https://github.com/github/copilot-cli/issues/116
- 將 `gradlew` 新增到可列入白名單的子命令清單中（修復 https://github.com/github/copilot-cli/issues/217#issuecomment-3393844685）
- 修復 MCP 工具呼叫失敗後會話可能進入卡住狀態的錯誤（修復 https://github.com/github/copilot-cli/issues/312）
- 使 `--help` 文字的輸出更簡潔

## 0.0.341 - 2025-10-14

- 新增 `/terminal-setup` 命令，用於在未實作 kitty 協定的終端機上設定多行輸入
- 修復拒絕 MCP 工具呼叫會拒絕所有未來工具呼叫的錯誤（修復 https://github.com/github/copilot-cli/issues/290）
- 修復使用參數呼叫 `/model` 無法正常運作的迴歸問題
- 在 `/model` 清單中新增每個模型的進階請求乘數（目前，我們支援的所有模型都是 1x）

## 0.0.340 - 2025-10-13

- 移除「Windows 支援為實驗性質」的警告 -- 在過去兩週，我們在改進 Windows 支援方面取得了一些重大進展！請繼續回報任何問題/回饋
- 改進透過包含模型呼叫錯誤的 Copilot API 請求 ID 和用戶端錯誤的堆疊追蹤來改進除錯
- 修復連續的孤立工具呼叫會導致 "Each `tool_use` block must have a corresponding `tool_result` block in the next message"訊息的問題（修復 https://github.com/github/copilot-cli/issues/102)
- 新增在 `-p` 模式中新增核准新路徑的提示。也新增了 `--allow-all-paths` 參數來核准存取所有路徑。
- 變更MCP 伺服器設定中環境變數的解析，將 `env` 區段的值視為字面值（修復 https://github.com/github/copilot-cli/issues/26).
  已為 CLI 設定 MCP 伺服器的客戶需要對其 `~/.copilot/mcp-config.json`進行小幅修改。對於任何已新增帶有 `env` 區段的伺服器，他們需要在每個 env 區塊條目的鍵值對的「值」部分開頭新增 `$`，以便將值視為環境變數的參考。

  例如：修改前：
    ```json
    {
        "env": {
            "GITHUB_ACCESS_TOKEN": "GITHUB_TOKEN"
         }
    }
    ```

    在此變更之前，CLI 會從 CLI 的環境中讀取 `GITHUB_TOKEN` 的值，並將 MCP 程序中名為 `GITHUB_ACCESS_TOKEN` 的環境變數設定為該值。透過此變更，`GITHUB_ACCESS_TOKEN` 現在將被設定為字面值 `GITHUB_TOKEN`。要獲得舊行為，請變更為：

    ```json
    {
        "env": {
            "GITHUB_ACCESS_TOKEN": "${GITHUB_TOKEN}"
         }
    }
    ```


## 0.0.339 - 2025-10-10

- 改進 `/mcp add` 中 MCP 伺服器的參數輸入——以前，使用者必須使用逗號分隔語法來指定參數。現在，「Command」欄位允許使用者輸入完整命令來啟動伺服器，就像在 Shell 中執行一樣
- 修復使用 Kitty 協定時導致包含 `u` 的文字無法正確貼上的錯誤。Kitty 協定支援仍在 `COPILOT_KITTY` 環境變數後面。（修復 https://github.com/github/copilot-cli/issues/259）
- 修復使用 Kitty 協定時導致程序在 Windows 的 VSCode 終端機中掛起的錯誤。Kitty 協定支援仍在 `COPILOT_KITTY` 環境變數後面。（修復 https://github.com/github/copilot-cli/issues/257）
- 改進當沒有可用模型時 `/model` 選擇器的錯誤處理（修復 https://github.com/github/copilot-cli/issues/229）

## 0.0.338 - 2025-10-09

- 將 Kitty 協定支援移至 `COPILOT_KITTY` 環境變數後面，因為觀察到迴歸問題（https://github.com/github/copilot-cli/issues/257、https://github.com/github/copilot-cli/issues/259）
- 修復多行提示中有空行時的換行問題

## 0.0.337 - 2025-10-08

- 新增 MCP 伺服器名稱的驗證（修復 https://github.com/github/copilot-cli/issues/110）
- 新增 Ctrl+B 和 Ctrl+F 的支援，用於向後和向前移動游標（修復 https://github.com/github/copilot-cli/issues/214）
- 新增支援 [Kitty 協定](https://sw.kovidgoyal.net/kitty/keyboard-protocol/) 的終端機的多行輸入（部分修復 https://github.com/github/copilot-cli/issues/14——更廣泛的終端機支援即將推出！）
- 更新 OAuth 登入 UI，使其在產生裝置代碼後立即開始輪詢（這將更穩固地修復 https://github.com/github/copilot-cli/issues/89 中描述的 SSH 邊緣案例）

## 0.0.336 - 2025-10-07

- 啟用透過 HTTPS_PROXY/HTTP_PROXY 環境變數的代理支援，無論 Node 版本為何（修復 https://github.com/github/copilot-cli/issues/41）
- 大幅減少權杖消耗、每個問題的往返次數和得到結果的時間。我們將在週五的每週變更日誌中分享更具體的資料！
- 改進檔案寫入效能（特別是在 Windows 上），不再依賴 Shell 來獲取當前工作目錄
- 修復 `/clear` 未正確重設情境截斷追蹤狀態的錯誤
- 隱藏會話恢復和 `/clear` 時的「Welcome to GitHub Copilot CLI」歡迎訊息，以獲得更簡潔的外觀
- 改進存在捲軸時表格的對齊
- 透過使其更簡潔來改進 `--help` 的輸出
- 為使用 `--screen-reader` 啟動的使用者新增提示，以持久儲存此偏好設定
- 可能改進某些情況下的閃爍問題；我們仍在處理此問題！

## 0.0.335 - 2025-10-06

- 改進透過預設在時間軸中顯示檔案差異來提升檔案編輯的可見性，無需 Ctrl+R
- 改進斜線命令輸入，在輸入框中顯示參數提示
- 改進寬度小於 80 欄的視窗中的介面顯示
- 減少顏色數量並改進 Markdown 渲染的間距
- 在嘗試在無法運作的環境中使用代理支援時新增警告（Node <24，未設定所需的環境變數）（https://github.com/github/copilot-cli/issues/41 的更永久修復即將在明天推出）
- 將情境截斷訊息的顏色從錯誤顏色更新為警告顏色
- 修復 `copilot` 日誌可能未在 Windows 上正確建立的錯誤
- 修復使用自訂設定檔的 Powershell 使用者可能在執行命令時遇到問題的錯誤（修復 https://github.com/github/copilot-cli/issues/196）
- 修復貼上後提示被截斷以及其他邊緣案例的錯誤（修復 https://github.com/github/copilot-cli/issues/208、https://github.com/github/copilot-cli/issues/218）
- 修復儘管已登入，使用者在啟動時仍會看到登入提示的錯誤（修復 https://github.com/github/copilot-cli/issues/202）
- 修復某些環境中的某些 SSH 使用者無法取得 OAuth 登入連結，且其程序在嘗試開啟瀏覽器時掛起的錯誤（修復 https://github.com/github/copilot-cli/issues/89）

## 0.0.334 - 2025-10-03

- 改進貼上大量內容的體驗：貼上超過 10 行時，會顯示為緊湊的權杖，如 `[Paste #1 - 15 lines]` 而不是讓終端機被大量文字淹沒。
- 新增當對話情境接近模型限制的 ≤20% 時新增警告，表示即將發生截斷。此時，我們建議您開始新的會話 (improves https://github.com/github/copilot-cli/issues/29)
- 移除從持久化的會話歷史記錄中移除退出時的使用統計資料
- 新增在啟動日誌中新增當前版本，以協助錯誤回報
- 移除如果存在參數，則移除透過 TAB 在自動完成項目中循環的功能。這可防止執行 `/cwd /path/to/whatever`，按下 `TAB`，然後看到 `/clear` 自動完成

## 0.0.333 - 2025-10-02

- 新增影像支援！ `@`-提及檔案以將它們新增為模型的輸入。
- 改進Node.JS v24+ 使用者的代理支援。詳情請參閱 [this comment](https://github.com/github/copilot-cli/issues/41#issuecomment-3362444262) 以獲取更多詳細資訊 (Fixes https://github.com/github/copilot-cli/issues/41)
- 新增直接執行 Shell 命令並透過在輸入前加上 `!` (fixes https://github.com/github/copilot-cli/issues/186, https://github.com/github/copilot-cli/issues/12)
- 新增`/usage` 斜線命令，提供有關進階請求使用、會話時間、程式碼變更和每個模型權杖使用的統計資料。此資訊也會在會話結束時列印 (Fixes https://github.com/github/copilot-cli/issues/27, https://github.com/github/copilot-cli/issues/121)
- 改進`--screen-reader` 模式，用資訊性標籤替換時間軸中的圖示
- 新增a `--continue` 旗標來恢復最近關閉的會話
- 更新 `/clear` 命令以正確清除舊的時間軸條目/會話資訊 (Fixes https://github.com/github/copilot-cli/issues/170)

## 0.0.332 - 2025-10-01

- 切換使用符合 [GitHub's docs](https://docs.github.com/en/copilot/how-tos/administer-copilot/manage-for-enterprise/manage-access/manage-network-access) (fixes https://github.com/github/copilot-cli/issues/76)
- 修復 `/user [list | show | swtich]` 未包含從所有驗證模式登入的使用者 (fixes https://github.com/github/copilot-cli/issues/58)
- 修復 使用 `/user switch` 切換到另一個使用者時未在 GitHub MCP 伺服器中生效
- 改進透過在 `@` 檔案選擇器、 `--resume` 會話選擇器和 `/` 命令選擇器中停用捲軸來改進螢幕閱讀器體驗
- 改進捲軸容器的精緻度（增加寬度，降低槽的不透明度）
- 輸入區域的小視覺改進（將當前模型指示器移至右側，使其不與 CWD 擁擠，改進檔案選擇器的 "indexing" 指示器的位置，改進完成選單中的提示格式）
- 改進透過排除標題中的 `#` 前綴來改進 Markdown 易讀性
- 改進我們如何從 Shell 命令中提取路徑以進行權限處理（可能修復 https://github.com/github/copilot-cli/issues/159, https://github.com/github/copilot-cli/issues/67)

## 0.0.331 - 2025-10-01

- 改進檔案讀取/編輯時間軸事件的資訊密度
- 修復 `--banner` 說明文字中的不準確之處；它以前暗示會持續變更設定以始終顯示啟動橫幅
- 改進`/model`清單，以確保使用者只看到他們有權使用的模型——以前，如果使用者嘗試使用他們無權存取的模型（由於其 Copilot 方案、地理區域等），他們會收到 `model_not_supported` 錯誤。這應該透過甚至不在清單中將此類模型顯示為選項來防止這種情況 (Fixes https://github.com/github/copilot-cli/issues/112, https://github.com/github/copilot-cli/issues/85, https://github.com/github/copilot-cli/issues/40)
- 修復在多行提示中按向下箭頭會繞回到第一行的錯誤（這是實作 https://github.com/github/copilot-cli/issues/14 的過程中）
- 將捲軸新增到 `@` 檔案提及選擇器，並將活動緩衝區的大小增加到 10 個項目
- 改進當代理執行時撰寫提示的體驗——上/下箭頭現在將在 `@` 和 `/` 選單中正確導航選項

## 0.0.330 - 2025-09-29

- 將預設模型改回 Sonnet 4，因為 Sonnet 4.5 尚未向所有使用者推出。Sonnet 4.5 仍可從 `/model` 斜線命令取得

## 0.0.329 - 2025-09-29

- 新增對 [Claude Sonnet 4.5](https://github.blog/changelog/2025-09-29-anthropic-claude-sonnet-4-5-is-in-public-preview-for-github-copilot/) 的支援並使其成為預設模型
- 新增 `/model` 斜線命令以輕鬆變更模型（修復 https://github.com/github/copilot-cli/issues/10）
    - `/model` 將開啟選擇器以變更模型
    - `/model <model>` 將模型設定為提供的參數
- 在輸入文字方塊上方顯示當前選擇的模型（解決 https://github.com/github/copilot-cli/issues/120、https://github.com/github/copilot-cli/issues/108 中的回饋）
- 改進當使用者提供不正確的命令列參數時的錯誤訊息。（解決 https://github.com/github/copilot-cli/issues/96 對非互動模式可發現性的回饋）
- 變更 `Ctrl+r` 的行為，使其僅展開最近的時間軸項目。執行 `Ctrl+r` 後，您可以使用 `Ctrl+e` 展開全部
- 改進單字移動邏輯以更好地偵測換行：使用單字移動鍵現在將正確移動到行中的第一個單字
- 改進輸入框中多行輸入的處理：輸入文字方塊可捲動，限制為 10 行。長提示不會再佔據整個螢幕！（這是實作 https://github.com/github/copilot-cli/issues/14 的過程中）
- 移除輸入框的左右邊框。這使得從中複製文字變得更容易！
- 新增 glob 比對到 Shell 規則。使用 `--allow-tool` 和 `--deny-tool` 時，您現在可以指定像 `shell(npm run test:*)` 這樣的內容，以比對以 `npm run test` 開頭的任何 Shell 命令
- 改進 `copilot --resume` 介面，具有相對時間顯示、會話訊息計數（修復 https://github.com/github/copilot-cli/issues/97）

## 0.0.328 - 2025-09-26

- 改進當 Copilot CLI 被組織政策封鎖時收到的錯誤訊息（修復 https://github.com/github/copilot-cli/issues/18 ）
- 改進當使用缺少「Copilot Requests」權限的 PAT 時收到的錯誤訊息（修復 https://github.com/github/copilot-cli/issues/46 ）
- 改進 `/user list` 的輸出，使當前使用者更清楚
- 改進對 `ForEach-Object` 的 PowerShell 解析以及命令名稱表達式的偵測（例如 `& $someCommand`）
