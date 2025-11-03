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

- 移除the "Windows support is experimental" warning -- we've made some big strides in improving Windows support the last two weeks! Please continue to report any issues/feedback
- 改進debugging by including the Copilot API request ID for model calls errors and stack traces for client errors
- 修復an issue where consecutive orphaned tool calls led to a "Each `tool_use` block must have a corresponding `tool_result` block in the next message" message (fixes https://github.com/github/copilot-cli/issues/102)
- 新增a prompt to approve new paths in `-p` mode. Also added `--allow-all-paths` argument that approves access to all paths.
- 變更parsing of environment variables in MCP server configuration to treat the value of the `env` section as literal values (fixes https://github.com/github/copilot-cli/issues/26).
  Customers who have configured MCP Servers for use with the CLI will need to make a slight modification to their `~/.copilot/mcp-config.json`.  For any servers they have added with an `env` section, they will need to go add a `$` to the start of the "value" pair of the key value pair of each entry in the env-block, so to have the values treated as references to environment variables.

  For example: Before:
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

- 改進argument input to MCP servers in `/mcp add` -- previously, users had to use comma-separated syntax to specify arguments. Now, the "Command" field allows users to input the full command to start the server as if they were running it in a shell
- 修復a bug when using the Kitty protocol that led to text containing `u` to not paste correctly. Kitty protocol support is still behind the `COPILOT_KITTY` environment variable. (Fixes https://github.com/github/copilot-cli/issues/259)
- 修復a bug when using the Kitty protocol that led to the process hanging in VSCode terminal on Windows. Kitty protocol support is still behind the `COPILOT_KITTY` environment variable. (Fixes https://github.com/github/copilot-cli/issues/257)
- 改進the error handling in the `/model` picker when no models are available (fixes https://github.com/github/copilot-cli/issues/229)

## 0.0.338 - 2025-10-09

- 移動Kitty protocol support behind the `COPILOT_KITTY` environment variable due to observed regressions (https://github.com/github/copilot-cli/issues/257, https://github.com/github/copilot-cli/issues/259)
- 修復a wrapping issue in multi-line prompts with empty lines

## 0.0.337 - 2025-10-08

- 新增validation for MCP server names (fixes https://github.com/github/copilot-cli/issues/110)
- 新增support for Ctrl+B and Ctrl+F for moving cursor back and forward (fixes https://github.com/github/copilot-cli/issues/214)
- 新增support for multi-line input for terminals that support the [Kitty protocol](https://sw.kovidgoyal.net/kitty/keyboard-protocol/) (partially fixes https://github.com/github/copilot-cli/issues/14 -- broader terminal support coming soon!)
- 更新the OAuth login UI to begin polling as soon as the device code is generated (this will _more solidly_ fix SSH edge-cases as described in https://github.com/github/copilot-cli/issues/89)

## 0.0.336 - 2025-10-07

- 啟用proxy support via HTTPS_PROXY/HTTP_PROXY environment variables regardless of Node version (Fixes https://github.com/github/copilot-cli/issues/41)
- 大幅減少token consumption, round trips per problem, and time to result. We'll share more specific data in our weekly changelog on Friday!
- 改進file write performances (especially on Windows) by not relying on the shell to fetch the current working directory
- 修復a bug where `/clear` did not properly reset the context truncation tracking state
- 隱藏the "Welcome to GitHub Copilot CLI" welcome message on session resumption and `/clear` for a cleaner look
- 改進the alignment of tables where the scrollbar is present
- 改進the output of `--help` by making it more concise
- 新增a prompt for users who launch with `--screen-reader` to persistently save this preference
- 可能改進flickering in some cases; we're still working on this!

## 0.0.335 - 2025-10-06

- 改進visibility into file edits by showing file diffs in the timeline by default, without the need to Ctrl+R
- 改進slash command input by showing argument hints in the input box
- 改進the display of the interface in windows less than 80 columns wide
- 減少the number of colors and improved the spacing of Markdown rendering
- 新增a warning when attempting to use proxy support in an environment where it won't work (Node <24, required environment variables not set) (A more permanent fix for https://github.com/github/copilot-cli/issues/41 is coming ~tomorrow)
- 更新the context truncation message's color from an error color to a warning color
- 修復a bug where `copilot` logs might not have been properly created on Windows
- 修復a bug where Powershell users with custom profiles might have had issues running commands (Fixes https://github.com/github/copilot-cli/issues/196)
- 修復a bug where prompts were truncated after pasting and other edge cases (Fixes https://github.com/github/copilot-cli/issues/208, https://github.com/github/copilot-cli/issues/218)
- 修復a bug where users would see a login prompt on startup despite being logged in (fixes https://github.com/github/copilot-cli/issues/202)
- 修復a bug where some SSH users in certain environments were unable to get the OAuth login link and had their processes hang trying to open a browser (fixes https://github.com/github/copilot-cli/issues/89)

## 0.0.334 - 2025-10-03

- 改進the experience of pasting large content: when pasting more than 10 lines, it's displayed as a compact token like `[Paste #1 - 15 lines]` instead of flooding the terminal.
- 新增a warning when conversation context approaches ≤20% remaining of the model's limit that truncation will soon occur. At this point, we recommend you begin a new session (improves https://github.com/github/copilot-cli/issues/29)
- 移除the on-exit usage stats from the persisted session history
- 新增the current version to startup logs to aid in bug reporting
- 移除cycling through TAB autocomplete items if an argument is present. This prevents running `/cwd /path/to/whatever`, hitting `TAB`, then seeing `/clear` autocomplete

## 0.0.333 - 2025-10-02

- 新增image support! `@`-mention files to add them as input to the model.
- 改進proxy support for users on Node.JS v24+. See [this comment](https://github.com/github/copilot-cli/issues/41#issuecomment-3362444262) for more details (Fixes https://github.com/github/copilot-cli/issues/41)
- 新增support for directly executing shell commands and bypassing the model by prepending input with `!` (fixes https://github.com/github/copilot-cli/issues/186, https://github.com/github/copilot-cli/issues/12)
- 新增`/usage` slash command to provide stats about Premium request usage, session time, code changes, and per-model token use. This information is also printed at the conclusion of a session (Fixes https://github.com/github/copilot-cli/issues/27, https://github.com/github/copilot-cli/issues/121)
- 改進`--screen-reader` mode by replacing icons in the timeline with informative labels
- 新增a `--continue` flag to resume the most recently closed session
- 更新the `/clear` command to properly clear old timeline entries/session information (Fixes https://github.com/github/copilot-cli/issues/170)

## 0.0.332 - 2025-10-01

- 切換to using per-subscription Copilot API endpoints in accordance with [GitHub's docs](https://docs.github.com/en/copilot/how-tos/administer-copilot/manage-for-enterprise/manage-access/manage-network-access) (fixes https://github.com/github/copilot-cli/issues/76)
- 修復a bug where `/user [list | show | swtich]` did not include users signed in from all authentication modes (fixes https://github.com/github/copilot-cli/issues/58)
- 修復a bug where switching to another user with `/user switch` did not take effect in the GitHub MCP server
- 改進the screenreader experience by disabling the scrollbar in the `@` file picker, the `--resume` session picker, and the `/` command picker
- 改進the polish of the scrollbar container (increased the width, reduced the opacity of the gutter)
- Minor visual improvements to the input area (moved the current model indicator to the right so it's not cramped with the CWD, improved the positioning of the file picker's "indexing" indicator, improved hint formatting in completion menus)
- 改進Markdown legibility by excluding `#` prefixes in headings
- 改進how we extract paths from shell commands for permission handling (might fix https://github.com/github/copilot-cli/issues/159, https://github.com/github/copilot-cli/issues/67)

## 0.0.331 - 2025-10-01

- 改進the information density of file read/edit timeline events
- 修復an inaccuracy in the `--banner` help text; it previously implied that it would persistently change the configuration to always show the startup banner
- 改進the `/model`s list to ensure that a user only sees models they have access to use -- previously, if a user tries to use a model they do not have access to (because of their Copilot plan, their geographic region, etc), they received a `model_not_supported` error. This should prevent that by not even showing such models as options in the list (Fixes https://github.com/github/copilot-cli/issues/112, https://github.com/github/copilot-cli/issues/85, https://github.com/github/copilot-cli/issues/40)
- 修復a bug where pressing down arrow in a multi-line prompt would wrap around to the first line (This is on the way to implementing https://github.com/github/copilot-cli/issues/14)
- 新增a scrollbar to the `@` file mentioning picker and increased the size of the active buffer to 10 items
- 改進the experience of writing prompts while the agent is running -- up/down arrows will now correctly navigate between options in the `@` and `/` menus

## 0.0.330 - 2025-09-29

- 變更the default model back to Sonnet 4 since Sonnet 4.5 hasn't rolled out to all users yet. Sonnet 4.5 is still available from the `/model` slash command

## 0.0.329 - 2025-09-29

- 新增support for [Claude Sonnet 4.5](https://github.blog/changelog/2025-09-29-anthropic-claude-sonnet-4-5-is-in-public-preview-for-github-copilot/) and made it the default model
- 新增`/model` slash command to easily change the model (fixes https://github.com/github/copilot-cli/issues/10)
    - `/model` will open a picker to change the model
    - `/model <model>` will set the model to the parameter provided
- 新增display of currently selected model above the input text box (Addresses feedback in https://github.com/github/copilot-cli/issues/120, https://github.com/github/copilot-cli/issues/108, )
- 改進error messages when users provide incorrect command-line arguments. (Addresses feedback of the discoverability of non-interactive mode from  https://github.com/github/copilot-cli/issues/96)
- 變更the behavior of `Ctrl+r` to expand only recent timeline items. After running `Ctrl+r`, you can use `Ctrl+e` to expand all
- 改進word motion logic to better detect newlines: using word motion keys will now correctly move to the first word on a line
- 改進the handling of multi-line inputs in the input box: the input text box is scrollable, limited to 10 lines. Long prompts won't take up the whole screen anymore! (This is on the way to implementing https://github.com/github/copilot-cli/issues/14)
- 移除the left and right boarders from the input box. This makes it easier to copy text out of it!
- 新增glob matching to shell rules. When using `--allow-tool` and `--deny-tool`, you can now specify things like `shell(npm run test:*)` to match any shell commands beginning with `npm run test`
- 改進the `copilot --resume` interface with relative time display, session message count, (Fixes https://github.com/github/copilot-cli/issues/97)

## 0.0.328 - 2025-09-26

- 改進error message received when Copilot CLI is blocked by organization policy (fixes https://github.com/github/copilot-cli/issues/18 )
- 改進the error message received when using a PAT that is missing the "Copilot Requests" permission (fixes https://github.com/github/copilot-cli/issues/46 )
- 改進the output of `/user list` to make it clearer which is the current user
- 改進PowerShell parsing of `ForEach-Object` and detection of command name expressions (e.g.,`& $someCommand`)
