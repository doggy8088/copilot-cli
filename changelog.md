## 0.0.412 - 2026-02-19

- 改善快速說明可近用性：螢幕閱讀器友善的分頁標籤、重新排序的版面與分組的 `help commands` 輸出
- 在 `/agents` 選擇器中隱藏 `user-invocable: false` 的自訂代理
- 設定檔語法錯誤改為顯示警告，不再靜默崩潰
- Windows 原生預建檔採用 Authenticode 簽署，避免防毒軟體隔離原生模組
- 允許 `/reset-allowed-tools` 在代理執行期間運行
- 工具 schema 無效的 MCP 伺服器不再失去所有工具
- alt-screen 模式在長時間會話中不再持續增加記憶體用量
- 新增 `/mcp reload` 指令以重新載入 MCP 設定
- 技能支援 `disable-model-invocation` frontmatter 欄位
- /fleet 協調器驗證子代理工作
- 棄用 gpt-5 模型
- Windows 斜線旗標（例如 `xcopy /E /I`）不再視為檔案路徑
- 啟動時若技能載入失敗，時間軸會顯示警告並提示執行 /skills 查看詳情
- 當橫幅停用時，啟動不再閃現橫幅字元
- 可用 ctrl+y 在終端編輯器中編輯 plan
- Windows 現已支援終端編輯器
- 可在 lsp.json 設定 LSP 伺服器請求逾時
- 新增 `/update` 指令以檢視變更日誌與更新說明
- 新增 exit_plan_mode 工具，提供計畫核准對話框以檢視並接受計畫
- 支援 ~/.copilot/instructions/*.instructions.md 檔案，作為跨所有儲存庫的使用者層級指令
- alt-screen 文字選取支援雙擊選字與三擊選行
- 可用 ctrl+x ctrl+e 在偏好的終端編輯器中編輯 prompt
- 避免 Windows 終端機出現多餘的錯誤訊息
- 在 AskUser 提示中輸入 `?` 不再觸發快速說明覆蓋層
- 改善 SQL 工具的時間軸條目
- 在長時間會話中降低 alt-screen 模式記憶體用量
- /fleet 模式以更多子代理並行分派，加速執行
- 啟用 alt-screen 模式時，指令選擇器會以全螢幕 alt-screen 檢視開啟
- 啟用 alt-screen 模式時，技能選擇器會以全螢幕 alt-screen 檢視開啟
- 指令檔案不再需要 YAML frontmatter——純 Markdown 檔案可自動推導名稱與描述
- 存在多個會話時，session 選擇器可即時開啟且不再出現載入閃爍
- 滑鼠事件座標片段不再出現在輸入欄位
- 新增跨會話記憶：可詢問過去工作、檔案與 PR（實驗性）
- 新增 `--bash-env` 旗標，在 shell 會話中 source BASH_ENV
- 恢復 `ctrl+x /` 作為執行指令且保留輸入的替代快捷鍵
- `/clear` 會保留代理模式（autopilot、plan 或 interactive）
- MCP 錯誤訊息會包含伺服器名稱
- 拖曳時，時間軸文字選取不再溢出到提示區域

## 0.0.411 - 2026-02-17

- 當政策拒絕存取時，改進錯誤訊息與指引
- 自訂代理改用 `disable-model-invocation` 取代 `infer`（向後相容）
- 新增支援 Claude Sonnet 4.6 模型
- 記憶儲存於時間軸中顯示主題、事實與引用
- Tab 自動完成會遵循已反白的斜線指令選項
- 支援來自 Windows On-Device Registry 的 MCP 伺服器
- alt-screen 模式下頁尾區域也可進行文字選取
- 支援 `--alt-screen on` 與 `--alt-screen off` 語法
- 新增 `include_coauthor` 設定選項，可停用 git commit 的 Co-authored-by trailer
- SDK API 支援 plan 模式、autopilot、fleet 與工作區檔案
- autopilot 模式與 /fleet 指令現在對所有使用者開放
- 在 alt-screen 模式拖曳選取到邊緣時視窗會自動捲動
- 互動式 shell 指令在所有版本的 Windows 上都能順利完成
- 降低 alt-screen 模式在長時間會話中的記憶體用量
- 在 alt-screen 模式使用 --resume 時，session 選擇器不再閃爍
- 代理完成時終端鈴聲只會響一次，而非每次工具完成都響
- 自訂指令檔案的大小寫不再影響辨識
- PowerShell 指令含語法錯誤時不再造成掛起
- 改進 --alt-screen 模式下文字選取的回應速度
- 暫停時顯示游標，恢復時隱藏游標

## 0.0.410 - 2026-02-14

- 修正由於快速日誌記錄導致的高記憶體用量
- Shell 模式貼上原始文字而非貼上標記
- 降低編碼串流區塊時的記憶體用量
- 修正 alt-screen 與時間軸網址渲染，保留長連結不截斷
- 透過壓縮後清除短暫事件，降低長時間會話下的記憶體成長
- 修正載入大型會話時記憶體用量高的問題
- 修正執行 Shell 指令且輸出很快時記憶體用量高的問題
- 新增 `/init suppress`，可針對每個儲存庫控制初始化建議
- 連接至 IDE 時於狀態列顯示 IDE 檔案選取指示器
- 儲存庫層級設定可停用個別驗證工具
- ACP 伺服器支援載入現有會話
- alt-screen 模式支援 Page Up/Page Down 鍵盤捲動
- Unix 平台支援 Ctrl+Z 暫停/恢復
- MCP 伺服器 cwd 設定支援波浪符號（~）展開
- 支援 ctrl+n 與 ctrl+p 作為方向鍵替代方案
- 空提示下使用 ctrl+d 離開 CLI
- 修正未知選項 '--no-warnings' 錯誤
- 支援 Shift+Enter 在啟用 kitty 鍵盤通訊協定的終端機插入新行
- MCP 伺服器清單在刪除後選取項目正確調整
- Shell 模式自 Shift+Tab 循環移除，僅能以 `!` 進入
- 優化 /tasks 對話框，圖示與排版更一致
- 離開 alt-screen 不再重播完整會話歷史
- MCP 伺服器錯誤與載入問題於時間軸顯示
- 輸入合併及更順暢的 alt-screen 動畫，減少輸入延遲
- 延伸技能名稱驗證，允許底線、點號與空格；技能前置資料中的名稱與描述成為選填並有合理預設值

## 0.0.409 - 2026-02-12

- /diff 在 alt-screen 模式會全螢幕顯示
- 快速說明覆蓋層：按 `?` 顯示分組捷徑及指令，使用方向鍵導覽
- 主題預覽於螢幕閱讀器模式下顯示於主題清單上方
- 預設 GitHub MCP 設定新增 `list_copilot_spaces` 工具
- 分代理回應完整內容
- CLI 現已整合 VS Code，更多資訊可使用 /ide
- 當權限提示包含長差異內容時，可於 alt-screen 模式中捲動
- 預設插件市集（copilot-plugins、awesome-copilot）協助更容易探索插件

## 0.0.408 - 2026-02-12

- 新增 `/streamer-mode`，串流時隱藏預覽模型名稱及配額詳細資料
- shellId 更靈活，傳入數字時不再出錯
- 背景任務提示於分離 Shell 被關閉或移除時會更新
- --alt-screen 模式新增滑鼠文字選取
- ! 指令大量輸出不再導致 CLI 當機
- alt-screen 模式調整終端機大小時不再產生重複/殭屍行
- MCP 伺服器尊重 `cwd` 工作目錄屬性
- 斜線指令自動完成功能加入子字串比對
- 執行指令快捷鍵由 ctrl+p 改為 ctrl+s

## 0.0.407 - 2026-02-11

- 強化 prompt 模式下的身份驗證錯誤訊息
- 配額超過錯誤會連結至 Copilot 設定頁，並提供具體操作指引
- 主題選擇器可即時預覽差異檔與 Markdown，新增色盲/藍黃盲主題
- 新增 `/on-air` 模式，串流時隱藏模型名稱與配額詳情
- 於 read_agent 時間軸條目中顯示代理型別與敘述
- `/tasks` 顯示背景代理之最新活動
- 新增實驗性替代畫面緩衝區模式：--alt-screen
- 會查詢終端狀態的互動式程式於 shell 中可執行
- 當預設模型被政策阻擋時，分代理將回退使用會話模型
- session.list SDK 回應顯示 Session Context
- 鍵盤快捷鍵提示於 CLI 支援一致的粗體字體
- 新增 `tools.list` RPC，查詢可用內建工具
- 串流回應若被伺服器錯誤中斷自動重試
- 新增永久同意某地點工具權限的選項
- 新增 `/instructions` 指令，可檢視及切換自訂指令檔案
- ctrl-b 及 ctrl-f 移動游標，現所有平台皆可用
- ctrl+d 現優先刪除游標後字元，移至 ctrl+q（或 ctrl+enter）做排隊
- 編輯 MCP 伺服器會顯示現有設定值
- `--resume` 可透過指定 UUID 建立新會話
- 新增工作區端 MCP 設定 `.vscode/mcp.json`
- 透過 `/skills` 指令更動技能即時生效
- /session 指令說明僅顯示可用子指令
- 斜線指令可直接跟提示並換行執行
- 移除狀態列中未預期字元
- 自動駕駛模式支援指定明確工具的自定代理
- 更新 node-pty 解決檔案描述元洩漏
- Windows 下斜線旗標（如 `dir /B`）不再視為檔案路徑
- Diff 模式檔案導覽時不再閃爍
- /mcp disable 與 /mcp enable 若伺服器名稱不存在會顯示明確錯誤
- Microsoft OAuth 的 MCP 伺服器自動設定免手動輸入 client ID
- Tab 正向循環各模式，Shift+Tab 反向；Shell 成獨立模式
- Ctrl+P 執行斜線指令並保留輸入內容（取代引 Ctrl+X → /）
- 終端標題適用於所有 TTY 終端機
- 說明文字註明在 CI 環境下自動更新預設為停用
- 終端頁籤閒置時顯示會話標題
- ask_user 工具一次只問一題，互動更清晰

## 0.0.406 - 2026-02-07

- 新增支援 Claude Opus 4.6 Fast（預覽版）
- Markdown 格式在非互動模式輸出時顯示
- 當使用者沒有 Copilot 訂閱時顯示警告
- 來自外掛的指令現在會轉換為 skills
- 新增 `/changelog` 指令以檢視發行說明
- plugin marketplace add 支援以 URL 作為來源
- `--no-experimental` 旗標可停用實驗性功能
- CLI 介面渲染時不會多出空白行
- `/mcp show` 會顯示 MCP 工具的啟用/停用狀態
- MCP 工具回應現在包含結構化內容（圖片、資源），可於 VS Code 提供更豐富的 UI 顯示

## 0.0.405 - 2026-02-05

- Plugin 和 marketplace 名稱支援大寫字母
- `/experimental` 顯示說明畫面，列出實驗性功能
- 修復 SQL 工具斷線問題
- Plugin 可捆綁 LSP server 設定

## 0.0.404 - 2026-02-05

- 新增 `claude-opus-4.6` 模型支援
- `/allow-all` 和 `/yolo` 立即執行
- MCP server 並行關閉以提升效能
- 取消 `--resume` session picker 以開始新 session
- MCP server 設定在 `tools` 參數未指定時預設包含所有工具
- 新增 `/tasks` 指令以檢視和管理背景工作
- 為所有用戶啟用**背景代理**(background agents)
- 簡化並明確 `/delegate` 指令訊息
- `GITHUB_TOKEN` 環境變數現已可於 agent shell session 存取

## 0.0.403 - 2026-02-04

- Windows 工作管理員顯示正確應用程式名稱
- 新增安全檢查，避免使用應用程式套件外部模組
- ACP 模型資訊包含使用倍數和啟用狀態
- 修復檢查用戶組織成員資格邏輯
- 更新 plugin 前會先停止 MCP server
- 分離的 shell 程序於原生 macOS 安裝可正常運作
- Escape 鍵可中止權限對話框，不論選擇狀態
- Plugin skills 支援 prompt 模式
- CLI 更新設定檔時保留自訂欄位
- 支援模型預設啟用推理摘要
- 自訂 agent frontmatter 支援逗號分隔工具
- frontmatter 欄位未知的 skills 由原本略過改為顯示警告並載入

## 0.0.402 - 2026-02-03

- ACP 伺服器支援「代理」與「計畫」會話模式
- MCP 設定適用於 ACP 模式
- 代理建立精靈介面樣式優化
- 含未知欄位的自訂代理載入時顯示警告而非錯誤
- 自訂代理作為子代理執行時會接收環境內容
- 外掛可為會話生命週期事件提供 hook
- 外掛更新指令支援直接外掛，並能處理 Windows 檔案鎖定
- 移除外掛時會停止 MCP 伺服器

## 0.0.401 - 2026-02-03

- 支援 `.agents/skills` 目錄以自動載入技能
- 當切換模型家族時，改進聊天紀錄處理方式
- MCP 工具回傳 structuredContent 現在可於 CLI 正確顯示
- 支援 Claude 樣式的 .mcp.json 格式且無需 mcpServers 包裹
- 在 VS Code 整合終端機中以 shift+enter 鍵綁定插入換行
- 大型多行貼上可正確運作
- ACP terminal-auth 傳遞正確參數以登入
- 按住箭頭與特殊按鍵可穩定運作
- 斜線指令 ghost text 正確附加
- 新增 `copilot login` 子指令並支援 ACP terminal-auth
- 新增 agentStop 與 subagentStop 鉤子以控制 agent 完成
- CLI 可優雅處理未知按鍵操作
- /diff 以雙欄版面顯示正確行號

## 0.0.400 - 2026-01-30

- 新增 MCP server 指令支援
- 時間軸會顯示使用者對 `ask_user` 工具提示的回應與使用者名稱
- 有序清單以數字顯示而非橫槓
- 新增主題選擇器，透過 `/theme` 指令選擇 GitHub Dark/Light 主題
- 修正在 Windows Terminal 貼上大量內容時的支援
- 改善處理 grep 與 glob 工具大量結果，避免記憶體問題
- CLI 於關閉時會送出 DELETE 請求移除 MCP server
- 修正無法以方向鍵離開選擇清單中的文字輸入欄
- ACP server 支援在工作階段變更模型
- ACP server 支援權限旗標：--yolo、--allow-all 等，及權限設定檔
- 終端分頁在思考時顯示進度指示器
- 移除內建 LSP server（TypeScript、Python）
- 改善與採用 OAuth 的遠端 MCP server 之相容性
- Markdown 表格標題以粗體顯示
- 新增自主任務完成的 autopilot 模式（實驗性）
- 模型選擇器新增模糊搜尋
- 選擇清單中的自由文字輸入可正常運作
- 新增 `copilot plugin` 子指令，支援非互動式外掛管理
- CLI 在訊息數量多的工作階段更為即時回應
- Shell 路徑偵測可更準確處理空白、引號及 Windows 參數
- Diff 模式檔案清單採用旋轉式導覽，一次顯示最多 5 個檔案
- 按住退格鍵可持續刪除文字
- 更佳支援 UNIX 鍵盤綁定（Ctrl+A/E/W/U/K、Alt+方向鍵）以及各種文字輸入欄的多行內容
- 新增 `launch_messages` 設定，用於啟動公告
- 程式碼審查工具處理大量變更時會忽略建置產物，並限制最多 100 個檔案

## 0.0.399 - 2026-01-29

- 壓縮訊息現在顯示更清楚的指令提示，可用於查看檢查點摘要
- 按下 Ctrl+X 然後 / 可執行斜線指令且不會失去輸入內容
- 改善 `/diff` 指令，提供更好的視覺指示與滾動加速
- 新增 `/allow-all` 及 `/yolo` 指令，於會話期間自動核准所有權限
- 建立代理時新增 Copilot 選項，可依初始代理描述自動產生名稱、描述和指示
- 新增 LSP（Language Server Protocol）工具，提供程式碼智能（需啟用實驗功能）
- 會話名稱自動根據第一則訊息由 AI 產生
- 會話歷史壓縮後技能仍然有效
- `/usage` 現在包含來自子代理（如通用代理）的 Token 消耗統計
- 支援以單一檔案方式於 `.claude/commands/` 實作指令，作為技能的簡化替代方案
- 技能可正確於 Windows 載入
- 新增 `/diff` 指令，可檢閱會話變更
- 按兩次 Esc 可復原/回到先前狀態

## 0.0.398 - 2026-01-28

- 修正導致 agent shell 呼叫時出現「Invalid session id」錯誤的回歸問題
- CLI 標頭在終端機寬度較窄時，路徑會使用中間截斷，保留第一個及最後一個資料夾
- 父目錄的 Skills 現在可以呼叫，並且在非 git 目錄也能運作

## 0.0.397 - 2026-01-28

- `/mcp show <server-name>` 會顯示伺服器詳細資訊及可用工具
- 標頭版面配置在終端機寬度較窄時能更好適應
- Plan 模式的輸入文字更易讀
- 貼上超過 30 KB 的內容至提示時，會自動儲存到 workspace 檔案
- Homebrew 工具在 macOS 以 zsh 為預設 shell 時能正確運作
- 新增 --acp 旗標，可作為 Agent Client Protocol server 啟動
- 目錄現在會出現在 @mention 自動完成
- Session 摘要會正確顯示行數

## 0.0.396 - 2026-01-27

- 技能名稱現在可以包含大寫字母
- 在輸入時，Ctrl+E 會將游標移到行尾，不會展開時間軸
- `/skills add` 可用於直接包含 SKILL.md 的目錄
- 子代理時間軸條目會以粗體且大寫名稱顯示
- 時間軸條目對於成功狀態會顯示實心圓
- 改善 UI 元素的水平對齊
- 簡化壓縮時間軸條目
- 透過互動式 CLI 精靈建立自訂代理
- 工具篩選旗標現在也適用於子代理
- 錯誤訊息會統一參照 /login 和 /logout 指令
- 新增 `copilot version` 和 `copilot update` 指令
- preToolUse 鉤子可拒絕工具執行並修改參數
- 修正 bash session 處理時的 PTY 資源釋放問題
- `/plugin install` 支援 GitHub 倉庫、URL 和本地路徑
- 新增 `/experimental` 指令和 `--experimental` 旗標以選用實驗功能
- 新增 `/init` 指令可產生 Copilot 說明
- 重新排序模型選擇器清單以提升組織性
- 插件可提供自訂代理
- 在 WSL 與 devcontainers 下於 VS Code 開啟計劃文件
- /diff 從子目錄執行時會顯示整個儲存庫的更動
- /skills add 在目錄路徑有斜線結尾時能正確計算技能數
- Undo/rewind 會顯示正確的受影響檔案數
- GitHub 預發行版現在會呈現詳細的更新說明

## 0.0.395 - 2026-01-26

- 選擇 Escape 項目時會以閃爍游標提示正在輸入文字
- `/mcp show` 會顯示所有已設定的 MCP 伺服器（包含預設與額外設定的伺服器）
- `/mcp show` 會顯示來自已安裝插件的伺服器
- 在非 git 儲存庫或無提交的儲存庫進行 Rewind 會有明確警告
- 當終端機失去焦點時游標會隱藏
- 捲動時格式化文字與連結會正確顯示
- 在代理 session 中載入本地 shell 設定
- 代理現可使用插件技能
- CLI 缺少 tree-sitter 檔案時不再當機，會平順處理
- 工具執行完成後會在提示模式下顯示
- /diff 模式支援針對行的評論以便回饋

## 0.0.394 - 2026-01-24

- 去除重複的模型說明文件以節省上下文
- 離開摘要會正確顯示使用率指標（不再是零）
- 支援在無提交的儲存庫檢查 git 分支
- /delegate 指令支援 GitHub Enterprise Cloud（*.ghe.com）
- 目錄路徑色調與 git 分支和模型顯示一致
- 插件技能可於代理回覆中使用
- 時間軸會隱藏啟動訊息，減少雜訊
- 修正時間軸條目錯誤，read_agent 及其他工具內容正確顯示
- Git 狀態現在可隨需更新，不再每 15 秒輪詢
- SDK 支援無限 session 並自動壓縮上下文
- 載入記憶體錯誤時會平順處理，使用者不會收到警告
- `/delegate` 指令接受可選提示，並使用會話上下文
- 自動更新時不會移除舊的 CLI 套件版本
- 明確指引分離程序以提升任務完成度
- 隱藏部分鍵盤提示以簡化底部工具列
- 使用 Ctrl+D 佇列斜線指令與訊息
- 在 `/resume` 模式中按 `/` 可搜尋會話

## 0.0.393 - 2026-01-23

- 以時間軸訊息顯示對話壓縮狀態，取代標頭指示器
- Memory 載入在不處於 Git 儲存庫時不再顯示警告
- 新增支援 GHE Cloud (*.ghe.com) 遠端自訂代理
- 套件解除安裝現在能正確運作
- 在 tool.execution_start 事件中公開 MCP server 與 tool 名稱以加強錯誤處理
- 新增 Esc-Esc 可將檔案變更回任何先前快照

## 0.0.392 - 2026-01-22

- 新增 `/plugin` 指令以管理 plugin marketplace
- 新增 `/rename` 指令，作為 `/session rename` 的別名
- 新增 `/plugin update` 指令以更新已安裝的 plugins
- Edit 工具在 timeline 展開時現在會顯示 diff

## 0.0.390 - 2026-01-22

- 壓縮後保留 extended thinking
- 搭配 MCP server 的 custom agent 可避免不必要的重新啟動
- 啟用 plan mode 期間可進行 steering

## 0.0.389 - 2026-01-22

- 改善 `/session` 指令的視覺層級與色彩
- 子代理在使用不同模型時能獲得正確的工具
- grep 與 glob 工具現在能搜尋隱藏檔案與點檔案
- 新增 Windows 用 MSI 安裝程式
- 從 npm 套件移除 Node 版本需求
- MCP 伺服器現在支援使用 OAuth 2.0 進行驗證，並自動管理與更新權杖
- 在時間軸中顯示 MCP 工具的進度訊息
- 外掛可綑綁預設自動載入的 MCP 伺服器
- 可以使用斜線指令 (如 /skill-name) 呼叫技能
- 新增 `/diff` 指令，用於檢視本次 session 期間的變更
- 當儲存庫記憶體載入失敗時顯示警告
- 子代理在請求使用者輸入時不會再卡住
- 速率限制錯誤現在會以易懂訊息顯示重試時間
- `/compact` 執行期間傳送的訊息會自動加入佇列
- 新增 `/models` 作為 `/model` 指令的別名
- 授權變更為 MIT License
- 減少歡迎標題的內距
- Shell 指令（!）可在代理工作時平行執行

## 0.0.388 - 2026-01-20

- 新增 `/review` 指令以分析程式碼變更
- 讓 session 事件訊息更簡潔，視覺上更清爽
- 在自動更新檢查時清理舊的套件版本以釋放磁碟空間
- `--enable-all-github-mcp-tools` 旗標現在可啟用讀寫 GitHub MCP 工具
- `/share gist` 在「具資料駐留功能的 GitHub Enterprise Cloud」上顯示更有幫助的錯誤訊息
- 從 CLI 標頭移除 commit hash
- 重新設計 CLI 標頭，加入品牌吉祥物並精簡歡迎訊息

## 0.0.387 - 2026-01-20

- Skill 工具可處理大型目錄，不會超出 context 限制
- 新增 ask_user 工具用於互動式釐清問題
- 新增 plan 模式與專屬面板以檢視實作計劃

## 0.0.386 - 2026-01-19

- 背景壓縮可正確保留工具呼叫順序
- 新增 `/resume` 指令以切換 session

## 0.0.385 - 2026-01-19

- `store_memory` 工具僅在用戶啟用記憶體時才納入
- 輸入預設提示從「Enter」改為「Type」，避免與 Enter 鍵混淆
- 使用下箭頭鍵瀏覽歷史紀錄時，游標正確定位在行尾
- 新的記憶體功能可在 Copilot 未連結 repository 時順利運作
- Control-C 訊息顯示時間從 1 秒延長為 5 秒
- 在終端分頁標題中顯示目前意圖
- 合併所有自訂指令檔，取代原本的優先序備援方式
- 支援無限 session，透過自動長時間 context 管理與壓縮檢查點
- 在不同自訂 agent 間進行 /agent 切換時管理 MCP 伺服器
- 按下 Escape 可取消手動 `/compact` 指令
- 從 Codex 切換到 Opus 模型時正確保留對話歷史

## 0.0.384 - 2026-01-16

- 新增 `&` 前綴快速鍵，可將提示委派到背景執行（等同於 `/delegate`）
- 按下 Tab 補全會根據已輸入的前綴正確循環，而不是補全後的文字
- 允許使用者設定 gpt 模型的推理努力程度
- MCP 伺服器現已可正確啟動自訂代理人
- Shell 指令失敗時現在會顯示錯誤輸出
- 修正部分情境下壓縮後導致模型呼叫失敗的錯誤

## 0.0.383 - 2026-01-15

- 登入流程遵守 OAuth slow_down 間隔且加入偵錯日誌
- 自訂代理人探索現已會追蹤至代理人定義檔的符號連結
- 增加自訂代理人委派的額外提示
- 新增 `/cd` 作為 `/cwd` 指令的別名
- 由 CLI 建立的檔案支援 @提及
- 啟用 Anthropic Claude 模型的延伸推理功能
- 螢幕閱讀模式登入時顯示靜態文字，取代動畫載入圖示
- 選擇「允許本次階段使用」現在會自動批准同類型的平行處理權限待審請求
- 推理檢視設定可跨會話持續保存
- 當儲存庫不存在或被拒絕存取時提供更明確的錯誤訊息
- 在提示中注入儲存庫記憶並新增記憶存儲工具，可跨會話記住事實
- Copilot 延遲讀取 shell 輸出時顯示延遲時間
- 支援無協定的 proxy URL（如 localhost:9999）

## 0.0.382 - 2026-01-14

- 新增支援 GPT-5.2-Codex 模型
- 新增 `--config-dir` 參數，可自訂設定目錄位置

## 0.0.381 - 2026-01-13

- 新增 --allow-all 和 --yolo 旗標，可一次啟用所有權限
- 幽靈文字和 Tab 補全在輸入像是 '/q' 這類斜線指令時會正確顯示對應別名（例如 '/quit'）
- 新增 `/new` 作為 `/clear` 指令的別名
- Shell 模式歷史記錄導航現在會依目前前綴過濾——例如輸入 `!git` 並按上箭頭時只會循環顯示過去的 git 指令

## 0.0.380 - 2026-01-13

- 取得模型能更妥善處理受到防火牆保護的路由錯誤，並適當拋出錯誤
- Bash 指令文字與時間軸事件的輸出對齊
- 大型輸出提示現在會根據不同內容類型（包含 JSON）建議合適工具
- `--agent` 旗標現在可於互動模式中使用
- 當拒絕工具權限請求時即時提供回饋，使代理不因拒絕權限而必須停止
- web-fetch 工具現在會拒絕 `file://` URL，並建議改用 view 工具
- 終端機的跳脫序列不再顯示為文字輸入
- 自動壓縮在背景執行，不會阻塞對話
- 終止訊號現在可傳遞至子代理，任務取消可停止所有巢狀代理工作
- 任務工具支援自訂代理工具別名
- 使用 view_range 參數時允許讀取大於 10MB 的檔案
- 有大量對話歷史的工作階段開啟時載入速度加快
- 於 Copilot 思考時即可傳送訊息來引導或佇列

## 0.0.377 - 2026-01-08

- 大型檔案訊息現在鼓勵使用 view_range 以漸進式閱讀，而非完全阻止所有閱讀

## 0.0.376 - 2026-01-08

- 透過 GraphQL ID 或工作階段選擇器載入遠端工作階段
- 任務工具子代理現在可以處理圖片
- 降版 CLI 版本不再需要手動清除已下載的套件
- 大型工具輸出寫入磁碟，並鼓勵模型使用高效搜尋工具

## 0.0.375 - 2026-01-07

- 新增 Ctrl+T 切換推理摘要，支援的模型適用
- 新增 --share 及 --share-gist 旗標，讓工作階段能在非互動模式下分享
- 檔案編輯在核准多個並行編輯時不再卡住
- 有推理內容的回應不再導致助理訊息重複
- 子代理執行完成後關閉 MCP 伺服器
- SVG 檔案現在以文字檔案而非二進位圖片處理
- 修復因訂閱式路由用於聊天補全導致的『Connection Error』問題

## 0.0.374 - 2026-01-02

- MCP 伺服器類型說明文字會顯示正確的選項
- 模型選擇器在模型無法使用時會顯示更清楚的訊息並附上設定連結
- 新增自動壓縮於 95% Token 上限及 `/compact` 指令
- 內建子代理可用於探索及管理任務
- 內建 `web_fetch` 工具，可抓取網頁內容

## 0.0.373 - 2025-12-30

- 分頁補齊已支援 `/cwd` 及 `/add-dir` 指令的路徑參數
- 在 GitHub MCP 伺服器啟用 Copilot Spaces 工具
- GitHub URL 現已正確解析 GHE
- kill 指令過濾現在允許在“kill”作為參數時執行指令
- 裝置驗證碼授權輪詢將會立即開始，無須等待剪貼簿或瀏覽器

## 0.0.372 - 2025-12-19

- 直接在 CLI 中啟用禁用的模型以選擇或指定它們
- 新增 `/context` 命令以視覺化顯示 token 使用情況
- 新增 `--resume` 標示以在本地繼續遠端會話
- 新增影響存取網頁的一般 shell 命令的 URL 權限控制
- 長命令過長時不再顯示重複的意圖標題

## 0.0.371 - 2025-12-18

- 正常文字遵循終端的預設前景色
- 更新技能幫助文字以引用正確的 ~/.copilot/skills/ 目錄

## 0.0.370 - 2025-12-18

- 使用 --disable-mcp-server 時，禁用的 MCP 伺服器現在被正確忽略
- 共用會話正確呈現巢狀的 markdown 程式碼區塊
- 日誌級別現在輸出該級別及更高嚴重性的所有訊息
- 從系統和環境變數載入 CA 憑證
- 改善 `/model` 錯誤訊息以顯示可用和不可用的模型
- 模型選擇器使用兩欄佈局，對齊的乘數和更清晰的視覺指示器
- 為 CLI 配置 UI 中的 MCP 伺服器新增 STDIO 類型作為 Local 的同義詞
- 差異顯示使用您配置的 git 分頁器 (如 delta、diff-so-fancy)
- 使用 npm install 的平台專屬可執行文件（當可用時）
- 在釋出中發佈 CLI 可執行文件的 SHA256 校驗和
- 新增 --available-tools 和 --excluded-tools 來篩選模型可使用的工具
- 確保根據橫幅和螢幕閱讀器首選項顯示動畫或非動畫橫幅
- 修正 codex 模型的截斷邏輯

## 0.0.369 - 2025-12-11

- 增加對 GPT-5.2 的支援

## 0.0.368 - 2025-12-10

- PRU (Premium Request Unit) 使用率現在正確顯示
- 修正勾選框和叉號圖示的渲染
- 新增 grep 工具 Codex 模型
- Numpad 鍵可在 Kitty 鍵盤協議中使用於提示

## 0.0.367 - 2025-12-04

- `GPT-5.1-Codex-Max` 現在可在 GitHub Copilot CLI 中使用

## 0.0.366 - 2025-12-03

- 添加 `infer` 屬性以控制自訂代理工具的可見性
- 在 GitHub 版本工件中新增 CLI 可執行檔
- 為 OpenAI Codex 模型添加 `apply_patch` 工具鏈

## 0.0.365 - 2025-11-25

- 添加 `--silent` 選項以在指令碼中隱藏統計輸出

## 0.0.364 - 2025-11-25

- 新增語法突顯於差異
- 修正淺色主題 markdown 呈現

## 0.0.363 - 2025-11-24

- Opus 4.5、GPT-4.1 和 GPT-5-Mini 現已在 GitHub Copilot CLI 中可用
- 貼上影像資料時，現在優先處理影像文件內容而非其文件圖示
- 改進 shell 工具名稱的時間軸呈現
- 新增支援 GITHUB_ASKPASS 環境變數進行認證
- MCP 伺服器在 `--prompt` 模式下工作

## 0.0.362 - 2025-11-20

- 修正 Windows 上影像拖放問題
- Shell 指令不再包含於 Bash 和 PowerShell 的歷史紀錄文件中
- 可直接從剪貼簿將影像資料貼入 CLI
- 清理並更新提示及工具說明以更流暢

## 0.0.360 - 2025-11-18

- 修正檔案操作在等待使用者許可時超時問題

## 0.0.359 - 2025-11-17

- 支援透過拖放及貼上影像文件路徑將影像加入到上下文。改進影像標籤在輸入框中的呈現
- 新增 `/share` 指令以將會話儲存為 markdown 文件或 GitHub gist
- 修正快取的權杖在會話結束時顯示為零的錯誤
- 啟用 `USE_BUILTIN_RIPGREP` 環境變數以選擇從 PATH 使用 ripgrep
- 修正從遠端存儲庫的默認分支來源自訂代理時導致的本地副本混淆問題
- 修正自訂代理的配置問題
- 改善 `Ctrl+C` 的效能
- 提高工具參數解析的安全性
- 區分工具名稱和路徑並改進工具成功/錯誤圖示
- `copilot -p` 將不再互動式請求許可
- 移除工具描述中不必要的空白符

## 0.0.358 - 2025-11-14

修復發布以解決 GPT-5.1、GPT-5.1-Codex 和 GPT-5.1-Codex-Mini 模型的可用性問題。

## 0.0.357 - 2025-11-13

修復發布以解決圖片調整大小的問題。

## 0.0.356 - 2025-11-13

- GPT-5.1、GPT-5.1-Codex 和 GPT-5.1-Codex-Mini 現已在 GitHub Copilot CLI 中可用。詳情請參閱 [GitHub 更新日誌](https://github.blog/changelog/2025-11-13-openais-gpt-5-1-gpt-5-1-codex-and-gpt-5-1-codex-mini-are-now-in-public-preview-for-github-copilot/)

## 0.0.355 - 2025-11-12

- 啟用 CLI 代理讀取自身的 `/help` 和 README 以回答有關其功能的問題
- 改進對 VSCode 格式自訂代理 (`.agent.md` 後綴) 的解析
- 清理工具名稱以修復類似 https://github.com/github/copilot-cli/issues/456 的問題
- 內建 `ripgrep` 並新增 `grep` 和 `glob` 工具，以更高效地搜尋程式碼庫
- 修復畸形工具呼叫在到達 UI 之前的處理 (部分解決 https://github.com/github/copilot-cli/issues/393)
- 防止 Markdown 訊息中的雙重換行
- 修復檔案選擇器在多行輸入中使用時導致非預期上下箭頭行為的錯誤 (修復 https://github.com/github/copilot-cli/issues/350)
- 修復自訂代理中遠端 MCP 伺服器配置未正確獲取的錯誤
- 為 `/session` 命令的輸出增加更多細節並改進樣式
- 從 Shell 工具的環境中移除內部 `NODE_ENV` 變數 (修復 https://github.com/github/copilot-cli/issues/151)
- 修復使用互動式 Shell 工具時的記憶體洩漏
- 改進檔案檢視輸出中的行號格式 (修復 https://github.com/github/copilot-cli/issues/471)
- 降低預設 Shell 工具逾時時間，並更新提示語言以不暗示逾時即為失敗
- 確保在渲染前查詢終端背景色 (修復 https://github.com/github/copilot-cli/issues/36)
- 確保代理不會對自己的 PID 執行 `pkill`
- 修復 `copilot` 在收到中止信號後不會退出的錯誤 (修復 https://github.com/github/copilot-cli/issues/529)
- 確保 Windows 上的 `!` 命令在可用時使用 PowerShell (修復 https://github.com/github/copilot-cli/issues/504)
- 修復 Windows Terminal 中不接受鍵盤輸入的錯誤

## 0.0.354 - 2025-11-03

- 當 `-p` 模式因大型語言模型後端錯誤 (認證失敗、配額耗盡、網路問題) 而失敗時，程式會以非零狀態碼退出
- 支援 MCP 伺服器工具通知
- 支援以 `COPILOT_GITHUB_TOKEN` 環境變數進行驗證 (優先於 `GH_TOKEN`)
- 改進 Shell 命令安全性，對命令外的 heredoc 處理更為健全
- 差異區塊 (diff hunk) 行現在會正確填滿差異框的寬度
- 在 GitHub Actions 環境中的 MCP 伺服器會自動使用 `GITHUB_WORKSPACE` 作為工作目錄
- 當沒有本地變更時，`/delegate` 命令現在能正確運作
- 檔名含特殊字元的自訂代理檔案不再導致失敗
- 在使用 `/model` 命令選擇不支援的模型時，錯誤訊息更清楚
- 當使用不同的 OpenAI base URL 時，替代模型提供者現在能正確運作

## 0.0.353 - 2025-10-28

- 新增自訂代理支援。自訂代理定義從 `~/.copilot/agents`、儲存庫中的 `.github/agents` 或組織的 `.github` 儲存庫提取。您可以在互動模式下使用 `/agent` 斜線命令明確呼叫代理，或在非互動模式下使用 `--agent <agent>` 參數。代理也會作為工具提供給模型在完成任務時呼叫
- 新增 `/delegate` 命令，可異步委派任務給 Copilot 程式碼代理。任何未暫存的變更將被提交到新分支，並在您的 GitHub 儲存庫中開啟 PR，Copilot 將在背景中完成工作。

## 0.0.352 - 2025-10-27

- 改進包含斜線的 MCP 工具處理
- 改進當使用不支援的模型時 `/model <model>` 命令的錯誤訊息

## 0.0.351 - 2025-10-24

- 改進路徑偵測啟發式演算法，以避免各種煩人且不必要的權限請求：
  - 執行許多已知為唯讀的標準 bash/PowerShell 命令 (部分修復 https://github.com/github/sweagentd/issues/7372)
  - PowerShell 中的 `npm test -- --something` 等命令
  - 在您已授予寫入權限的路徑中的 Shell 重導向，如 `> some_file.txt`、`> /dev/null` 和 `2>&1` (修復 https://github.com/github/copilot-cli/issues/211)
  - `gh api` 的參數，如 `gh api /repos/user/repo/ec` (修復 https://github.com/github/copilot-cli/issues/216)
- 改進 Sonnet 4.5 的提示，以減少工作區中留下的中間 markdown 檔案數量
- 👀 ... 我們在 [GitHub Universe](https://githubuniverse.com/) 見！

## 0.0.350 - 2025-10-23

- 為了節省情境視窗空間，我們限制了預設 GitHub MCP 伺服器可用的工具清單。在我們的測試中，模型將使用 [GitHub CLI, `gh`](https://github.com/cli/cli)(如果已安裝) 來取代缺少的 MCP 工具。如果您希望開啟所有可用工具，我們新增了 `--enable-all-github-mcp-tools` 旗標。
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
- 將 `sharp` 相依套件整合到 CLI 套件中 —— 我們離實作 https://github.com/github/copilot-cli/issues/16 更近一步，這也修復了 Windows 上的一些啟動阻礙問題 (修復 https://github.com/github/copilot-cli/issues/309 和 https://github.com/github/copilot-cli/issues/287)
- 修復輸入權杖未正確追蹤的錯誤 (修復 https://github.com/github/copilot-cli/issues/337)
- 修復啟用串流時帶有參數的 MCP 工具會失敗的錯誤
- 新增額外的除錯記錄，有助於我們調查 https://github.com/github/copilot-cli/issues/346

## 0.0.349 - 2025-10-22

- 模型現在可以平行呼叫多個工具。每個工具必須事先確認。此行為可以使用 `--disable-parallel-tools-execution` 旗標停用
- 新增 `/quit` 作為 `/exit` 的別名 (修復 https://github.com/github/copilot-cli/issues/357)
- 修復每個串流輸出區塊都被作為對話的一部分傳回模型的錯誤 (修復 https://github.com/github/copilot-cli/issues/379)
- 確保在執行路徑權限檢查之前展開環境變數
- 修復 Ctrl+K 刪除到輸入框視覺行結尾而不是邏輯行結尾的錯誤
- 將暫存目錄新增到模型預設可存取的路徑中 (修復 https://github.com/github/copilot-cli/issues/306)

## 0.0.348 - 2025-10-21

- Copilot 的輸出現在會逐個權杖串流！可以使用 `--stream off` 停用此功能
- 改進 Copilot CLI 的記憶體佔用，特別是在處理產生大量輸出的 Shell 命令時
- 確保在使用 `/terminal-setup` 時保留 VSCode 設定檔中的註解 (修復 https://github.com/github/copilot-cli/issues/325)
- 將 `node-pty` 整合到 CLI 套件中 —— 我們離實作 https://github.com/github/copilot-cli/issues/16 更近一步
- 修復本地工具呼叫中斷會話的問題 (修復 https://github.com/github/copilot-cli/issues/365、https://github.com/github/copilot-cli/issues/364、https://github.com/github/copilot-cli/issues/366)
- 將 LICENSE.md 新增到我們的 Node 套件中 (修復 https://github.com/github/copilot-cli/issues/371)
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

- 修復某些使用者的進階請求被過度計算的錯誤 (https://github.com/github/copilot-cli/issues/351)。如果您受到影響，我們正在努力退還您被多收的進階請求！

## 0.0.344 - 2025-10-17

- 在提示模式中啟用 GitHub MCP 伺服器
- 新增對 bash 工具執行分離程序的支援
- 在 `copilot help config` 文字中新增支援的模型清單
- 修復會話中止處理，以在按下 <kbd>Esc</kbd> 或強制退出時正確清理孤立的工具呼叫
- 在啟動時強制執行最低 Node 版本要求
- 簡化 `/terminal-setup` 的訊息

## 0.0.343 - 2025-10-16

- 新增模型：執行 `/model` 斜線命令可選擇 Haiku 4.5。
- 新增旗標以增強 MCP 伺服器設定，可在每個會話中暫時新增或覆寫伺服器設定：`--additional-mcp-config` (修復 https://github.com/github/copilot-cli/issues/288)
  - 您可以用兩種方式傳遞 MCP 伺服器設定：
    - 內嵌 JSON：`copilot --additional-mcp-config '{"mcpServers": {"my-tool": {...}}}'`
    - 從檔案讀取 (前綴為 @)：`copilot --additional-mcp-config @/path/to/config.json`
  - 您也可以多次傳遞此旗標 (後面的值會覆寫前面的值)：`copilot --additional-mcp-config @base.json --additional-mcp-config @overrides.json`
- 改進提示以確保代理在 Windows 上使用 Windows 樣式的路徑 (修復 https://github.com/github/copilot-cli/issues/261)
- 新增提示，建議使用者在需要啟用多行輸入時執行 `/terminal-setup`
- 各種視覺改進：
  - 在「Thinking...」指示器新增閃爍效果
  - 移除時間軸中使用者訊息周圍的方框
  - 增加差異中已移除行內高亮的對比度
  - 允許在斜線命令中循環瀏覽 (從清單底部回到頂部)
  - 對齊權限 / 確認提示，確保所有提示使用相同的視覺樣式

## 0.0.342 - 2025-10-15

- 全面改版我們的會話記錄格式：
  - 引入新的會話記錄格式，將我們儲存會話的方式與在時間軸中顯示它們的方式分離。新格式更清晰、更簡潔且可擴充，未來將更容易實作新功能。
  - 新會話儲存在 `~/.copilot/session-state`
  - 舊版會話儲存在 `~/.copilot/history-session-state` —— 當您從 `copilot --resume` 恢復時，這些會話將遷移到新格式和位置
- 預設啟用 Kitty 協定。支援 Kitty 協定的終端機現在可以透過 Shift+Ctrl 支援多行輸入。透過執行 `/terminal-setup` 命令，在 VSCode 及其分支中也支援多行輸入 (修復 https://github.com/github/copilot-cli/issues/14)
- 透過遵循 `GH_HOST` 環境變數來啟用 PAT 和 `gh` 驗證模式的非互動式 GHE 登入 (修復 https://github.com/github/copilot-cli/issues/296)
- 透過在 `~/.copilot/config` 中新增持久性的 `log_level` 選項，改進除錯日誌收集的便利性。可能的值：`["none", "error", "warning", "info", "debug", "all", "default"]`
- 在呼叫 `/model` 導致 Copilot API 錯誤時新增除錯記錄。這應該有助於我們診斷一些政策 / 模型存取邊緣案例，如 https://github.com/github/copilot-cli/issues/268 和 https://github.com/github/copilot-cli/issues/116
- 將 `gradlew` 新增到可列入白名單的子命令清單中 (修復 https://github.com/github/copilot-cli/issues/217#issuecomment-3393844685)
- 修復 MCP 工具呼叫失敗後會話可能進入卡住狀態的錯誤 (修復 https://github.com/github/copilot-cli/issues/312)
- 使 `--help` 文字的輸出更簡潔

## 0.0.341 - 2025-10-14

- 新增 `/terminal-setup` 命令，用於在未實作 kitty 協定的終端機上設定多行輸入
- 修復拒絕 MCP 工具呼叫會拒絕所有未來工具呼叫的錯誤 (修復 https://github.com/github/copilot-cli/issues/290)
- 修復使用參數呼叫 `/model` 無法正常運作的迴歸問題
- 在 `/model` 清單中新增每個模型的進階請求乘數 (目前，我們支援的所有模型都是 1x)

## 0.0.340 - 2025-10-13

- 移除「Windows 支援為實驗性質」的警告 -- 在過去兩週，我們在改進 Windows 支援方面取得了一些重大進展！請繼續回報任何問題 / 回饋
- 改進透過包含模型呼叫錯誤的 Copilot API 請求 ID 和用戶端錯誤的堆疊追蹤來改進除錯
- 修復連續的孤立工具呼叫會導致 "Each `tool_use` block must have a corresponding `tool_result` block in the next message" 訊息的問題（修復 https://github.com/github/copilot-cli/issues/102)
- 新增在 `-p` 模式中新增核准新路徑的提示。也新增了 `--allow-all-paths` 參數來核准存取所有路徑。
- 變更 MCP 伺服器設定中環境變數的解析，將 `env` 區段的值視為字面值（修復 https://github.com/github/copilot-cli/issues/26).
  已為 CLI 設定 MCP 伺服器的客戶需要對其 `~/.copilot/mcp-config.json` 進行小幅修改。對於任何已新增帶有 `env` 區段的伺服器，他們需要在每個 env 區塊條目的鍵值對的「值」部分開頭新增 `$`，以便將值視為環境變數的參考。

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

- 改進 `/mcp add` 中 MCP 伺服器的參數輸入 —— 以前，使用者必須使用逗號分隔語法來指定參數。現在，「Command」欄位允許使用者輸入完整命令來啟動伺服器，就像在 Shell 中執行一樣
- 修復使用 Kitty 協定時導致包含 `u` 的文字無法正確貼上的錯誤。Kitty 協定支援仍在 `COPILOT_KITTY` 環境變數後面。(修復 https://github.com/github/copilot-cli/issues/259)
- 修復使用 Kitty 協定時導致程序在 Windows 的 VSCode 終端機中掛起的錯誤。Kitty 協定支援仍在 `COPILOT_KITTY` 環境變數後面。(修復 https://github.com/github/copilot-cli/issues/257)
- 改進當沒有可用模型時 `/model` 選擇器的錯誤處理 (修復 https://github.com/github/copilot-cli/issues/229)

## 0.0.338 - 2025-10-09

- 將 Kitty 協定支援移至 `COPILOT_KITTY` 環境變數後面，因為觀察到迴歸問題 (https://github.com/github/copilot-cli/issues/257、https://github.com/github/copilot-cli/issues/259)
- 修復多行提示中有空行時的換行問題

## 0.0.337 - 2025-10-08

- 新增 MCP 伺服器名稱的驗證 (修復 https://github.com/github/copilot-cli/issues/110)
- 新增 Ctrl+B 和 Ctrl+F 的支援，用於向後和向前移動游標 (修復 https://github.com/github/copilot-cli/issues/214)
- 新增支援 [Kitty 協定](https://sw.kovidgoyal.net/kitty/keyboard-protocol/) 的終端機的多行輸入 (部分修復 https://github.com/github/copilot-cli/issues/14—— 更廣泛的終端機支援即將推出！)
- 更新 OAuth 登入 UI，使其在產生裝置代碼後立即開始輪詢 (這將更穩固地修復 https://github.com/github/copilot-cli/issues/89 中描述的 SSH 邊緣案例)

## 0.0.336 - 2025-10-07

- 啟用透過 HTTPS_PROXY/HTTP_PROXY 環境變數的代理支援，無論 Node 版本為何 (修復 https://github.com/github/copilot-cli/issues/41)
- 大幅減少權杖消耗、每個問題的往返次數和得到結果的時間。我們將在週五的每週變更日誌中分享更具體的資料！
- 改進檔案寫入效能 (特別是在 Windows 上)，不再依賴 Shell 來獲取當前工作目錄
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
- 在嘗試在無法運作的環境中使用代理支援時新增警告 (Node <24，未設定所需的環境變數)(https://github.com/github/copilot-cli/issues/41 的更永久修復即將在明天推出)
- 將情境截斷訊息的顏色從錯誤顏色更新為警告顏色
- 修復 `copilot` 日誌可能未在 Windows 上正確建立的錯誤
- 修復使用自訂設定檔的 Powershell 使用者可能在執行命令時遇到問題的錯誤 (修復 https://github.com/github/copilot-cli/issues/196)
- 修復貼上後提示被截斷以及其他邊緣案例的錯誤 (修復 https://github.com/github/copilot-cli/issues/208、https://github.com/github/copilot-cli/issues/218)
- 修復儘管已登入，使用者在啟動時仍會看到登入提示的錯誤 (修復 https://github.com/github/copilot-cli/issues/202)
- 修復某些環境中的某些 SSH 使用者無法取得 OAuth 登入連結，且其程序在嘗試開啟瀏覽器時掛起的錯誤 (修復 https://github.com/github/copilot-cli/issues/89)

## 0.0.334 - 2025-10-03

- 改進貼上大量內容的體驗：貼上超過 10 行時，會顯示為緊湊的權杖，如 `[Paste #1 - 15 lines]` 而不是讓終端機被大量文字淹沒。
- 新增當對話情境接近模型限制的 ≤20% 時新增警告，表示即將發生截斷。此時，我們建議您開始新的會話 (improves https://github.com/github/copilot-cli/issues/29)
- 移除從持久化的會話歷史記錄中移除退出時的使用統計資料
- 新增在啟動日誌中新增當前版本，以協助錯誤回報
- 移除如果存在參數，則移除透過 TAB 在自動完成項目中循環的功能。這可防止執行 `/cwd /path/to/whatever`，按下 `TAB`，然後看到 `/clear` 自動完成

## 0.0.333 - 2025-10-02

- 新增影像支援！ `@`- 提及檔案以將它們新增為模型的輸入。
- 改進 Node.JS v24+ 使用者的代理支援。詳情請參閱 [this comment](https://github.com/github/copilot-cli/issues/41#issuecomment-3362444262) 以獲取更多詳細資訊 (Fixes https://github.com/github/copilot-cli/issues/41)
- 新增直接執行 Shell 命令並透過在輸入前加上 `!` (fixes https://github.com/github/copilot-cli/issues/186, https://github.com/github/copilot-cli/issues/12)
- 新增 `/usage` 斜線命令，提供有關進階請求使用、會話時間、程式碼變更和每個模型權杖使用的統計資料。此資訊也會在會話結束時列印 (Fixes https://github.com/github/copilot-cli/issues/27, https://github.com/github/copilot-cli/issues/121)
- 改進 `--screen-reader` 模式，用資訊性標籤替換時間軸中的圖示
- 新增 a `--continue` 旗標來恢復最近關閉的會話
- 更新 `/clear` 命令以正確清除舊的時間軸條目 / 會話資訊 (Fixes https://github.com/github/copilot-cli/issues/170)

## 0.0.332 - 2025-10-01

- 切換使用符合 [GitHub's docs](https://docs.github.com/en/copilot/how-tos/administer-copilot/manage-for-enterprise/manage-access/manage-network-access) (fixes https://github.com/github/copilot-cli/issues/76)
- 修復 `/user [list | show | swtich]` 未包含從所有驗證模式登入的使用者 (fixes https://github.com/github/copilot-cli/issues/58)
- 修復 使用 `/user switch` 切換到另一個使用者時未在 GitHub MCP 伺服器中生效
- 改進透過在 `@` 檔案選擇器、 `--resume` 會話選擇器和 `/` 命令選擇器中停用捲軸來改進螢幕閱讀器體驗
- 改進捲軸容器的精緻度 (增加寬度，降低槽的不透明度)
- 輸入區域的小視覺改進 (將當前模型指示器移至右側，使其不與 CWD 擁擠，改進檔案選擇器的 "indexing" 指示器的位置，改進完成選單中的提示格式)
- 改進透過排除標題中的 `#` 前綴來改進 Markdown 易讀性
- 改進我們如何從 Shell 命令中提取路徑以進行權限處理（可能修復 https://github.com/github/copilot-cli/issues/159, https://github.com/github/copilot-cli/issues/67)

## 0.0.331 - 2025-10-01

- 改進檔案讀取 / 編輯時間軸事件的資訊密度
- 修復 `--banner` 說明文字中的不準確之處；它以前暗示會持續變更設定以始終顯示啟動橫幅
- 改進 `/model` 清單，以確保使用者只看到他們有權使用的模型 —— 以前，如果使用者嘗試使用他們無權存取的模型 (由於其 Copilot 方案、地理區域等)，他們會收到 `model_not_supported` 錯誤。這應該透過甚至不在清單中將此類模型顯示為選項來防止這種情況 (Fixes https://github.com/github/copilot-cli/issues/112, https://github.com/github/copilot-cli/issues/85, https://github.com/github/copilot-cli/issues/40)
- 修復在多行提示中按向下箭頭會繞回到第一行的錯誤 (這是實作 https://github.com/github/copilot-cli/issues/14 的過程中)
- 將捲軸新增到 `@` 檔案提及選擇器，並將活動緩衝區的大小增加到 10 個項目
- 改進當代理執行時撰寫提示的體驗 —— 上 / 下箭頭現在將在 `@` 和 `/` 選單中正確導航選項

## 0.0.330 - 2025-09-29

- 將預設模型改回 Sonnet 4，因為 Sonnet 4.5 尚未向所有使用者推出。Sonnet 4.5 仍可從 `/model` 斜線命令取得

## 0.0.329 - 2025-09-29

- 新增對 [Claude Sonnet 4.5](https://github.blog/changelog/2025-09-29-anthropic-claude-sonnet-4-5-is-in-public-preview-for-github-copilot/) 的支援並使其成為預設模型
- 新增 `/model` 斜線命令以輕鬆變更模型 (修復 https://github.com/github/copilot-cli/issues/10)
  - `/model` 將開啟選擇器以變更模型
  - `/model <model>` 將模型設定為提供的參數
- 在輸入文字方塊上方顯示當前選擇的模型 (解決 https://github.com/github/copilot-cli/issues/120、https://github.com/github/copilot-cli/issues/108 中的回饋)
- 改進當使用者提供不正確的命令列參數時的錯誤訊息。(解決 https://github.com/github/copilot-cli/issues/96 對非互動模式可發現性的回饋)
- 變更 `Ctrl+r` 的行為，使其僅展開最近的時間軸項目。執行 `Ctrl+r` 後，您可以使用 `Ctrl+e` 展開全部
- 改進單字移動邏輯以更好地偵測換行：使用單字移動鍵現在將正確移動到行中的第一個單字
- 改進輸入框中多行輸入的處理：輸入文字方塊可捲動，限制為 10 行。長提示不會再佔據整個螢幕！(這是實作 https://github.com/github/copilot-cli/issues/14 的過程中)
- 移除輸入框的左右邊框。這使得從中複製文字變得更容易！
- 新增 glob 比對到 Shell 規則。使用 `--allow-tool` 和 `--deny-tool` 時，您現在可以指定像 `shell(npm run test:*)` 這樣的內容，以比對以 `npm run test` 開頭的任何 Shell 命令
- 改進 `copilot --resume` 介面，具有相對時間顯示、會話訊息計數 (修復 https://github.com/github/copilot-cli/issues/97)

## 0.0.328 - 2025-09-26

- 改進當 Copilot CLI 被組織政策封鎖時收到的錯誤訊息 (修復 https://github.com/github/copilot-cli/issues/18 )
- 改進當使用缺少「Copilot Requests」權限的 PAT 時收到的錯誤訊息 (修復 https://github.com/github/copilot-cli/issues/46 )
- 改進 `/user list` 的輸出，使當前使用者更清楚
- 改進對 `ForEach-Object` 的 PowerShell 解析以及命令名稱表達式的偵測 (例如 `& $someCommand`)
