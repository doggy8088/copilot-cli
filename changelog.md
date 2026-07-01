## 1.0.68 - 2026-07-01

- 新增對 `kimi-k2.7-code` 模型的支援
- `/mcp` 設定表單中目前聚焦的欄位，現在會以 `"❯ "` 箭頭標示，而不再只靠顏色區分
- 在 IDE 短暫中斷連線期間，會保留 IDE tools 可用性；斷線時回傳清楚的錯誤，IDE 重新連線後會自動恢復
- Tab 補全現在會內嵌顯示 slash command aliases（例如 `/pr automerge|agentmerge`）
- 當工作階段的工作目錄或 git worktree 已被刪除時，hooks 不再報錯並拒絕所有工具
- 當 reasoning effort 或 context tier 變更時，保持頁尾的模型狀態同步更新
- 避免來自符號連結掃描根目錄的重複 skill 與命令解析錯誤
- 在執行 `/cd` 與 `/worktree` 後更新 Sessions 側邊欄中的 branch
- 在 Windows 上，可在 Win32 extended-length paths 下找到 agents 與 instructions
- 顯示 slash-command 輸入選項的說明
- 避免在 macOS 上複製已選取的時間線文字時造成終端機顯示損壞
- 將符號連結的 sandbox 路徑折疊為單一列
- 可從 agents 畫面瀏覽、恢復與切換工作階段
- Code review 在收集變更時，會重試暫時性的 git 失敗
- 略過格式錯誤的 plugin manifests，並繼續載入有效的 plugins
- 針對支援的方案，在狀態列與 `/usage` 中顯示 plan budget 詳細資訊
- 在裁切輸出中正確渲染泰文與天城文文字
- 保持檔案編輯與 patch 都遵守 sandbox 檔案系統政策
- 在終端機輸出中保留被換行包裹的 OSC 8 超連結 ID
- 允許 device-managed settings 覆寫 server-managed settings
- 在 skill prompt context 中保留內嵌的 `/skill` tokens
- 讓 git commands 可從 sandbox 中的 repo 子目錄運作
- PowerShell 變數參照不再觸發 content-policy 拒絕
- 當工作目錄在不同 turn 之間變更時通知代理，讓它在執行命令與解析相對路徑時使用新目錄
- 互動式工作階段預設改用穩定的垂直線游標
- 啟動時停用游標閃爍，但不改變游標形狀
- 拒絕與其他清單中的符號連結衝突的 sandbox 路徑編輯
- 當 slash-command picker 開啟時，保持狀態列可見
- Custom agents 在巢狀 subagents 中保留其工具篩選條件
- 在 `/diagnose` 工作階段日誌摘錄中保留多位元組字元（emoji、重音字母、非拉丁文字）

## 1.0.67 - 2026-06-30

- 在本次工作階段剩餘時間停用 sandbox，現在會立即生效，因此 shell 與 search commands 不會在同一個 turn 中再次提示你繞過 sandbox
- Subagent 工作階段現在會保留父層工具限制
- 當 host custom agents 載入失敗時，現在會顯示警告與錯誤
- 要求 session limits 至少為 30 AI credits
- 新增對 Claude Sonnet 5 的支援
- 當 hooks 逾時時，仍允許 tool calls 繼續執行
- `Ctrl+Q` 現在會將目前反白的 slash-command argument completion 加入佇列
- 針對位於 tenant vanity domain 後方的 Microsoft Entra servers（例如 Copilot Studio）進行 MCP OAuth 時，不再發生無法 refresh 或重新驗證的問題（AADSTS9010010 / AADSTS90023）
- Prompt mode 的結束摘要現在會顯示 resume 提示，方便你繼續該工作階段

## 1.0.66 - 2026-06-30

- 在互動式工作階段中，現在會使用不閃爍的區塊游標，並在結束時還原終端機的預設游標
- 新增對 Claude Opus 4.8 Fast 的支援，並淘汰 Claude Opus 4.6 Fast
- MCP 新增／編輯表單現在接受 HTTP 風格的 `Key: value` headers
- 避免 LSP servers 在啟動期間重複啟動兩次
- 避免封鎖包含 Windows 風格路徑片段的命令
- 讓 Copilot 可以讀取已分離背景 shell commands 的輸出並停止它們
- 大量輸出處理現在會遵守自訂輸出目錄與停用設定
- 防止在 assistant 回覆為空時，產生 PR 描述導致當機
- 現在會將時間線渲染為緊湊的「精華片段」樣式，為所有使用者顯示單行的工具與 reasoning 列
- 在 relay 工作階段中新增 `@` 檔案與 `#` GitHub 參照補全
- 當檔案系統缺少 birthtime 時，會顯示正確的工作階段存活時間
- 防止 GPT 模型產生重複的最終 assistant 訊息
- 終端機標題更新現在可在更多終端機中運作
- 在緊湊 Search 時間線項目上顯示 `(sandboxed)` 標記
- Git commands 現在可在經 sandbox 保護的 linked worktrees 中運作
- 將目前 pull request 連結顯示為狀態列項目
- 顯示 WebSocket Responses requests 的 quota snapshots
- 顯示準確的 Anthropic reasoning token 數量
- 在 sandbox 核准後，允許 `grep` 與 `glob` 重試原本被封鎖的搜尋
- 以工作階段標題與 GitHub Copilot 後綴來格式化終端機標題
- 在 tmux 下略過 synchronized output，以避免滑鼠指標閃爍
- Session limits 現在會套用到目前整段對話，在 `/clear` 後重設，並使用 `sessionLimits` 選項鍵
- 在 agent 選擇中隱藏被排除的內建 agents
- 使用 Anthropic 模型的 BYOK 工作階段，不再因 adaptive-thinking 不匹配而觸發 HTTP 400 錯誤；無論是對不支援 adaptive thinking 的模型注入 adaptive thinking，或對需要 adaptive thinking 的模型送出標準 thinking，都不會再出錯。雙模式模型的 thinking mode 選擇維持不變。
- 允許來自不同 plugins、但名稱相同的 skills 共存
- 讓 integrations 可以讀寫 CLI 使用者設定
- 可在 `/lsp logs` 與 `read_agent` 中查看 LSP server logs
- 在 GitHub repositories 中，若缺少 `gh` CLI，會提示安裝
- 為 prompt rendering 新增 GitHub 附件變體
- Extension 開關現在會保留所選模式
- 取消附加的 shell commands 後，會返回 prompt
- 保持背景 `git status` 檢查不會干擾並行的 git commands
- 載入時可恢復已損毀的工作階段歷史記錄
- 在 `/after` 與 `/every` 排程 prompts 中保留換行
- 啟動多行 `/worktree` 任務時，會保持內容完整
- 讓 `/cd` 路徑補全維持與 Enter、Escape、Tab 一致的行為
- 保持 session-store 搜尋與 context 查詢的回應速度
- 在 macOS 上從 CLI 顯示桌面通知
- 當 Windows 環境變數不可用時，仍可貼上 WSL 圖片
- 移除任務後，保持選取停留在相鄰任務上
- `read_agent since_turn: 0` 現在會正確回傳所有 turns，包括 turn 0
- 在啟動期間過濾 MCP servers 輸出的非 JSON stdout 行
- 在背景執行緒中平行進行 tokenizer 預熱，以改善啟動效能
- 在時間線中於使用者 prompts 旁顯示送出時間
- 改善 `/share`，以管理已同步工作階段的可見性
- 在 `AGENTS.md`、`CLAUDE.md` 與 Copilot instruction 檔中展開 `@` 風格 imports
- 讓 `/pr auto` 能持續在 CI、review 與 merge queue 流程中運作
- 點擊展開緊湊時間線項目時，該項目會固定位置並向下展開內容
- 可在 `/settings` 中設定 subagent 的並行度與深度限制（適用於按用量計費使用者）
- 新增 `/chronicle skills review`，可檢閱建議的草稿 skill 變更，並可逐項接受、拒絕或延後
- 為 attention prompts 與閒置工作階段新增桌面通知
- 讓 `/share` 使用 Mission Control 連結來分享工作階段
- 建立快照時，會重試暫時性的 HEAD 查詢失敗，而不是直接當機
- 讓 `/chronicle reindex` 保持回應，並在時間線中顯示進度
- 切換分頁時，會返回最後一次開啟的 GitHub issue、pull request 或 gist 檢視
- 安裝 MCP registry 項目時，會解析 package argument placeholders
- 避免佇列訊息卡在背景工作之後
- 發生暫時性的 connection-pool 錯誤後，會重試擷取 managed settings
- 當受 sandbox 保護的 MCP server 在請求中途結束時，不再顯示 broken-pipe 錯誤
- 當 OAuth token 過期或需要更大 scope 時，能正確恢復由 MCP host 委派的連線
- CLI git 檢查現在會略過可選鎖定，讓狀態與 branch 查詢在繁忙的 repositories 中仍可運作
- 在緊湊時間線列中，將多行子項目折疊為單一行內列
- Inline hook settings 現在可正確處理巢狀的 Claude 風格 hook 群組
- 在 secret filtering 期間保持 CLI 可回應
- Search 輸入現在可比對前後帶有空白的查詢
- 取消某個 turn 後，保持閒置 agents 仍可使用
- 顯示 sandbox 繞過警告，並為已繞過的命令加上標示
- `/pr auto` 現在會啟動自我節奏迴圈，每次執行修正一個項目，並配合 CI 節奏推進 PR 至綠燈；`/pr automerge` 會持續執行直到 PR 合併。可從 `/loop` 或 `/every` 管理或停止。
- 在遠端託管工作階段（cloud 與 relay）中啟用 `/rename`
- 在 CLI 的 MCP 清單檢視中新增切換開關，可啟用或停用 MCP servers
- 在 CLI 設定中新增實驗性的 response limits 控制
- 讓 managed settings 可以設定 OpenTelemetry 匯出
- 使用 OAuth 驗證的遠端 servers 上的 MCP tools，現在可在工作階段中途 token 過期後自動恢復，行為與既有的 OIDC 重試一致。若 tool call 遇到 401，會觸發非互動式重新連線；若 server 需要互動式重新驗證，則會在下一個 turn 開始時重試。
- 新增持久化的 `dynamicRetrieval` 設定（以及 `--dynamic-retrieval skills=<on|off>` 旗標），可啟用或停用基於 embeddings 的 skill 擷取
- 讓 custom agents 可以在其定義中設定 reasoning effort
- 可將任務傳給 `/worktree`（例如 `'fix the login redirect'`），用該任務為 branch 命名，並將這句話作為新 worktree 中的第一個 prompt 執行
- 新增 MCP host token-injection OAuth 流程的執行時遙測，會記錄何時向 host 廣播 OAuth，以及 host 如何回應（token 或取消）與回應延遲
- 在 Pull requests 分頁中顯示各 pull request 的 merge 狀態，並可按 `r` 依需求重新整理快取狀態
- 修正一個輕微卡住問題：若啟動提示（folder trust、screen reader 或 Copilot free signup）在首頁非 Main 分頁聚焦時開啟，CLI 會停止回應輸入
- 引導代理將跨儲存庫的 issue/PR 參照格式化為 `owner/repo#number`（保留裸露的 `#number` 僅用於目前儲存庫），避免誤連到目前儲存庫
- 保持 `/restart` 在關閉清理過久時仍可運作
- 當 `cmd.exe` 不在 `PATH` 中時，仍可在 WSL 中將文字複製到剪貼簿
- `COPILOT_HOME` 與 `--config-dir` 不再從 `~/.agents/skills` 載入 skills
- 在 `/extensions` 中切換 extension 模式時，保留各 extension 被停用的選擇
- 從捲動檢視複製換行文字時，會保持正確間距
- 當語音引擎在啟動時無法啟動，voice mode 會自動關閉
- 在驗證完成前的啟動期間，按 `Ctrl+D` 現在可乾淨結束
- 防止帶框的使用者訊息在右側邊界裁掉尾端字元
- 行內圖片在結束後不再寫入 shell
- 顯示 slash command 子命令的描述
- 在驗證變更後自動重新整理 MCP server headers
- LSP commands 與 tools 現在能更可靠地解析專案設定與 server 路徑
- 新增 `--allow-all-mcp-server-instructions`，可選擇將所有 MCP servers 的 instructions 納入 system prompts
- 在 `--yolo` 工作階段中，自動接受選擇加入的 MCP 同意提示，同時仍顯示系統權限提示
- 在全螢幕檢視中使用完整終端機高度
- 為 shell 與 search 時間線項目使用更清楚的圖示
- 讓終端機文字顏色與 GitHub 主題畫布一致
- 在工作中的頁尾文字中顯示目前啟用的 agent mode
- `/worktree` 現在會保留原樣且有效的 branch 名稱，例如 `feature/JIRA-123`，而不會再將其壓平成像 `feature-jira-123` 這樣的 slug
- 在沒有參數時，`/worktree` 會根據你尚未提交的變更與最近對話，使用目前啟用的模型來命名 branch，而不是固定使用較小模型
- 將調色盤設定整併到 `/settings theme`
- 更可靠地儲存 CLI 設定與工作階段狀態

## 1.0.65 - 2026-06-24

- `/cd` 現在會保存工作目錄，因此恢復工作階段時會回到該目錄，並探索新目錄中的 custom agents
- 帶有斜線開頭字串參數的命令（例如 `--body "/azp run"`）不再觸發多餘的檔案系統權限提示
- 全螢幕時間線在較舊內容被裁切時，現在會保持錨定位置
- 重新啟動 CLI 後，會自動恢復已開啟的 canvases
- 新增可選擇啟用的狀態列項目，用來顯示目前 branch 的 CI 檢查狀態（成功／執行中／失敗）
- 新增 `copilot skill` 子命令（以及 `/skills` 的別名 `/skill`），可從檔案、URL 或目錄列出、新增與移除 skills
- 使用非 GitHub 主題啟動時，不再閃現 GitHub 背景
- 在 Windows 上，代理執行 hook commands 或解析命令路徑時，不再短暫閃現主控台視窗
- 將 userPromptSubmitted hook 的 additionalContext 納入提供給模型的 prompt
- 新增 stdio MCP servers 時，會保留 Windows 路徑原貌
- MCP 關閉時，不再等待進行中的 server 連線完成
- 重新啟動 CLI 時，不再受到關閉逾時影響
- 移除時間線中 shell commands 的語法高亮
- 使用 BYOK providers 時，會保留 custom-agent subagent 的模型選擇
- 會使用工作階段的主要模型來解析 `/every` 排程
- 在 tmux 中更可靠地渲染行內圖片
- `ask_user` 的自由輸入選項現在會自動換行，並保持游標對齊
- 在 `/settings` 中儲存自訂 status line commands
- 將串流位元組數與取消提示分開顯示
- 當沒有啟用 self-paced schedule 時，若發生喚醒誤觸，會顯示友善訊息
- 靜默 MCP OAuth 重新整理會重用已授權的 scope，因此重新連線後仍會保持登入狀態
- 在一般模式下，上下鍵歷史記錄與 Ctrl+R 反向搜尋現在也會包含先前的 shell commands，因此你不必先輸入 `!` 進入 shell mode，就能回想並重新執行 shell command

## 1.0.64 - 2026-06-23

- 路徑存取提示現在會顯示解析後的符號連結目標，讓你能清楚看到實際授予的是哪些存取權限
- 啟動時會顯示按用量計費的額外使用預算，在因超出額外支出上限而遭拒的 request 之後會重新整理，並在達到額外使用上限時顯示友善訊息
- 為 BYOK OpenAI-compatible providers 加入 websocket responses 支援
- 恢復工作階段時，會重現原本附加檔案的參照，即使這些檔案之後在磁碟上發生變更，也能避免 prompt cache 重設
- 含有冒號的自由文字搜尋詞（例如 `CLI:`）現在會在 Issues 與 Pull requests 搜尋中回傳正確結果，而不再被 GitHub 誤判為無效限定詞
- 支援為 MCP server 驗證設定靜態 OAuth client 覆寫值，包括 client secrets
- 在 CLI 尚未完成載入時輸入的按鍵現在會被保留
- 新增可讓 shell commands 繞過 sandbox 的選項
- 在分頁式清單中加入滑鼠單擊與雙擊選取
- 在 Markdown 表格中為 PR 與 issue 參照建立連結
- 預設使用 GitHub 主題，並為所有使用者啟用首頁分頁與 prompt frame
- 終端機調整大小後，終端機輸出現在會維持對齊
- 當 rules service 無法連線（離線或暫時性的網路錯誤）時，content exclusion 不再封鎖所有檔案。系統會先允許存取，直到規則可重新擷取並在背景重試，行為與編輯器一致。
- 可在 `/subagents` 中設定 rubber-duck subagent，包括會挑選相反家族模型的互補模型策略
- `/diff` 現在會在非 git 資料夾中顯示 Copilot 變更的工作階段 diff
- 可透過使用者設定配置 HTTP(S) proxy
- 即使工作階段名稱包含空白，也可依名稱恢復工作階段
- 在遠端託管工作階段中隱藏不支援的斜線指令
- 新增可隱藏對話捲軸的設定
- 在 CLI 中加入行內圖片渲染
- 為 skills 加入 argument-hint frontmatter 支援
- OpenTelemetry：成功 compaction 後的 chat spans 現在會攜帶 `gen_ai.conversation.compacted=true`，而摘要會作為 CompactionPart 輸出在 `gen_ai.input.messages` 中
- PowerShell cmdlets（Select-String、Where-Object、ForEach-Object）不再誤觸多餘的目錄存取提示
- 非互動式 prompt 輸出現在會維持在第 1 欄開始
- 當 vision 停用時，會清除佇列中的工具圖片
- 變更模型時，現在會等到新模型實際套用後才完成切換
- 在 shell 安全性提示中，`2>/dev/null` 重新導向現在會被視為唯讀
- 在外部編輯器中開啟 prompts 時，編輯後文字現在會正規化為 LF
- 在完整 allow-all 工作階段中，會略過 computer-use 同意提示
- 遠端匯出在 `/clear` 之後仍會持續執行，而 `/session info` 會保留 task URL
- 在工作階段選擇器中刪除某個工作階段後，游標會停留在相鄰的工作階段上
- 在 musl 主機上解析與自動更新 SEA 套件時，會使用正確的 Linux libc 目標
- 當 `minItems` 未設定時，必要的多選提示現在允許提交空白選擇
- 附加並還原後，首頁的工作階段時間線會保持可見
- `/settings` 搜尋欄位現在支援 readline 編輯鍵與游標移動
- OpenTelemetry GenAI spans 現在會依 GenAI semantic conventions 規格輸出 `gen_ai.usage.cache_read.input_tokens`、`gen_ai.usage.cache_creation.input_tokens` 與 `gen_ai.usage.reasoning.output_tokens`（先前使用了錯誤的底線分隔命名）
- CLI 結束後終端機滑鼠滾輪失效的問題已修正，做法是以相反順序拆除終端機模式（現在會先停用滑鼠追蹤，再離開 alt screen）
- 修正 `/rewind` 檔案還原確認對話框在捲動過的時間線上方開啟時，底部會被裁切的問題；現在會在檔案清單載入後以完整高度顯示
- 在 `--help` 輸出中顯示 `--remote-export` 與 `--no-remote-export`
- 會將 compact timeline 中展開的 shell 項目自動換行，讓長指令與描述維持可見
- 讓 Markdown 表格中的連結可點擊
- 在 `/usage` 中顯示各模型的 token 總數，並加速大型歷史記錄掃描
- OpenTelemetry GenAI chat spans 現在會為已設定的 reasoning effort 輸出 `gen_ai.request.reasoning.level`
- Autopilot mode 現在會在代理呼叫 task_complete 後回到互動模式，因此下一個 prompt 不會留在 autopilot
- 新增 `/branch` 作為 `/fork` 的別名，與 Claude Code 的指令命名一致
- 實驗性：加入 `--worktree [name]`（`-w`）旗標（透過 `/experimental` 啟用），會在 `<repo>.worktrees/` 下建立或重用 git worktree，並在其中啟動工作階段
- 為 `/agent` 名稱加入 Tab 補全
- 在模型設定中加入像 opus、sonnet、haiku、gpt 與 gemini 這類 model family aliases
- 在 `/terminal-setup` 中為 Windows Terminal 加入 Ctrl+Backspace 綁定
- 為遠端 MCP servers 加入 SDK 對 host-provided OAuth tokens 的支援
- 實驗性：在 compact timeline 中，可點擊單一 tool-call 或 reasoning 列來展開或收合該項目（類似單列的 ctrl+o / ctrl+t），並在滑鼠所在列上顯示細微高亮
- 工作階段建立或重新載入 MCP servers 時，會套用 MCP 組織政策
- 修正稍後要求時無法取得已完成背景指令輸出的問題
- 讓使用 task 或 agent alias 的 custom agents 仍可使用 task companion tools
- 使用 tools wildcard `\*` 的 custom agents 現在會遵守 deferredToolLoading opt-in 開關
- 在 WSL 工作階段中遵守 tmux 色彩偵測
- 遵守 custom agent frontmatter 中 MCP servers 設定的 `deferTools`
- 當 completion picker 開啟時，Ctrl+Q 會將 prompt 加入佇列
- 工作階段重新命名後，Sessions 分頁的列標籤會立即更新
- `--continue` 與 `--resume` 現在會選取目前儲存庫中最新的工作階段
- 當由 nix 提供的 bash 位於 PATH 最前面時，shell 工作階段現在可正確啟動
- 在 marketplace.json 中宣告 MCP servers 的 marketplace plugins，現在可正確使用 OAuth 驗證
- Content exclusion 不再因命令名稱或幽靈路徑而封鎖 shell commands
- 單獨的代理替代字元（lone surrogates）不再導致工作階段恢復失敗或 prompts 被截斷
- 在斜線指令補全中展開 Windows 家目錄路徑
- 保持截斷後的工具輸出預覽仍為有效 UTF-8
- CLI 自動更新器現在會在 Alpine 系統上下載正確的 musl Linux 套件
- 複製上一則 assistant 回覆時，現在會包含完整內容，包括多個區塊的回覆
- 在受信任的 server-mode 工作階段中載入 workspace MCP servers
- 堆疊 diff 現在會使用與檔案樹相同的檔案順序
- 讓 `/pr status` 與 web confirmations 連到 PR 所屬的儲存庫
- 回捲到沒有快照的某個 turn 時，會還原之後的檔案變更
- 佇列中的 `!` shell commands 現在會在本機執行，而不是送給代理
- 排程 prompts 管理對話框現在會縮小以貼合其條目內容
- 當檔案搜尋遇到符號連結迴圈時，保持 `@` 檔案選擇器仍有內容可選
- 對未提供 cache-write 價格的模型，也會顯示 cache-write 定價
- 允許 `/update` 重新啟動以 `copilot -r` 啟動的工作階段
- 防止選擇器與對話框在內容載入時位移或被裁切
- Markdown 中現在只會將雙波浪號渲染為刪除線
- 允許 `/allow-all` 在 relay 工作階段中運作
- 在 compact timeline markdown 中恢復可點擊的 PR 與 issue 連結
- repo 範圍的 plugins 不再跨專案洩漏到全域設定
- 重新登入後，`/model` 在恢復的工作階段中仍可正常運作
- PowerShell script blocks 與插值 `$()` 子運算式不再觸發 content-exclusion 拒絕
- 結束訊息現在一律在恢復指令中顯示 session ID，而不是友善名稱
- 會等待遠端 sandbox 啟動完成後，才開啟 cloud 工作階段
- Autopilot mode 現在會自動處理 elicitation、ask_user、sampling 與權限提示（包括使用 `--autopilot` 啟動與 continuation turns 期間），而不再將對話框直接顯示給使用者
- 新建立的工作階段現在會出現在 agents 分頁中其群組的底部
- 即使來源檔之後被變更或刪除，附加的圖片與 PDF 仍會在工作階段恢復後持續保留
- 允許停用 task 與 explore 內建 subagents
- 工作階段恢復在載入大型歷史記錄時仍能保持回應
- Code search 與 worktree listing 速度更快
- CLI 輸出改用純文字標籤，而不是裝飾性 emoji
- 在時間線中為 shell commands 加入語法高亮
- 在重新連線與重新啟動後保留已開啟的 canvas instances
- 將 preToolUse 提示中輸入的拒絕回饋轉送給模型
- 在 statusline picker 中，已啟用項目的核取方塊顯示為綠色，停用項目則顯示為灰色
- 將 shell timeline 列顯示為黃色 `$` 提示與 Shell 標籤
- 在 resume picker 中新增 Folder 欄位，用來顯示各工作階段的工作目錄
- 自動跟隨系統的淺色與深色模式變更
- 在 CLI 橫幅中使用語意化吉祥物主題色
- 讓頁尾對話框能在 unified view 中隨時間線一起捲動
- 點擊 `/diff` 樹狀檢視中的檔名，可跳到該檔第一個變更處
- 在 Markdown 中以符合主題的 chip 樣式渲染行內程式碼
- 在 `mcp` 指令中顯示已安裝 plugin 提供的 MCP servers
- 移除終端機回報的色彩方案支援
- 新增 `/diagnose` 指令，用來分析工作階段記錄
- 新增 `/mcp registry` 安裝功能，可瀏覽與安裝 MCP servers
- 讓 `/security-review` 對所有使用者可用，不再需要 `--experimental`
- 探索已安裝 plugins 所提供的 MCP servers
- 為 MCP tools 加入 CSV 輸出支援
- 新增 `/loop` 作為 `/every` 指令的別名
- 移除舊版 `/terminal-setup` 建立的錯誤 Ctrl+Enter VS Code 快捷鍵綁定
- tools 回傳的圖片在後續 turns 與恢復工作階段後，仍會對模型保持可見
- 在 `/share` 匯出中保留 Markdown 引言區塊
- 啟用 content exclusion 時，會正確過濾過長的串流結果
- 在達到額外使用上限時顯示友善訊息
- 搜尋 tools 現在可正確處理 Windows 風格的 glob patterns
- 防止 kill 自我保護機制誤判帶引號的 pipe 與以 kill 結尾的路徑
- Azure CLI、PowerShell 與 Developer CLI 憑證現在可再次正常用於 Azure 驗證
- 斜線指令選擇器的名稱欄寬由 25 擴大到 35 字元，因此較長的 skill 名稱較不容易被截斷
- `/diff` view 現在會換行長內容，不再截斷
- 改善 `/diff` 中 branch、whitespace 與 tree 導覽的快捷鍵標籤
- 從 CLI 中移除舊版 intent-reporting tool

## 1.0.54 - 2026-05-24

修正與變更

## 1.0.53 - 2026-05-24

- 多行提示現在會完整顯示，不再發生內容被裁切或選取偏移
- `/skills` 選擇器在儲存 skill 偏好設定時，現在會正確遵循 `--config-dir`
- 當環境中設定了 `PS0` 或 `PROMPT_COMMAND` 時，Bash shell sessions 不再卡住

## 1.0.52 - 2026-05-23

- 非互動式子命令 (`plugin list`、`mcp list`、`help`、`version`) 不再消耗 stdin
- 在主對話檢視中新增可用滑鼠拖曳的垂直捲軸
- 切換到 Autopilot mode 時，不再意外觸發工具、路徑或 URL 存取的權限提示
- `copilot --continue` 從工作階段儲存的目錄啟動時，現在會重新整理儲存的 branch 與 git 情境，而不再沿用過期資訊
- Kill command 安全過濾器不再拒絕像 `kill -0 <PID> 2>/dev/null` 這類包含 shell 重新導向的有效指令
- 工作階段現在會在其儲存的工作目錄中恢復；可傳入 `-C <dir>` 覆蓋。值為相對路徑的旗標 (例如 `--attachment`、`--log-dir`) 會以儲存的 cwd 為基準解析。
- Context window tier 選擇 (預設約 200K 與 1M tokens) 現在會端到端強制生效，因此選定 tier 後會實際限制 compaction、truncation 與 token 顯示
- 使用 Responses API 的工作階段結束後，AI Credits 使用量現在會正確顯示
- 在 Cygwin 或 mintty 中搭配 tmux 使用時，渲染不再卡頓
- 斜線指令選擇器在列被選取時，仍會將 `(experimental)` 與 `(staff)` 標籤維持為橘色
- 在 token 使用量摘要中，reasoning tokens 現在會以輸出 token 數的括號附註顯示
- 若工作階段事件中的 URL/URI 欄位含有非 URL 字串，工作階段恢復時不再出現「Session file is corrupted」錯誤
- 因 HTTP/2 上傳停滯而逾時的 requests，現在會自動以 HTTP/1.1 重試

## 1.0.60 - 2026-06-05

- 在斜線指令路徑參數中，按 Tab 補全 `..` 上層路徑時，現在不會切換分頁
- 為 Anthropic 模型加入最高等級的 reasoning effort，並讓所有方案都可使用所有 effort levels
- 在終端機多工器中從睡眠喚醒後，畫面不會再維持空白
- 輸入欄位在反白框內現在可正確渲染背景色
- Plan approval 與 review feedback prompts 中的游標現在會顯示在正確位置
- 當 PR branch 名稱包含斜線時，worktree 目錄現在會使用平坦名稱（例如 `cli/foo` 會變成 `.worktrees/cli-foo`）
- 啟用 kitty keyboard protocol 時，排隊提示現在會正確顯示 `ctrl+enter`，而不是 `ctrl+q`
- 狹窄終端機寬度下，status line 現在會逐行堆疊顯示，而不是把元素截斷到難以辨識
- 在 X11 上進行剪貼簿操作時，不再破壞終端機顯示
- 新增 `builtInAgents.rubberDuckAutoInvoke` 設定，可控制是否自動呼叫 rubber duck agent（預設停用）
- 在 Windows 上，以裸名稱呼叫可執行檔（例如 `git`）時，不會再從工作目錄中探索執行檔。若要啟用此行為，請將工作目錄加入 `PATH`。
- 互動式 shell 指令在產生大量輸出時，不再卡住
- `/context` 圖例中的 MCP tools glyph 現在會以正確大小顯示
- Skill 與斜線指令 picker 的列，現在會將多行描述正確顯示為單行
- IDE picker 現在會隱藏編輯器連線已中斷的項目，因此選取時不再因連線錯誤失敗；若多個項目共用相同的編輯器與資料夾，還會附加 process id，以便區分同一 repo 的 git worktrees
- Model picker 現在可容納於較小的終端機視窗中，且支援在 picker 內使用滑鼠滾輪
- `/usage` 顯示現在會在 cache read tokens 旁邊一併顯示 cache write tokens
- `ctrl+s` 現在會暫存並還原目前的 prompt（與 Claude Code 一致）；斜線指令 picker 仍可透過輸入 `/` 開啟
- `/context` 現在會將 Custom Instructions 與 system prompt 分開顯示，並與 `/mcp` 交叉參照各伺服器的 MCP tool token 成本
- 新增 `billing` help topic，概述 AI credit 使用功能
- 在 `/diff` view 中新增類 Vim 導覽鍵（`g`、`G`、`Ctrl+D`、`Ctrl+U`）
- 在 `/session info` 檢視中顯示已同步 sessions 的 Mission Control 分享狀態
- 新增 `-r` 作為 `--resume` 的簡寫
- LSP server config 現在接受 `bash`、`powershell` 與 `cwd` keys；若未設定 `cwd`，指令啟動的預設工作目錄仍為專案根目錄；`cwd` 展開現在也支援像 `PLUGIN_ROOT` 這類 plugin 變數，而 shell 啟動則維持既有的 hook-matching cwd/env 行為
- Rewind picker 現在會在每個 checkpoint 顯示 working-tree diff 統計（+新增 −移除）
- 現在可直接從 pull requests 畫面為 pull request 建立 git worktree
- 對於超過限制的使用者，剩餘 requests 百分比不再顯示負值
- 啟動時，extension 權限提示現在會遵循 `--yolo` 與預先核准的位置
- 自訂 agent instructions 不再於每個 turn 重複注入，從而降低 context window 使用量
- 當設定了 `allowedHosts` 或 `blockedHosts` 時，Linux sandbox 不再失敗
- 工作階段完成訊號（終端機提示音、autopilot 持續執行）現在會等背景 shell 指令完成後才觸發
- 在 macOS 的 prompt 輸入中，`Cmd+Backspace` 現在可刪除游標前的整行
- `web_fetch` 會封鎖 loopback、private 與 cloud metadata 位址，且不再靜默跟隨 redirects
- 當實驗指派被並行快取時，Trusted folders 與其他 config keys 不再遺失
- 回捲到先前快照時，Rewind 不再刪除被忽略的檔案
- ACP `allow_all` config option 現在可正確套用工具、路徑與 URL 的不受限制權限
- `--available-tools`、`--excluded-tools` 與 `--reasoning-effort` 旗標現在可在 ACP mode 中正確生效
- LSP `workspace/configuration` 回應現在會回傳正確數量的項目，避免像 `ty` 這類嚴格的 servers 發生 panic
- 透過目錄符號連結連入的 extensions，現在可正確被探索與載入
- 在 prompt 輸入 `help` 時，現在會開啟 quick-help 覆蓋層，而不是將它當成聊天訊息送出
- 寬字元（例如 CJK）現在可在終端機 diff view 中正確渲染，不再造成視覺破損
- Folder trust 現在會在 git worktrees 間持久保存，不需重新提示
- 強制移除 marketplace 後，不會再讓其 plugins 在下次啟動時重新安裝
- 若登入已在進行中，MCP OAuth 重新驗證不再因位址已被使用而失敗
- Repository plugin overrides 不再改動全域啟用的 plugin 設定
- MCP allowlist 現在可正確比對 npm scope servers，即使 registry 項目省略了 package identifier 前面的 `@`
- 透過 Azure API Center 註冊的 MCP servers，不再被 allowlist 錯誤封鎖
- 共用序列化 token broker 的本機 MCP servers（例如 M365）現在可穩定啟動，而不再間歇性失敗
- 執行會設定 dynamic-loader 或 git-config 環境變數的命令前，現在會先要求核准（例如 `LD_PRELOAD`、`GIT_EXTERNAL_DIFF`）
- 某個 server 在同一個 turn 中新增或移除 MCP tools 後，現在可立即在該 turn 使用
- 大於 5 MiB 的 BYOK 檔案附件，現在可透過 OpenAI Responses provider 成功送出
- 當在 git repository 之外執行時，不再顯示 `/init` 建議
- 當進行 remote exporting 或 steering 時，會在 `/session info` 表格中顯示 session 連結
- `/env` 指令現在會顯示有效 hooks 的數量與來源資訊
- 在 `/help` 內容中補上缺漏的鍵盤快捷鍵（`?`、`ctrl+q`、`ctrl+r`、`ctrl+z`、`ctrl+y`、`shift+enter`）
- 會將裸露的 `#number` issue 與 PR 參照自動連結到目前的 git repository
- `--cloud` 若未啟用 experimental mode，其錯誤訊息現在會說明如何啟用 `/experimental`
- 在傳送後續訊息給背景 agent 後，`/tasks` 詳細檢視現在會顯示最新的 prompt
- 對 `--allow-all-tools`、`--allow-all-paths` 與 `--allow-all-urls` 旗標，現在會強制套用 bypass permissions policy

## 1.0.63 - 2026-06-15

- 被封鎖的圖片附件現在會說明可採取的作法，例如透過 "Editor preview features" 政策啟用 vision、切換到支援 vision 的模型，或改用其他圖片，而不再顯示令人困惑的錯誤
- `--help` 輸出中的選項現在會依字母順序排序，包括具有兩個長旗標的選項
- Auth 驗證錯誤（例如 VPN 或 IP allowlist 失敗）現在會顯示在登入橫幅中，並提示檢查網路存取
- 在 `/pr` 與分支 PR 標記中顯示以 fork 為基礎的 pull requests
- 當本機與遠端 repository 名稱僅大小寫不同時，現在可恢復遠端工作階段
- 當 read_bash 輸出過大時，會顯示 spill file 路徑
- 在 `/chronicle standup` 中納入最近的本機工作階段
- 恢復 `/responses` WebSocket 連線
- 在 HMAC 與 OAuth 模式下重試暫時性的 401 auth 失敗
- 在 `/diff` 中按 `w` 可隱藏僅有空白差異的變更
- 在 MCP server config 中新增 `deferTools` 選項，讓某個 server 的 tools 即使在啟用 tool search 時也能始終可用
- Agent mode 現在會依工作階段追蹤，因此在建立、清除或切換工作階段時不再沿用
- 按下 Enter 會開啟目前反白的 issue 詳細內容
- Plan review 選單現在可在嚴格的 OpenAI-compatible backends 上運作
- 當原生 runtime addon 載入到損毀的 host process heap 時，可避免 Windows 當機
- 遇到無法讀取的原生文件附件時，現在會回退為 file-path uploads 以繼續處理
- 在搜尋指令歷史時，會讓 reverse search 持續與輸入頁尾對齊
- PostToolUse hook matchers（例如 `Edit|Write`）現在會正確生效，而不再被靜默忽略，因此 formatters 與 linters 只會在其指定的 tools 之後執行
- 提升 OpenAI、Anthropic 與 Azure OpenAI requests 的可靠性
- 實驗性：`/rewind` 不再需要 git，且只會還原 Copilot 變更過的檔案（保留你自己的編輯），並提供僅還原對話或同時還原對話加檔案兩種選擇

## 1.0.62 - 2026-06-13

- Ask 與 elicitation 對話框現在會與時間線一起捲動，而不是接管整個畫面，因此較高的對話框不會再遮住 agent 的輸出；向上捲動可閱讀較早的輸出，再向下回到對話框
- 保留 reasoning summary 各區段之間的空白行
- 在搜尋 chip 中顯示使用者輸入的冒號詞彙
- Plugins 現在可內含 extensions，因此可透過 plugin marketplace 安裝
- 在 diff view 中新增內容搜尋、比對高亮與 `n`/`N` 導覽
- 新增 `/app` 斜線指令，可開啟 GitHub app，若不可用則回退為瀏覽器
- 可透過使用者設定或 `/subagents`（也支援 `/agents`）選擇器來設定 subagent 的 model、reasoning effort 與 context tier
- PowerShell 重新導向路徑不再觸發 content-exclusion 拒絕
- WebSocket transport 現在可在 Tokio runtime 外乾淨地關閉
- Shell tool 錯誤現在會說明 shell ID 是已停止、已完成，還是已被回收
- 語音執行階段下載對話框在安裝失敗後，不會再陷入重複開啟的迴圈
- 改善 MCP server 設定表單，採用以選擇器為主的流程，使用上更容易
- 在頁尾顯示「YOLO」（allow all）指示器，並將 allow-all 狀態加入自訂 `statusLine.command`
- 在 Issues 或 Pull Requests 分頁按下 `/`，現在可使用伺服器端篩選來搜尋 GitHub
- 新增 session-scoped extensions 與 canvases
- 允許 SDK clients 透過 `session.create` 與 `session.resume` 設定 session memory
- 現在可透過 Kerberos/Negotiate（SPNEGO）自動經由企業 forward proxies 完成驗證
- 在 `/diff` view 中新增檔案樹側欄與行內註解編輯器
- 對 BYOK Responses providers 現在會遵循 `max_output_tokens`
- 名稱包含點號與斜線的 MCP server，現在可對應為有效的 Responses API namespaces
- 像 `code-insiders --wait` 這類編輯器指令，現在可在 Windows 上正確啟動
- 現在可從設定根目錄之外的符號連結目錄載入 skills
- 遇到過大的行內圖片時，現在會優雅地恢復，而不是讓整個 turn 失敗
- 若圖片附件因政策停用 vision 或目前模型不支援而被拒絕，現在不會再污染後續整個 session。發生 400 後，該圖片會從對話歷史中移除，因此之後的 prompts 可正常成功。
- 從 `/tasks` 提升為背景執行的 shells，現在會在 turn 結束後持續執行
- 對背景 helper agents 隱藏內部的已停用工具訊息
- 當主機環境提供 `mxc-sdk` 時，sandbox tool 現在可正確載入
- 當工作階段從 repository 根目錄的子目錄啟動時，現在也會探索巢狀 `.github/agents` 與 `.claude/agents` 目錄中的 custom agents
- 核准某個工具權限提示後，不會再因同一次工具呼叫而出現第二次提示
- View tool 提示現在會正確說明 20KB 截斷限制，而不是 50KB
- 防止 workspace MCP servers 陷入反覆重啟的迴圈
- 使用 BYOK providers 時，custom agents 現在會維持其設定的 model
- 遇到暫時性的內容政策錯誤時，現在可自動恢復，而不需要重新啟動工作階段
- Autopilot 在 relay sessions 中現在可乾淨地持續執行，且 `/plan` 會顯示簡短 prompt
- Git 指令在 Windows 上不再閃現主控台視窗
- Claude 格式 plugin 的 `preToolUse` 與 `permissionRequest` hooks，現在可對 `Bash`、`Read` 與 `*` 這類 tool matchers 正確觸發，而 Claude 格式的 hook payloads 也會攜帶 Claude 的工具名稱（例如 `Bash`，而不是 `bash`）
- 當工作階段中途切換啟用主題時，終端機色彩現在會即時更新
- 串流中的 assistant 文字不再偶爾在時間線中重複顯示
- grep 現在會跳過不存在的搜尋路徑，並繼續返回有效結果，而不是直接失敗
- 遠端 MCP OAuth servers 對於每個相符設定現在只會啟動一次，而不是對每個 subagent 都重新啟動
- 巢狀 subagents 現在會遵守並行限制，且不會阻塞終端機輸入
- 當 marketplace ref 是完整限定 tag（例如 `refs/tags/v2.1.0`）時，plugin install 現在可正常運作
- 在展開的 issue 或 pull request 詳細檢視中按 `W`，即可建立 worktree
- `/every` 與 `/after` 現在可排程斜線指令（例如 `/every 1d /chronicle standup`）
- Model picker 現在會開啟到包含目前已選模型的分頁
- 透過輕量級 process spawning 執行的 shell commands，現在不再使用 pseudo-terminal；也因此不再支援透過 `write_bash` 進行互動式輸入
- 改善 GitHub 主題的色彩對比，以符合 WCAG AA 無障礙標準
- 顯示 ACP session config options 的說明文字
- 加快 warm sessions 中 branch 與 HEAD 的偵測速度
- 淺色主題的次要背景色現在可正確渲染

## 1.0.48 - 2026-05-14

- 採用 token-based billing 的使用者，model picker 現在會顯示實際 token 價格，而不是圓點指示器
- 指令檔 frontmatter 中 `applyTo` 若含有未加引號的 glob pattern（例如 `applyTo: *_/*.ts`），現在也能正確套用
- 含有 CJK 字元或 emoji 的輸入文字，現在渲染時不會在行與行之間出現空白斷裂
- `/context` 現在會顯示所有模型的正確 token 上限，而不再一律顯示 128k
- 在僅使用 Azure DevOps 的 workspace 中，以 prompt/headless mode 執行時，現在會自動停用內建的 github-mcp-server，與互動模式行為一致
- 終端機游標現在會正確落在輸入欄位，而不是選取中的分頁等裝飾元素上
- 當作用中的模型變更時，ACP clients 現在會收到更新後的 config options
- `/ask` 對話框不再提示它無法接收的後續回覆
- 注入給模型的 skill 內容，現在不再包含 YAML frontmatter metadata

## 1.0.47 - 2026-05-13

- `/fork` 現在接受可選名稱，且 fork 出來的工作階段會在 sessions 對話框中顯示其來源
- Copilot Max 訂閱者現在會看到符合其訂閱層級的正確可用模型
- `/diff` 檢視現在支援使用 `j`/`k` 鍵進行上下導覽
- `--resume` 現在支援 Copilot cloud agent sessions，即使 agent 尚未將任何變更推送到其 branch

## 1.0.46 - 2026-05-12

- 當 CLI 版本已遭淘汰、可能失去 premium model 存取權時，現在會顯示警告
- 當 `pwsh` 以 .NET global tool shim 安裝時，PowerShell 現在可正確啟動
- Diff view 中的長行現在會依終端機寬度換行，而不再被截斷

## 1.0.61 - 2026-06-09

- `/agents` 選擇器與 Create New Agent 精靈已完成潤飾，邊框、標頭與輸入樣式更加一致
- 修正恢復工作階段時可能讓畫面維持空白的問題
- 新增 `/settings` 互動式對話框，可在單一介面中瀏覽並編輯所有使用者設定
- 在 memory 停用時恢復本機工作階段，不再讓 UI 當掉成空白畫面
- `/after` 與 `/every` 指令現在會出現在 `/experimental` 斜線指令清單中
- 現在會自動從 `.github/mcp.json` workspace 設定檔載入 MCP servers
- `/env` 輸出現在會隱藏內部 hooks，並顯示 hook 來源的完整檔案路徑
- 防止因格式錯誤的 UTF-8、過大的字串緩衝區與終端機中斷連線錯誤而造成 crash
- 新增對 Claude Fable 5 模型的支援
- Gemini 模型現在可正確搭配使用 nullable schema types 的 MCP tools
- 選擇器中的數字鍵選取（例如 `/agent`）現在可正確處理第 10 項之後的項目
- 既有連結中的 GitHub issue 與 PR 參照，不再產生損壞的巢狀自動連結
- Bash tool 現在可正確處理命令輸入中的多位元組 UTF-8 字元（例如 em dash、彎引號等）
- 符號連結目錄現在會出現在 `@` 檔案選擇器建議中
- 遠端伺服器的 MCP OAuth 重新驗證，現在會正確使用已儲存的 OAuth client ID
- 貼上的圖片在權限對話框關閉後，不再外洩到主要提示輸入區
- 在 `/agent` 選擇器中按下 `/`，現在可依名稱篩選 agents
- 現在可透過 `settings.json` 中的 `tabs` 設定，配置首頁分頁列的顯示、順序與隱藏項目
- grep 與 glob tools 現在可正確處理單一路徑參數，避免漏掉搜尋結果
- 標記為暫時性的 hook 進度狀態列，現在會原地收合，而不會在對話時間線中持續累積
- `/fork` 在建立 fork 期間，現在會顯示「Creating fork...」進度通知
- `/mcp search` 現在可正確搭配外部 registries 使用
- 現在可在 `/every` 與 `/after` 中使用自然語言，以 cron expressions、日曆時間或相對時間長度來排程任務
- 淺色主題的次要背景色現在可正確渲染
- 搜尋列的比對計數現在會維持在提示框內
- GitHub 主題現在可適應淺色終端機，並採用更貼近 GitHub Primer 的淺色調色盤
- 新增透過 HTTPS 匯出 OTLP telemetry 時的 mTLS 與 private-CA 支援
- 修正 shell 指令驗證中的誤判，避免因字串常值或嵌入文件（heredoc）內含像 `kill` 這類字詞，而錯誤封鎖無害指令
- 新增全螢幕捲軸
- 在大型 monorepo 中，grep 搜尋現在會使用索引化搜尋引擎，顯著提升速度
- `/sessions` 現在會導向 Sessions 分頁，而不是開啟覆蓋層
- 新增透過標準 OTel protocol 環境變數使用的 http/protobuf OTLP HTTP 匯出
- Prompt mode 現在會將 model 載入錯誤輸出到 stderr，而不再靜默結束
- 新增 `/worktree` 指令（別名 `/move`），可建立新的 git worktree、切換進去，並一併帶上未提交的變更
- 即使因網路錯誤無法取得 settings，plugin install 仍會強制遵循受管理 marketplace policy
- `/help` 現在會將 `$HOME/.copilot/instructions/**/*.instructions.md` 列為其他使用者層級 instructions 位置之一
- 色彩現在可在 WSL 與 tmux 工作階段中正確渲染，不再退回成較差的調色盤
- 除了 Backspace 之外，現在也可在空白提示下按 `Esc` 或 `Ctrl+C` 離開 shell mode
- 新增 `beepOnSchedule` 設定，可停用排程 `/every` 與 `/after` 執行完成時的提示音

## 1.0.58 - 2026-06-02

- Rubber Duck 現在預設為啟用
- Remote JSON RPC 現在預設為啟用
- 實驗性：可使用 `/every` 與 `/after` 安排排程提示
- 實驗性：新的 GitHub TUI 主題
- 實驗性：新的 UI，可更輕鬆存取 issues、pull requests 與 gists

## 1.0.57 - 2026-06-01

- 在 `copilot update` 遇到 GitHub API rate limit 時，現在會顯示可採取行動的錯誤訊息
- Plugin 斜線指令（/plugin install、uninstall、update、marketplace add/remove/browse）現在會在操作進行中立即顯示回饋
- 取消執行中的 shell 指令（在 `!command` 上按 `Ctrl+C`，或中止 agent 指令，包括 sandboxed shell 與提升為背景執行的 shell）時，現在會終止整個 process tree，而不再留下孤兒程序
- Canvas providers 現在可在 open results 中回傳 `file://` URLs，用於本機檔案預覽
- `/cwd` 補全建議中現在會顯示符號連結目錄
- 在僅使用 Azure DevOps 的 repositories 中，內建 GitHub MCP server 現在只會公開 web_search tool，而不會被完全停用
- 配額頁尾現在會以四捨五入後的百分比顯示剩餘 requests
- 從子目錄啟動 CLI 時，/lsp show、/lsp test 與 /lsp reload 現在可正確找到專案的 LSP config
- MCP server timeout 設定在 tools 清單變更後仍會保留
- `/skills add` 與 `/skills remove` 現在可正確處理被引號包住的路徑（例如來自 Windows Explorer 的 "Copy as path"）
- 以未加引號的多字 prompt 執行 `copilot` 時，現在會顯示有幫助的 "quote your prompt" 提示，而不是原始 commander 錯誤
- 預設網路傳輸現在為 HTTP/1.1，可提升某些網路路徑下的可靠性。如需使用 HTTP/2，可設定 `COPILOT_ENABLE_HTTP2=1`
- 從 repository settings 自動安裝的 plugins 不再洩漏到使用者的全域設定
- Grep tool 現在可正確將 tsx 與 jsx 當作檔案類型篩選條件處理
- 伺服器探索 registry 目錄現在會正確遵循 `COPILOT_HOME`
- 現在可用滑鼠點擊 diff 的某一行，以在 diff mode 中選取它
- `Ctrl+C` 與其他修飾按鍵在 tmux 內現在可正確運作
- `@` 提及的檔案搜尋現在會忽略查詢字母大小寫來比對檔案
- `copilot plugin marketplace list` 現在會遵循 `.github/copilot/settings.json` 中 repo 層級的 `extraKnownMarketplaces` 設定
- 頁尾中的排隊 prompts 現在會限制為單行，避免將工作階段訊息擠出畫面
- 使用 `npx --registry` 設定的 MCP servers 不再被 policy 錯誤封鎖
- 內部事件處理發生錯誤後，工作階段不再無限卡住
- 已安裝的 plugins 不再包含 plugin 來源 repository 中的 `.git` 目錄
- 工具呼叫後的新 reasoning 現在會顯示在時間線底部，而不是跑到較早輸出的上方
- 貼上從瀏覽器、編輯器或終端機複製的文字時，提示區不再殘留多餘空白行、破損的 box-drawing 線條或錯位的游標
- preToolUse hook 錯誤現在會拒絕工具呼叫，而不是靜默允許執行
- 若 crash 在 session log 中留下部分資料，工作階段恢復現在仍可正確運作
- 高對比 diff 背景現在會使用更深的顏色，以提升文字可讀性
- 新增 `showTipsOnStartup` 設定，可控制是否顯示啟動提示
- 當 SDK auth-token 驗證失敗時，現在會顯示底層原因（例如 GitHub API rate limit），而不是誤導性的 "Session was not created with authentication info or custom provider" 訊息
- 沒有 unstaged changes 時，`/diff` 現在預設顯示 branch diff

## 1.0.56 - 2026-05-29

- Free 與 Student 使用者現在可在 model picker 中選擇 Auto 以外的模型
- ThemePicker 的並排版面可在 120 欄寬的終端機中正常顯示，不會換行
- Model picker 現在會依 pricing tier 顯示正確的總 context window 大小
- 新增 `builtInAgents.rubberDuck` 設定，可透過 `copilot config` 啟用或停用 rubber duck agent
- 當 Kitty keyboard protocol 無法使用時，extended key reporting 現在可在 tmux 中正確運作
- Config 與 settings 檔案現在會以原子方式寫入，避免多個 CLI 程序並行執行時造成資料遺失
- BYOK provider 設定現在可正確套用到 ACP sessions
- 同時回傳可讀文字 `content` 與 `structuredContent` payload 的 MCP tools，現在會將兩者都提供給 agent，而不再丟棄任一邊。若文字內容是字面上的 JSON 序列化結果（依 MCP spec §5.2.6），則會去重；否則兩者會串接。
- 修正 `/context` 中 small-token 圖例格式與可用空間網格的四捨五入
- Reasoning effort picker 現在會遵循模型能力，不支援的選項不再顯示
- `/env` 輸出中的檔案路徑現在會以正確格式顯示
- Reasoning 文字現在一律顯示在對話時間線中的 assistant 回覆上方
- Assistant 回覆在終端機時間線中的渲染，不再出現單字孤行
- Diff view 現在使用連續捲動版面，搭配固定的檔案與 hunk 標頭、完整終端機寬度，以及依主題調整的顏色
- web_fetch tool 現在在可用時會優先取得 markdown 內容，並透過 HTTP content negotiation，讓文件站點的結果更乾淨
- 貼上包含 tab 字元的文字後，游標現在仍會停留在正確位置
- Code review agent 現在會使用與目前工作階段相同的模型，而不是固定的預設模型
- 當 `gh` CLI 在 `PATH` 中時，GitHub MCP server 現在預設會省略可由 `gh` 取代的重複工具，以降低 token 使用量
- Context window tier 選擇現在會穩定持久地保存到 session events，並在僅 SDK 的 resume 路徑中持續生效，因此由 tier 衍生的限制會重新套用到 request、compaction 與 truncation 邏輯，而不需應用層修補
- Remote session URL 現在會正確使用 repository owner/name，而不是字面上的 `copilot`
- Trusted folder 確認訊息現在會更清楚說明，權限可能會為該工作階段記住

## 1.0.55 - 2026-05-28

- 採用 token-based billing 的 Free 與 Student 方案使用者，現在只能選擇 Auto 模型；model picker 中會顯示原因說明
- 在工作階段使用量摘要中回報 Claude thinking（reasoning）tokens
- 新增對 Claude Opus 4.8 的支援
- 在不受信任的資料夾中啟動時，loading spinner 不再無限卡住
- 在 MCP server configuration form 中按下 `Ctrl+S` 時，現在會儲存最新輸入的值
- 在 `/mcp` 中顯示各 MCP server 的 token 使用量，並在 `/context` 中拆分顯示 MCP tool tokens
- 現在會遞迴探索子目錄中的 custom agents 與 skills
- 新增 `permissions.disableBypassPermissionsMode` 設定，可防止啟用 allow-all/yolo mode
- 針對特定訂閱方案更新 model selection 行為
- 只有在工作階段處於 plan mode 時，才會向模型提供 exit_plan_mode tool
- 原生二進位檔崩潰（例如 SIGSEGV）時，現在會回退到 JavaScript fallback，而不是靜默結束
- 新增 `/autopilot <objective>` 以讓 autopilot 聚焦於特定目標，並提供 `/goal` 作為別名
- 當 pwsh.exe 以 Microsoft Store App Execution Alias 安裝時，現在可正確偵測 PowerShell 7
- 若工作階段包含大小為零的 CAPI billing batches，現在也可正確恢復
- 以 cell 為基礎的 terminal renderer 現在預設對所有使用者啟用
- 當組織政策停用 remote controlled sessions 時，現在會顯示警告
- Extension log files 現在會依 extension 分別擷取，並在 extensions_manage tool 中顯示，以協助診斷失敗原因
- `.github/extensions` 中的專案 extensions，現在可在非 git（folder-backed）workspace 中被探索到
- `/statusline` 與 `/theme` 指令現在可在 agent 執行期間使用
- MCP configuration 現在會在獨立畫面中開啟；當內容超出可視區域時，可捲動瀏覽 server 與 tool 清單
- Hook progress streaming 現在會在時間線中顯示長時間執行 hooks 的即時狀態訊息
- session.create 與 session.resume RPC 上的 pluginDirectories：SDK clients 現在可在每個工作階段掛載 Open Plugins 格式目錄
- 可直接從 session picker 刪除 remote sessions
- 排程管理器提示列文字在新增項目後，不再換行壓到對話框邊框
- `copilot update` 與 `copilot version` 現在會驗證 release API requests，以避免在共用 NAT 環境中觸發 rate limit 錯誤
- 在 unstaged 與 branch diff modes 之間切換時，Diff view 的鍵盤快捷鍵提示現在可正確顯示
- 在不支援 wlr-data-control 的 Wayland compositor（例如 GNOME/Mutter）上，剪貼簿貼上現在可正確運作
- 互動式 shell tool 現在會保留父終端機的色彩設定，讓 diff tools 與其他程式可完整顯示色彩
- 具有可選 object input schemas 的 Canvas tools，現在可正確開啟，不再出現驗證錯誤
- 當從較舊版本 CLI fork 出 extension subprocesses 時，不再因 "Invalid command format" 而失敗
- 若舊版 CLI 留下 legacy snake_case keys，settings migration 現在會保留使用者資料
- 從 marketplace 新增 plugins 時，現在支援 owner/repo#ref 語法
- Feedback dialog 與 `/skills` help 文字現在使用與 Copilot 一致的 log 路徑與術語
- Progress indicators 現在可原生整合 tmux 3.6b pane progress state
- `--plugin-dir` skills 現在會優先於 personal-home（`~/.copilot`、`~/.agents`）中同名的 skills。順序現在是 project > plugin-dir > personal > custom。
- 當組織政策停用 remote controlled sessions 時，現在會顯示有幫助的訊息
- 所有使用者的 session token summary 中，現在都會顯示 reasoning token 計數
- 除非透過設定明確啟用，否則 turn 完成時終端機鈴聲不再響起
- `/resume` picker 不再對於在發送訊息前就關閉的工作階段顯示空白列
- 中止工作階段時，若 Task tool agents 正在執行，UI 不再卡在 Cancelling 狀態
- vote_memory tool calls 現在會依每次回應與每次互動節流，避免失控的連續投票
- 在時間線頂端以上拖曳滑鼠選取時，現在會自動向上捲動
- 在 Windows 上，剪貼簿現在可正確複製 CJK 與補充平面 Unicode 字元
- 為了提高可見性，所有色彩主題中的選取背景對比都已提升
- `/env` 現在會顯示已載入的 extensions 及其狀態與來源
- 當 CLI 以單一可執行檔應用程式（SEA）執行時，extensions 現在可正確啟動

## 1.0.54 - 2026-05-24

修正與變更

## 1.0.53 - 2026-05-24

- 多行提示現在會完整顯示，不再出現內容被裁切或選取偏移
- `/skills` 選擇器在儲存 skill 偏好設定時，現在會正確遵循 `--config-dir`
- 當環境中設定了 `PS0` 或 `PROMPT_COMMAND` 時，Bash shell 工作階段不再卡住

## 1.0.52 - 2026-05-23

- 非互動式子命令（`plugin list`、`mcp list`、`help`、`version`）不再消耗 stdin
- 主對話檢視新增可用滑鼠拖曳的垂直捲軸
- 切換到 Autopilot mode 時，不再意外觸發工具、路徑或 URL 存取的權限提示
- 在工作階段的已儲存目錄中執行 `copilot --continue` 時，現在會更新已儲存的 branch 與 git context，而不會保留過期資訊
- kill 指令的安全性篩選不再拒絕含有 shell 重新導向的合法指令，例如 `kill -0 <PID> 2>/dev/null`
- 工作階段現在會在原本儲存的工作目錄中恢復；傳入 `-C <dir>` 可覆寫。值為相對路徑的旗標（例如 `--attachment`、`--log-dir`）會以儲存的 cwd 為基準解析。
- Context window tier 選擇（預設約 200K 與 1M tokens）現在會端到端強制套用，因此選擇 tier 之後，會實際限制 compaction、truncation 與 token 顯示
- 使用 Responses API 的工作階段後，AI Credits 用量現在會正確顯示
- 在 Cygwin 或 mintty 上搭配 tmux 使用時，渲染不再卡頓
- 當 slash command 選擇器中的列被選取時，`(experimental)` 與 `(staff)` 標籤會維持橘色
- 在 token usage 摘要中，reasoning tokens 現在會以輸出 token 數量後方的括號形式顯示
- 若工作階段包含在 URL/URI 欄位中帶有非 URL 字串的事件，現在仍可恢復，不再出現 "Session file is corrupted" 錯誤
- 因 HTTP/2 上傳停滯而逾時的請求，現在會自動改用 HTTP/1.1 重試
- 當程序以高位元 exit code 結束時（例如 .NET 未處理例外），工作階段在 Windows 上不再載入失敗
- 展開時間線項目時，其連接線顏色現在會與周圍元素一致
- 在不支援 truecolor 的終端機上，使用者訊息後方不再出現灰色背景條
- 狀態列指令除了可執行腳本路徑外，現在也支援一般 shell 指令
- 啟動時會自動清除 `~/.copilot/logs/` 中舊的程序記錄檔，避免磁碟無限制成長
- `/statusline` 選擇器經過潤飾，項目描述更精簡、間距更佳
- 選擇器核取方塊現在改用單一字元的 ▣/▢ 字形，讓各選擇器中的列更緊湊且一致
- 自訂 agents 現在支援透過 agent frontmatter 中的 `deferred-tool-loading` 啟用選擇性延後載入工具，讓擁有大量工具清單的 agents 可使用 tool-search discovery
- Exit summary 現在會以正確間距顯示 `AI Credits` 標籤與數值
- `/restart` 與 `/update` 在重新啟動後，現在會保留目前工作階段 ID
- MCP server 設定中的舊版巢狀 `oauth.clientId` 與 `oauth.callbackPort` keys，現在會遷移到受支援的 `oauthClientId` 與 `auth.redirectPort` keys，而不再被靜默捨棄
- MCP OAuth 重新驗證現在會遵循已設定的 `redirectPort`
- PowerShell 除法運算子在 Windows 上不再誤觸 "Allow directory access" 權限提示
- `/compact` 現在接受可選的 focus instructions，用來塑造 compact summary 的重點
- 通用型 subagents 在可用時，現在會使用 GPT-5.4 或 GPT-5.5
- `/usage` 現在會顯示 session 與每週限制的 quota progress bars
- AI credits 錯誤訊息已更新為更清楚的文字，並附上 Manage budget 連結

## 1.0.51 - 2026-05-20

- `--session-id=<id>` 現在可恢復已知工作階段或 tasks，也可用指定 UUID 啟動新工作階段
- `/remote` 指令現在會遵循組織的 remote control 與從雲端檢視政策，停用時會顯示明確錯誤
- agent 執行工作時，現在也可使用 `/remote` 指令
- 終端機頁尾中的可自訂狀態列現在會顯示 model、context window、git branch 等工作階段資訊
- 對於設定了大量 HTTP 型 MCP servers 的使用者，啟動時載入 MCP tools 的速度更快
- 更新設定時，settings 檔案不再累積不相關的 config keys
- 新增 `/security-review` 斜線指令，可檢查程式碼變更中的安全性漏洞
- 新增 `preMcpToolCall` hook，讓 hook providers 可控制送出的 MCP request metadata
- 新增 `/chronicle cost-tips` 子命令，可提供個人化的 token 使用與成本降低建議
- 使用 OAuth 的 MCP servers，若驗證是在另一個工作階段中完成，現在仍可維持連線
- 清單項目內的 GFM tables 與 blockquotes 現在會正確渲染，不再出現浮動的上邊框
- 實驗模式指示器現在會持續顯示在應用程式標頭中，而不再只是一次性的通知
- 載入指示器顏色現在會與目前模式（plan、autopilot、shell）一致
- 使用量計費使用者的工作階段命名現在可正確運作
- 在反白的子命令補全項上按 Enter，現在會插入選取內容，而不是提交部分指令
- 發布 release 時若沒有 changelog 項目，現在會使用預設 release notes
- 透過 `Ctrl+G` 啟動的編輯器不再搶走按鍵輸入，也不再需要按兩次鍵
- `/memory show` 現在會顯示文件連結，方便了解與管理 Copilot Memory
- 新增 `terminalProgress` 設定，可啟用或停用 OSC 9;4 終端機進度指示器
- `postToolUse` hooks 現在可將額外的 `additionalContext` 注入成功的工具結果
- 只有在透過 `--remote` 明確要求 remote mode，或使用者設定已啟用時，才會顯示 remote session 啟動失敗
- 即使模型省略 `description` 參數，shell tool calls 現在仍可成功執行
- 確保 input token 用量包含 cached tokens，並更新 token 格式以讓顯示更清楚
- 當 token 儲存退回到不安全的純文字 config 檔案時，登入提示現在會更明確地提出警告
- GitHub MCP web search tool 現在可立即使用，不再需要先執行 tool search
- Secret scanning 現在也涵蓋 commit messages 與 PR descriptions，並會在發佈前遮蔽 secrets
- 輸入區會隨終端機高度自適應增長，不再限制最多 3 行

## 1.0.49 - 2026-05-18

- `postToolUse` hook 的 additionalContext 現在會以 system message 注入給模型，而不再被靜默捨棄
- 當輸入內容包含寬字元（CJK、emoji）時，滑鼠點擊提示區現在可正確定位游標
- 新增 `/chronicle search` 子命令，可依關鍵字或主題搜尋所有工作階段內容
- `/user switch` 現在會重用已抓取的使用者清單，首次開啟時會顯示 loading spinner
- 使用靜態 OAuth clients 的 MCP servers，現在可正確持久保存註冊資訊以供 token refresh
- 新增對 Alpine Linux（musl libc）的 CLI 執行支援
- 新增 `/exit print` 選項，可在退出前將工作階段內容輸出到終端機
- 新增 `/rubber-duck` 指令，可對 agent 目前的工作提出獨立評論
- 新增 `/session id` 子命令，可顯示目前工作階段 ID 並複製到剪貼簿
- 新增 MCP server 的 `auth.redirectPort` config option，可將 OAuth callback 固定在特定埠號
- 新增 `/memory on|off|show` 斜線指令，可啟用、停用或查看 memory 狀態（持久化）
- 新增 `copilot plugin update --all`，可一次更新所有已安裝的 plugins
- 新增 `/rubber-duck` 指令，可呼叫 rubber duck agent 進行獨立評論（實驗性）
- 輸入提示在空白時現在會收合為單行，並在輸入時自然增長
- 所有編輯型工具類型的檔案 diff，現在都可正確回報給 ACP clients
- 當資料夾已受信任時，`.github/hooks/` 中的 repo hooks 現在會在 prompt mode（`-p`）載入
- 修正時間線項目中的多餘空行
- 在未使用 UTF-8 code page 的 Windows 終端機上，box drawing 與 block 字元現在可正確顯示
- 未設定 `args` 欄位的 MCP server 設定現在可被接受，並視為空的 args 清單
- 文件附件路徑現在會納入 context，讓 agent 可參照貼上的檔案路徑，包括 Windows 的 Copy as path 輸入
- MCP stdio servers 現在會將型別顯示為 `stdio`，而不是 `local`，以保持一致
- 進度條指示器現在可在 tmux 工作階段中正確顯示
- 實驗性斜線指令現在會在 help 對話框與指令選擇器中標註為 "(experimental)"
- 若有提供較小的平台專屬套件，auto-update 現在會下載它，而不是通用套件
- assistant 回覆中的 GitHub issue 與 PR 參照（`owner/repo#number`）現在會自動連結
- Prompt mode（`-p`）在目前資料夾已受信任時，現在會自動載入 workspace MCP sources
- 實驗性：新增 `/mcp search` 指令，可從 registry 搜尋並安裝 MCP servers
- 實驗性：MCP 與外部工具支援透過延後載入進行 tool search
- 新增 "None" reasoning effort 選項，可在 reasoning effort picker 中停用模型推理
- 新增 `COPILOT_PLUGIN_DIR_ONLY` 環境變數，可停用自動 plugin discovery，讓使用 `--plugin-dir` 時的 plugin 集合具可重現性
- 從捲動檢視複製文字時，現在會將軟換行合併，不再插入額外換行或縮排
- 輸入欄位中的游標定位，現在可正確處理寬字元（CJK、emoji）
- Hooks（`preToolUse`、`postToolUse`、`subagentStart`、`subagentStop`）現在會對 sub-agent 的工具呼叫正確觸發
- 透過 `--plugin-dir` 載入的 plugins，現在可在 prompt mode 中正確將其 agents 註冊為可用的 `task(agent_type=...)` subagents
- 當沒有 repository context 時，memory storage 現在會正確限制可用的 scopes
- `--plugin-dir` 與 `--additional-mcp-config` 現在可在 `--server` / `--headless` mode 中運作
- 經內容過濾的模型回覆，現在會顯示說明，而不再出現空白的 assistant 回合
- 當外層終端機是 ghostty、WezTerm 或 kitty 時，PromptFrame UI 現在可在 tmux 中渲染（透過 `tmux list-clients` 偵測）
- MCP OAuth token 查找現在會正確限制在目前工作階段範圍內
- Memory 權限提示現在會說明誰可以看到儲存的 memory：user scope 或特定 `owner/repo` 的 repository scope。時間線項目也會顯示 scope（`(for user)` / `(shared with repository collaborators)`）。
- 在 Windows 上使用舊版 PowerShell 5.x 時，透過避免使用 `&&` 串接指令，降低 PowerShell 語法錯誤

## 1.0.60 - 2026-06-05

- 在斜線指令的路徑參數中，按 Tab 補全 `..` 上層目錄時，現在會進行路徑補全，而不是切換分頁
- 新增 Anthropic 模型可用的最高 reasoning effort level，並讓所有方案都可使用所有 effort levels
- 在 terminal multiplexer 中從睡眠喚醒後，畫面不再維持空白
- 輸入欄位現在會在高亮框線內正確渲染背景色
- 游標現在會在 plan approval 與 review feedback prompts 中顯示於正確位置
- 當 PR branch 名稱包含斜線時，worktree 目錄現在會使用扁平名稱（例如 `cli/foo` → `.worktrees/cli-foo`）
- 啟用 kitty keyboard protocol 時，排隊提示現在會正確顯示 `ctrl+enter`，而不是 `ctrl+q`
- 在狹窄終端機寬度下，status line 現在會逐列堆疊顯示，而不是把元素截斷到難以辨識
- 在 X11 上進行剪貼簿操作時，不再破壞終端機顯示
- 新增 `builtInAgents.rubberDuckAutoInvoke` 設定，用來控制是否自動呼叫 rubber duck agent（預設停用）
- 在 Windows 上，以裸名稱呼叫可執行檔（例如 `git`）時，不再從目前工作目錄搜尋。若要啟用此行為，請將工作目錄加入 `PATH`。
- 互動式 shell 指令在產生大量輸出時不再卡住
- `/context` 圖例中的 MCP tools 字形現在會以正確大小顯示
- skill 與斜線指令選擇器的列現在會將多行描述正確顯示為單行
- IDE picker 現在會隱藏其編輯器連線已中斷的項目，因此選取時不再因連線錯誤而失敗；若多個項目共用相同編輯器與資料夾，則會附加 process id，以便區分同一 repo 的 git worktrees
- model picker 現在可適配較小的終端機視窗，且可在選擇器中使用滑鼠滾輪
- 在 `/usage` 顯示中，現在會將 cache write tokens 與 cache read tokens 一併顯示
- 將 `ctrl+s` 改作暫存與還原目前提示（與 Claude Code 對齊）；斜線指令選擇器仍可透過輸入 `/` 開啟
- `/context` 現在會將 Custom Instructions 與 system prompt 分開顯示，並在每個 server 的 MCP tool token 成本上與 `/mcp` 交互參照
- 新增 `billing` 說明主題，概述 AI credit usage 功能
- 在 `/diff` 檢視中新增 Vim 風格導覽按鍵（`g`、`G`、`Ctrl+D`、`Ctrl+U`）
- 在 `/session info` 檢視中顯示同步工作階段的 Mission Control 分享狀態
- 新增 `-r` 作為 `--resume` 的簡寫
- LSP server 設定現在接受 `bash`、`powershell` 與 `cwd` 鍵；command 啟動時的預設 cwd 仍為專案根目錄，除非設定了 `cwd`；此外，`cwd` 展開現在支援像 `PLUGIN_ROOT` 這類 plugin 變數，而 shell 啟動仍維持 hook-matching 的 cwd/env 行為
- rewind picker 現在會在每個 checkpoint 顯示 working-tree diff 統計（`+added −removed`）
- 可直接從 pull requests 畫面為某個 pull request 建立 git worktree
- 對於超出限制的使用者，剩餘 requests 百分比不再顯示為負值
- extension 權限提示現在會在啟動時遵循 `--yolo` 與預先核准的位置
- 自訂 agent instructions 不再於每回合重複附加，以降低 context window 使用量
- 當設定了 `allowedHosts` 或 `blockedHosts` 時，Linux sandbox 不再失敗
- 工作階段完成訊號（終端機嗶聲、autopilot continuation）現在會等到背景 shell 指令完成後才觸發
- 在 macOS 的提示輸入中，`Cmd+Backspace` 現在會刪除游標前的一整行
- `web_fetch` 現在會封鎖 loopback、private 與 cloud metadata 位址，且不再靜默跟隨重新導向
- 當實驗指派快取同時寫入時，Trusted folders 與其他 config keys 不再遺失
- rewind 在回溯到先前快照時，不再刪除被忽略的檔案
- ACP 的 `allow_all` config option 現在會正確套用於 tools、paths 與 URLs 的無限制權限
- `--available-tools`、`--excluded-tools` 與 `--reasoning-effort` 旗標現在可在 ACP mode 中正確生效
- LSP `workspace/configuration` 回應現在會回傳正確數量的項目，避免像 `ty` 這類嚴格的 servers 發生 panic
- 透過目錄符號連結連結的 extensions 現在可被正確發現並載入
- 在提示中輸入 `help` 現在會開啟快速說明覆蓋層，而不是作為聊天訊息送出
- 寬字元（例如 CJK）現在會在終端機 diff 檢視中正確顯示，不再出現視覺破損
- 資料夾信任現在會跨 git worktrees 持久保留，不需重新提示
- 強制移除 marketplace 時，不再導致其 plugins 在下次啟動時重新安裝
- 當登入流程已在進行中時，MCP OAuth 重新驗證不再因位址已被使用而失敗
- repository plugin overrides 不再改變全域啟用的 plugin 設定
- MCP allowlist 現在可正確比對 npm scope servers，即使其 registry 項目會省略套件識別碼前方的 `@`
- 透過 Azure API Center 註冊的 MCP servers 不再被 allowlist 錯誤封鎖
- 共用序列化 token broker 的本機 MCP servers（例如 M365）現在可穩定啟動，不再偶發失敗
- 在執行會設定 dynamic-loader 或 git-config 環境變數的指令前，現在會先要求核准（例如 `LD_PRELOAD`、`GIT_EXTERNAL_DIFF`）
- 當 server 在單一回合中途新增或移除 MCP tools 時，這些工具現在可立即於同一回合使用
- 大於 5 MiB 的 BYOK 檔案附件現在可透過 OpenAI Responses provider 成功送出
- 在 git repository 之外執行時，不再顯示 `/init` 建議
- 在 remote exporting 或 steering 時，`/session info` 表格現在會顯示 session link
- `/env` 指令現在會顯示啟用中 hooks 的數量與來源資訊
- 在 `/help` 內容中補上遺漏的鍵盤快捷鍵（`?`、`ctrl+q`、`ctrl+r`、`ctrl+z`、`ctrl+y`、`shift+enter`）
- 自動將裸露的 `#number` issue 與 PR 參照連結到目前 git repository
- `--cloud` 未啟用 experimental mode 時的錯誤訊息，現在會說明如何啟用 `/experimental`
- `/tasks` 詳細檢視在對背景 agent 發送 follow-up 後，現在會顯示最新提示
- 對 `--allow-all-tools`、`--allow-all-paths` 與 `--allow-all-urls` 旗標，現在會強制套用 bypass permissions policy

## 1.0.48 - 2026-05-14

- 對採用 token-based billing 的使用者，model picker 現在會顯示實際 token 價格，而不是點狀指示器
- `applyTo` frontmatter 中未加引號的 glob patterns 指令檔案（例如 applyTo: \*_/_.ts）現在可正確套用
- 含有 CJK 字元或 emoji 的輸入文字，現在渲染時不會在行與行之間出現空白間隙
- `/context` 現在會針對所有模型顯示正確的 token 上限，而不再一律顯示 128k
- 在僅使用 Azure DevOps 的工作區中於 prompt/headless mode 執行時，現在會自動停用內建 `github-mcp-server`，與互動模式行為一致
- 終端機游標現在會正確定位在輸入欄位，而不是選取分頁等裝飾元素上
- 當變更目前模型時，ACP clients 現在會收到更新後的 config options
- `/ask` 對話框不再要求它無法接收的後續回覆
- 注入模型的 skill 內容不再包含 YAML frontmatter metadata

## 1.0.47 - 2026-05-13

- `/fork` 現在接受可選名稱，且 fork 出來的工作階段會在 sessions 對話框中顯示其來源
- Copilot Max 訂閱者現在會看到其訂閱 tier 可用的正確模型
- 支援在 `/diff` 檢視中使用 `j/k` 鍵上下導覽
- `--resume` 現在支援 Copilot cloud agent 工作階段，即使 agent 尚未將任何變更推送到其 branch

## 1.0.46 - 2026-05-12

- 當 CLI 版本已被淘汰且 premium model 存取可能喪失時，現在會顯示警告
- 當 `pwsh` 以 .NET global tool shim 安裝時，PowerShell 現在可正確啟動
- `diff` 檢視中的長行現在會依終端機寬度換行，而不是被截斷
- 唯讀的 `gh` CLI 指令（list、view、status、diff 等）現在會自動核准，不再提示使用者確認
- 工作階段不再因 `ERR_HTTP2_INVALID_SESSION` 錯誤而在回合中途崩潰

## 1.0.45 - 2026-05-11

- 新增 `/autopilot` 斜線指令，用來在 interactive 與 autopilot modes 之間切換
- 當 Windows 上無法使用 PowerShell 7+ (`pwsh`) 時，會回退使用 Windows PowerShell (`powershell.exe`)
- OpenTelemetry 輸出現在符合 GenAI semantic conventions：MCP 工具呼叫改用標準 `tool_call` spans，並新增 `gen_ai.client.operation.duration` metric 以追蹤工具執行時間
- 具有 extension 權限提示的工作階段現在可恢復，不再出現 "Session file is corrupted" 錯誤
- 當 agent 透過 `task_complete` 停止時，`agentStop` hook 現在會正確觸發
- 在 OSC 色彩查詢支援有限的終端機上，CLI 啟動更快，最多可縮短約 1.5 秒的啟動時間。
- 新增 `/fork` 指令，可將目前工作階段分岔成新的獨立工作階段

## 1.0.44 - 2026-05-08

- `/add-dir` 中的路徑補全不再閃爍，也不再被 `@` 與 `#` 選擇器攔截
- 斜線指令現在可出現在輸入內容中段，且可在單一訊息中呼叫多個 skills
- `userPromptSubmitted` hooks 現在可直接處理請求，繞過 LLM 並在不發出 model call 的情況下回傳回應
- 多帳號使用者的 `/user list` 與 `/user switch` 更快
- 新增可選 `prerelease` 參數給 `copilot update` 與 `/update`，可取得最新 prerelease build
- 透過 `!` 前綴執行的 shell commands 現在可在各種 shell 設定下正確運作
- Shell aliases 與 rc file 設定現在也會在 `!` 指令中生效
- 配額顯示現在會正確呈現 Free 使用者的剩餘用量，而不是一律顯示已用 100%
- 在 autopilot mode 中授予的工具權限會在 `/clear` 後保留
- 當透過 `/model` picker 切換模型時，effort level 現在會正確套用
- 當權限提示尚在等待時按下 `Ctrl+C`，CLI 不再卡住
- 當沒有結果相符時，project info 仍會顯示在 slash command picker 中
- `settings.json` 中無效的 URL 項目不再導致 CLI 啟動崩潰，且會以警告略過
- 時間線現在會顯示 rubber-duck sub-agents 解析後的模型名稱（例如 `Rubber-duck(claude-opus-4.7)`）

## 1.0.43 - 2026-05-06

- 新增 username 切換項到 `/statusline` picker，可在頁尾顯示目前帳號
- Auto mode 現在使用 server-side model routing，以改善即時模型選擇
- 當多個工作階段同時存在時，resume prompt 現在會顯示正確的工作階段名稱
- 防範專案內巢狀惡意 bare repositories 所造成的 RCE
- MCP server child processes（例如由 `npx` 或 `uvx` 啟動）現在會在工作階段結束時完整終止
- 執行 update 指令時，現在會顯示下載進度

## 1.0.42 - 2026-05-06

- 當 server 名稱包含空白時，MCP server failure warning 現在會建議可直接執行的 `/mcp show` 指令
- MCP server failure warnings 現在包含 stderr 輸出，協助診斷連線錯誤
- 新增 `-C <directory>` 旗標，可在啟動前切換工作目錄，類似 `git -C`
- 結束訊息中的 resume 指令，當工作階段尚未重新命名時，現在會顯示 session ID 而非自動產生的名稱
- Remote session export 現在支援非 GitHub repositories 與沒有 repository 的目錄
- 選擇 "Go back" 後，恢復工作階段不再錯誤顯示 "session in use" 警告
- 取消請求後，Enter 鍵不再永久卡住
- 當工作階段沒有使用者訊息且沒有可恢復的已儲存工作階段時，現在會隱藏 exit summary
- 當套件解壓過程中出現暫時性 `EPERM` 時，Windows 上的 CLI 更新不再因 `ENOENT` 失敗
- 新增給 GPT 工作階段使用、由 Claude 驅動的 rubber-duck agent（可於 `/experimental` 使用）

## 1.0.41 - 2026-05-05

- CLI 現在會先立即渲染 UI，再於背景處理驗證，因此啟動更快
- Shell completions（bash、zsh、fish）現在會在首次執行時自動安裝，並在 `copilot update` 後更新
- 對接受參數的斜線指令執行 Tab 補全時，現在會自動加入尾隨空白
- 當防毒軟體或檔案系統鎖導致暫時性 `EPERM` 錯誤時，Windows 上的套件解壓不再崩潰
- Remote session 連線錯誤現在會顯示你已登入的帳號與對應的修復步驟
- `ask user` prompt 問題現在可渲染 Markdown 格式
- 新增實驗性 MCP Tasks 支援：帶有 `taskSupport: "required"` 的 MCP 工具會以非阻塞背景 agent 執行，並可透過 `list_agents` 與 `read_agent` 追蹤（需啟用 experimental mode，例如 `/experimental on` 或 `--experimental` 旗標）
- Extensions 現在會在 prompt mode (`-p`) 載入。User extensions 預設會載入；project extensions 與 management tools 則需要 `GITHUB_COPILOT_PROMPT_MODE_EXTENSIONS=true`。
- assistant 回覆不再包含多餘的系統通知 XML tags
- 大型輸出提示現在會正確引用已設定的 grep tool 名稱
- 使用 git SSH URL（例如 `git@github.com:owner/repo`）新增 plugin marketplace 現在可正確運作
- Slash command picker 現在會搜尋指令描述，並為匹配字元加上底線
- Memory 工具的確認提示現在會在請求儲存記憶時顯示 scope（repository 或 user）
- SQL todo 時間線項目現在會更準確顯示 `INSERT OR IGNORE/REPLACE` 與 blocked 狀態更新
- Streaming text 與 shimmer animations 在緩慢或高負載主機上仍能保持平順
- 新增 `--attachment` 旗標於 non-interactive (`-p/--prompt`) mode，可將檔案（圖片或原生文件）附加到初始提示
- `@` 提及補全現在支援 `./` 路徑、不再在目錄後加入尾隨空白，且會先顯示 project files 再顯示 workspace roots
- 透過繞過 Node 24.x 中的 V8 crash，改善 Windows 穩定性
- 含有 Unicode line separator characters 的 session files 現在可正確載入
- Reasoning effort picker 的提示文字現在會以正確間距顯示 "Esc to cancel"
- 透過更妥善地從模糊或錯位的 edit blocks 中恢復，提升檔案編輯可靠性

## 1.0.40 - 2026-05-01

- 不受模型名稱長度影響，頁尾中的 PR branch 裝飾現在會正確顯示
- `/clear` 與 `/new` 現在會重設目前啟用的自訂 agent 選擇
- assistant 回覆現在會以更平順的文字串流輸出
- 執行 `copilot plugin update` 後，`copilot plugin list` 現在會顯示正確版本
- 新增對 MCP servers 的 `client_credentials` OAuth grant type 支援，可在無瀏覽器情況下完成完全 headless 的驗證
- Subagents 現在會依其自身模型正確判斷 tool search 支援，而不再繼承父工作階段的設定
- 切換到 `/new` 或 `/resume` 的新工作階段時，不再把待處理訊息帶過去
- 傳送大型檔案附件時，CLI 不再以 100% CPU 卡住
- Resume session picker 不再為同一個 Mission Control-backed 工作階段顯示重複項目
- Session resume selector 現在會以單行顯示摘要，並截斷以符合欄寬
- 在 prompt mode 中按下 `Ctrl+C` 時，會立即將 "Exiting…" 輸出到 stderr，讓關閉進度可見
- `/research` 現在使用 orchestrator/subagent 模型，以產生更完整且更可靠的 deep research 結果
- Autopilot mode 現在預設最多只會送出 5 則 continuation messages（可用 `--max-autopilot-continues` 設定）
- Auto-update 期間現在會自動清理磁碟上的舊 CLI 套件版本
- Remote session statusline 現在會顯示遠端工作目錄與 branch，而不是本機 context
- `/update` 重啟後不再重新提交原本的 `-i` prompt
- 會偵測 Azure DevOps repositories 並自動停用 GitHub MCP server
- Session history、file tracking 與 `/chronicle` 指令現已開放給所有使用者
- Skills 現可在 ACP clients 中作為斜線指令使用，與 CLI 體驗一致
- 在先前 CLI 程序意外退出後，恢復工作階段不再誤報為使用中
- `--config-dir` 現在會正確傳遞到 plugin 子指令；`--config-dir` 已棄用，改以 `COPILOT_HOME` 取代
- 當 `/ask` 回應對話框開啟時，滑鼠選取仍可使用，因此其內容可被高亮與複製
- 透過非同步載入自訂 CA 憑證，提升 CLI 啟動速度
- Remote control 連結現在會在時間線中顯示完整 URL，而不是 'Open in browser'
- ACP clients（例如 Zed）現在可在 agent 執行多步驟任務時顯示其即時計畫
- 在 statusline picker 中新增自訂 `statusLine.command` 可見性的切換選項
- ACP clients 現在可透過 agent config option 列出並切換自訂 agents
- 當多個 servers 共用相同 URL 但使用不同靜態 OAuth client IDs 時，MCP OAuth tokens 現在可正確快取
- 含有點號或其他無效字元的 MCP 工具名稱現在會被正確清理
- `Ctrl+C` 與連按兩次 Esc 現在會一次移除一則待處理訊息，而不是全部清空
- Slash command suggestions 現在會將前綴匹配排在模糊匹配之前
- Prompt mode (`-p`) 現在預設以安全為先，會將 repo hooks 與 workspace MCP 置於需顯式啟用的環境變數之後（`GITHUB_COPILOT_PROMPT_MODE_REPO_HOOKS` 與 `GITHUB_COPILOT_PROMPT_MODE_WORKSPACE_MCP`）

## 1.0.59 - 2026-06-02

- 當 `copilot update` 期間觸發 GitHub API rate limit 時，現在會顯示可採取行動的錯誤訊息
- 新增 `/rubber-duck` 指令，可對程式碼與設計提供挑戰性的回饋
- 外掛斜線指令（`/plugin install`、`uninstall`、`update`、`marketplace add/remove/browse`）現在會在操作進行中立即顯示回饋
- 取消執行中的 shell 指令（對 `!command` 按 `Ctrl+C`，或中止 agent 指令，包括 sandboxed 與升級為背景執行的 shells）現在會終止整個程序樹，不再留下孤兒程序
- Canvas providers 現在可在 open 結果中回傳 `file://` URLs，用於本機檔案預覽
- `/cwd` 補全建議現在會顯示符號連結目錄
- 在僅使用 Azure DevOps 的儲存庫中，內建 GitHub MCP server 現在只會暴露 `web_search` tool，而不會被完全停用
- 配額頁尾現在會以四捨五入的百分比顯示剩餘 requests
- 當從子目錄啟動 CLI 時，`/lsp show`、`/lsp test` 與 `/lsp reload` 現在可正確發現專案的 LSP 設定
- MCP server timeout 設定在 tools 清單變更後仍會保留
- `/skills add` 與 `/skills remove` 現在可正確處理被引號包住的路徑（例如 Windows Explorer 的 "Copy as path"）
- 以未加引號的多字提示執行 `copilot` 時，現在會顯示實用的 "quote your prompt" 提示，而不是原始的 commander 錯誤
- 預設網路傳輸現在改為 HTTP/1.1，在某些網路路徑上可靠性更好。若要啟用 HTTP/2，請設定 `COPILOT_ENABLE_HTTP2=1`。
- 從儲存庫設定自動安裝的外掛不再洩漏到使用者全域 config
- Grep tool 現在可正確將 `tsx` 與 `jsx` 作為檔案類型篩選條件處理
- 新增 `/voice` 指令，可使用本機 speech-to-text models 來口述提示
- `COPILOT_HOME` 現在會正確套用於 server discovery registry 目錄

## 1.0.58 - 2026-06-02

- Rubber Duck 現在預設啟用
- Remote JSON RPC 現在預設啟用
- 實驗性的 `/every` 與 `/after` 排程提示
- 實驗性的全新 GitHub TUI 主題
- 實驗性的全新 UI，可更輕鬆存取 issues、pull requests 與 gists

## 1.0.57 - 2026-06-01

- 當 `copilot update` 期間觸發 GitHub API rate limit 時，現在會顯示可採取行動的錯誤訊息
- 外掛斜線指令（`/plugin install`、`uninstall`、`update`、`marketplace add/remove/browse`）現在會在操作進行中立即顯示回饋
- 取消執行中的 shell 指令（對 `!command` 按 `Ctrl+C`，或中止 agent 指令，包括 sandboxed 與升級為背景執行的 shells）現在會終止整個程序樹，不再留下孤兒程序
- Canvas providers 現在可在 open 結果中回傳 `file://` URLs，用於本機檔案預覽
- `/cwd` 補全建議現在會顯示符號連結目錄
- 在僅使用 Azure DevOps 的儲存庫中，內建 GitHub MCP server 現在只會暴露 `web_search` tool，而不會被完全停用
- 配額頁尾現在會以四捨五入的百分比顯示剩餘 requests
- 當從子目錄啟動 CLI 時，`/lsp show`、`/lsp test` 與 `/lsp reload` 現在可正確發現專案的 LSP 設定
- MCP server timeout 設定在 tools 清單變更後仍會保留
- `/skills add` 與 `/skills remove` 現在可正確處理被引號包住的路徑（例如 Windows Explorer 的 "Copy as path"）
- 以未加引號的多字提示執行 `copilot` 時，現在會顯示實用的 "quote your prompt" 提示，而不是原始的 commander 錯誤
- 預設網路傳輸現在改為 HTTP/1.1，在某些網路路徑上可靠性更好。若要啟用 HTTP/2，請設定 `COPILOT_ENABLE_HTTP2=1`。
- 從儲存庫設定自動安裝的外掛不再洩漏到使用者全域 config
- Grep tool 現在可正確將 `tsx` 與 `jsx` 作為檔案類型篩選條件處理
- `COPILOT_HOME` 現在會正確套用於 server discovery registry 目錄
- 在 diff mode 中可用滑鼠點擊 diff 行來選取
- `Ctrl+C` 與其他修飾鍵現在可在 tmux 中正確運作
- `@` 提及的檔案搜尋現在不區分查詢字母大小寫
- `copilot plugin marketplace list` 現在會遵循 `.github/copilot/settings.json` 中儲存庫層級的 `extraKnownMarketplaces` 設定
- 頁尾中的排隊提示現在限制為單行，避免把工作階段訊息擠出畫面
- 設定為 `npx --registry` 的 MCP servers 不再被政策誤判封鎖
- 內部事件處理出錯後，工作階段不再無限卡住
- 已安裝外掛不再包含外掛來源儲存庫中的 `.git` 目錄
- 工具呼叫之後的新 reasoning 現在會顯示在時間線底部，而不是插在較早輸出的上方
- 貼上從瀏覽器、編輯器或終端機複製的文字時，不再留下多餘空白行、破損的 box-drawing 線條，或讓提示區游標跑到錯誤位置
- `preToolUse` hook 錯誤現在會拒絕工具呼叫，而不是靜默允許執行
- 當工作階段記錄因崩潰留下部分資料時，現在仍可正確恢復工作階段
- 高對比 diff 背景現在採用更深的顏色，以提升文字可讀性
- 新增 `showTipsOnStartup` 設定，用來控制是否顯示啟動提示
- 當 SDK auth-token 驗證失敗時，現在會顯示底層原因（例如 GitHub API rate limit），而不是誤導性的 "Session was not created with authentication info or custom provider" 訊息。
- 當沒有 unstaged changes 時，`/diff` 現在預設為 branch diff

## 1.0.56 - 2026-05-29

- Free 與 Student 使用者現在可在 model picker 中選擇 Auto 以外的模型
- ThemePicker 的並排版面現在可在 120 欄寬的終端機中容納，不會換行
- Model picker 現在會依不同計費 tier 顯示正確的總 context window 大小
- 新增 `builtInAgents.rubberDuck` 設定，可透過 `copilot config` 啟用或停用 rubber duck agent
- 當 Kitty keyboard protocol 無法使用時，extended key reporting 現在可在 tmux 中正確運作
- Config 與 settings 檔案現在會以原子方式寫入，避免多個 CLI 程序同時執行時造成資料遺失
- BYOK provider 設定現在可正確套用到 ACP 工作階段
- 同時回傳人類可讀的 `content` 文字與 `structuredContent` payload 的 MCP 工具，現在會將兩者都提供給 agent，不再捨棄任一方。當文字是 JSON 的字面序列化結果（依 MCP spec §5.2.6）時，系統會去重；否則會將兩者串接
- 修正 `/context` 中 small-token 圖例格式與可用空間格線的四捨五入
- Reasoning effort picker 現在會遵循模型能力，不再顯示模型不支援的選項
- `/env` 輸出中的檔案路徑現在會以正確格式顯示
- 在對話時間線中，reasoning 文字現在一律顯示在 assistant 回覆上方
- assistant 回覆在終端機時間線中的渲染，現在不會出現只剩單字的孤行
- Diff view 現在採用連續捲動版面，具備固定的檔案與 hunk 標頭、完整終端機寬度，以及符合主題的色彩
- `web_fetch` tool 在可用時現在會優先使用 markdown 內容，並透過 HTTP content negotiation 從文件網站取得更乾淨的結果
- 貼上含有 tab 字元的文字後，游標現在會維持在正確位置
- Code review agent 現在會使用與目前工作階段相同的模型，而不是固定的預設模型
- 當 `gh` CLI 位於 PATH 中時，GitHub MCP server 現在預設會省略可由 `gh` 取代的重複工具，以降低 token 使用量
- Context window tier 選擇現在會穩定地持久化到 session events 中，且在僅透過 SDK 的 resume 流程下也能保留，因此由 tier 衍生的限制會重新套用到 request、compaction 與 truncation 邏輯，不需要 app 層級修補
- Remote session URL 現在會正確使用儲存庫的 owner/name，而不是字面值 'copilot'
- Trusted folder 確認訊息現在會說明權限可能會在該工作階段中被記住

## 1.0.55 - 2026-05-28

- 採用 token-based billing 的 Free 與 Student 方案使用者，現在僅能選擇 Auto 模型，model picker 也會顯示說明
- 在工作階段使用量摘要中回報 Claude thinking（reasoning）tokens
- 新增對 Claude Opus 4.8 的支援
- 在不受信任的資料夾中啟動時，loading spinner 不再無限卡住
- 在 MCP server 設定表單中按下 Ctrl+S 時，會儲存最新輸入的值
- 在 `/mcp` 中顯示各 MCP server 的 token 使用量，並在 `/context` 中拆分顯示 MCP tool tokens
- 自訂 agents 與 skills 現在會遞迴搜尋子目錄
- 新增 `permissions.disableBypassPermissionsMode` 設定，可防止啟用 allow-all/yolo mode
- 更新部分訂閱方案的模型選擇行為
- `exit_plan_mode` tool 現在只會在工作階段處於 plan mode 時提供給模型
- Native binary 當機（例如 `SIGSEGV`）時，現在會改由 JavaScript fallback 接手，而不是靜默退出
- 新增 `/autopilot <objective>`，讓 autopilot 維持聚焦，並以 `/goal` 作為別名
- 當 `pwsh.exe` 透過 Microsoft Store App Execution Alias 安裝時，現在可正確偵測 PowerShell 7
- 含有零大小 CAPI billing batches 的工作階段現在可正確恢復
- Cell-based terminal renderer 現在預設對所有使用者啟用
- 當 remote controlled sessions 被組織政策停用時，現在會顯示警告
- Extension log files 現在會依 extension 分別擷取，並在 `extensions_manage` tool 中提供，以協助診斷失敗原因
- `.github/extensions` 中的專案 extensions 現在可在非 git（folder-backed）工作區中被發現
- 當 agent 正在執行時，現在也可執行 `/statusline` 與 `/theme` 指令
- MCP 設定現在會在獨立畫面中開啟，當內容超出可視區域時，可捲動檢視 server 與 tool 清單
- Hook 進度串流現在會在時間線中顯示長時間執行 hooks 的即時狀態訊息
- 在 `session.create` 與 `session.resume` RPC 中新增 `pluginDirectories`：SDK client 現在可為每個工作階段掛載 Open Plugins 格式目錄
- 現在可直接從工作階段選擇器刪除 remote sessions
- 當新增項目時，schedule manager hint bar 文字不再換行超出對話框邊界
- `copilot update` 與 `copilot version` 現在會對 release API 請求進行驗證，以避免共享 NAT 環境中的 rate limit 錯誤
- 在 unstaged 與 branch diff 模式間切換時，Diff view 的鍵盤快捷提示現在會正確顯示
- 在不支援 `wlr-data-control` 的 Wayland compositor（例如 GNOME/Mutter）上，剪貼簿貼上現在可正確運作
- Interactive shell tool 現在會保留父終端機的色彩設定，讓 diff 工具與其他程式可完整顯示色彩
- 具有可選 object input schemas 的 canvas tools，現在可正確開啟，不再出現驗證錯誤
- 當 extension 子程序是由較舊的 CLI 版本 fork 出來時，不再因 "Invalid command format" 而失敗
- 當較舊的 CLI 版本留下 legacy snake_case keys 時，settings migration 現在會保留使用者資料
- 從 marketplace 新增 plugins 時，現在支援 `owner/repo#ref` 語法
- Feedback 對話框與 `/skills` 說明文字，現在使用與 Copilot 一致的 log 路徑與術語
- 進度指示器現在可原生整合 tmux 3.6b pane progress state
- `--plugin-dir` 載入的 skills，現在會優先於個人家目錄（`~/.copilot`、`~/.agents`）中同名的 skills。順序現為 project > plugin-dir > personal > custom。
- 當 remote controlled sessions 被組織政策停用時，現在會顯示實用的提示訊息
- 現在所有使用者的工作階段 token 摘要都會顯示 reasoning token 數量
- 除非在 config 中明確啟用，否則工作回合完成時終端機鈴聲不再響起
- `/resume` picker 不再為尚未送出訊息就關閉的工作階段顯示空白列
- 當 Task tool agents 正在執行時，中止工作階段不再讓 UI 卡在 Cancelling 狀態
- `vote_memory` tool 呼叫現在會依每次回覆與每次互動進行節流，避免失控的投票暴增
- 當滑鼠選取拖曳超過時間線頂部時，現在會自動向上捲動
- 在 Windows 上，剪貼簿現在可正確複製 CJK 與增補平面 Unicode 字元
- 提升所有色彩主題中選取背景的對比，以增加可見度
- `/env` 現在會顯示已載入的 extensions，以及其狀態與來源
- 當 CLI 以 single-executable application（SEA）執行時，extensions 現在可正確啟動

## 1.0.54 - 2026-05-24

修正與變更

## 1.0.53 - 2026-05-24

- 多行提示現在會完整顯示，不再出現內容被裁切或選取位置偏移的問題
- `/skills` 選擇器在儲存 skill 偏好設定時，現在會正確遵循 `--config-dir`
- 當環境中設定了 `PS0` 或 `PROMPT_COMMAND` 時，Bash shell 工作階段不再卡住

## 1.0.52 - 2026-05-23

- 非互動式子指令（`plugin list`、`mcp list`、`help`、`version`）現在不再消耗 stdin
- 主對話檢視現在新增可用滑鼠拖曳的垂直捲軸
- 切換到 Autopilot mode 時，不再意外觸發工具、路徑或 URL 存取的權限提示
- 在工作階段儲存的目錄中執行 `copilot --continue` 時，現在會重新整理儲存的分支與 git context，而不是保留過時資訊
- kill 指令的安全過濾器不再拒絕包含 shell redirection 的合法指令，例如 `kill -0 <PID> 2>/dev/null`
- 工作階段現在會在其儲存的工作目錄中恢復；可傳入 `-C <dir>` 來覆寫。值為相對路徑的旗標（例如 `--attachment`、`--log-dir`）會以儲存的 cwd 為基準解析。
- Context window tier 選擇（預設約 200K 與 1M tokens）現在會端到端強制生效，因此所選 tier 會實際限制 compaction、truncation 與 token 顯示
- 使用 Responses API 的工作階段之後，AI Credits 使用量現在會正確顯示
- 在 Cygwin 或 mintty 上搭配 tmux 使用時，渲染不再卡頓
- Slash command picker 在選取列時，會維持 `(experimental)` 與 `(staff)` 標籤為橘色
- Token 使用摘要中的 reasoning tokens 現在會以括號形式顯示在 output token 數旁
- 含有 URL/URI 欄位中非 URL 字串事件的工作階段，現在可正常恢復，不再出現 "Session file is corrupted" 錯誤
- 因 HTTP/2 上傳停滯而逾時的請求，現在會自動以 HTTP/1.1 重試
- 在 Windows 上，當程序以高位元 exit code 結束時（例如 .NET 未處理例外），工作階段不再無法載入
- 展開後的時間線項目連接線顏色現在會與周圍元素一致
- 在不支援 truecolor 的終端機中，使用者訊息後方不再出現灰色背景條
- 狀態列指令除了可執行腳本路徑外，現在也支援一般 shell 指令
- 啟動時現在會自動清理 `~/.copilot/logs/` 中的舊程序記錄檔，避免磁碟用量無限制成長
- `/statusline` picker 已調整為更乾淨的項目描述與更佳間距
- 各種 picker 的核取方塊現在改用單一字元寬度的 ▣/▢ glyph，讓列項更緊湊且一致
- 自訂 agents 現在支援透過 agent frontmatter 中的 `deferred-tool-loading` 啟用選擇性的延遲工具載入，讓大型工具清單的 agent 可透過 tool-search 被發現
- Exit summary 現在會以正確的間距顯示 `AI Credits` 標籤與其數值
- `/restart` 與 `/update` 在重新啟動後會保留目前的工作階段 ID
- MCP server 設定中舊版巢狀 `oauth.clientId` 與 `oauth.callbackPort` keys，現在會遷移為受支援的 `oauthClientId` 與 `auth.redirectPort` keys，而不是被靜默捨棄
- MCP OAuth 重新驗證現在會遵循已設定的 `redirectPort`
- 在 Windows 上，PowerShell 的除法運算子不再誤觸 "Allow directory access" 權限提示
- `/compact` 現在接受可選的 focus instructions，用來塑造 compaction summary
- 通用用途的 subagents 在可用時現在會使用 GPT-5.4 或 GPT-5.5
- `/usage` 現在會顯示工作階段與每週限制的配額進度列
- AI credits 錯誤訊息已更新為更清楚的措辭，並附上 Manage budget 連結

## 1.0.35 - 2026-04-23

- 斜線指令現在支援參數與子指令的 Tab 補全
- Shell escape 指令（`!`）現在在有設定 `$SHELL` 時會使用它，而不再一律呼叫 `/bin/sh`
- CLI TUI 的遠端工作階段現在可正確顯示權限提示
- 工作階段選擇器現在會顯示分支名稱、閒置/使用中狀態，並改進搜尋與游標支援
- 模型變更通知現在會同時顯示先前與新的模型名稱
- `/update` 與 `/version` 指令現在會遵循你設定的更新頻道
- 工作階段同步提示現在使用更清楚的標籤，並說明 GitHub.com 跨裝置同步
- 新增 `COPILOT_GH_HOST` 環境變數支援，用於設定 GitHub 主機名稱，且優先於 `GH_HOST`
- 在補全彈出視窗（`@` 提及、路徑補全、斜線指令）中，除了 Tab 之外，現在也可按 Ctrl+Y 接受高亮選項
- 新增 `/session delete`、`delete <id>` 與 `delete-all` 子指令，並可在工作階段選擇器中按 `x` 刪除
- 現在支援帶有空白與特殊字元的 MCP server 名稱
- 透過 `-i` 傳入作為初始提示的 skill 斜線指令（例如 `/skill-name`）現在可在啟動時正確識別
- 當 `read_bash` 已回傳結果時，shell 補全通知不再重複顯示
- `--continue` 現在會優先恢復目前工作目錄中的工作階段，而不是最近操作的工作階段
- 狀態列腳本現在包含與模型徽章及 `/context` 輸出一致的 context window 欄位
- 使用者設定現在儲存在 `~/.copilot/settings.json`，與 `config.json` 中的內部狀態分開
- 可用 `--name` 為工作階段命名，並使用 `--resume=<name>` 依名稱恢復
- Configure Copilot agent 現在在 Windows 上也能存取 shell
- 當 Linux 缺少剪貼簿工具（`wl-clipboard` 或 `xclip`）時，會顯示含安裝說明的實用錯誤訊息
- `lsp.json` 中的 LSP server 項目現在支援可設定的 spawn、initialization 與 warmup timeouts
- 狀態列中的 context window 指示器現在預設隱藏
- MCP OAuth 現在移入共用 runtime 流程，並會在移除 MCP server 時清除相關的 OAuth 狀態
- `/usage` 新增 GitHub 風格的 contribution graph，可配合終端機色彩模式調整，並在無色彩終端機中退回為不同 glyph
- 在 agentic loop 中可自我修正的自訂工具呼叫
- 文字輸入中的 emoji 與多碼點字元現在可正確移動游標、刪除與渲染
- Windows 上的工具可用性偵測現在可正確運作
- 工作階段 token 在回合中途過期時，現在會自動處理，不需要你重新送出訊息
- `/cwd` 與 `/add-dir` 路徑選擇器在初次使用 Tab 與方向鍵導覽時，現在會選到正確項目
- 當 IDE 或 extension 中斷連線時，暫時性的 I/O 錯誤不再以紅色錯誤項目顯示在時間線中
- `~/.claude/` 中的自訂 agents 與 skills 不再被錯誤載入為 Copilot 專案設定
- 認證完成後，登入指令現在可正確恢復互動式輸入
- 在時間線中顯示大量文字時，渲染效能有所提升
- 在 `MULTI_TURN_AGENTS` 下，同步 task 呼叫現在會阻塞直到完成，而不會在 60 秒後自動升級為背景執行；同步模式也不再回傳可重用的 `agent_id`，後續互動請改用 `mode: "background"`
- 分頁導覽現在支援 Home/End 鍵，可跳到第一個與最後一個分頁
- Plugins 安裝後立即生效，不需要重新啟動
- 新增 `continueOnAutoMode` config 選項，可在觸發 rate limit 時自動切換到 auto model，而不是暫停
- Auto mode 在切換到不支援目前 reasoning effort 的模型時，不再報錯
- 特定 pattern 的 instruction 檔（`.github/instructions/\*.instructions.md`）不再在每個工作階段都把完整內容納入 system prompt
- extension 關閉錯誤不再於每次工作階段結束時以 error-level log 形成噪音
- 當存在 LSP 設定時，LSP refactoring tools 現在會在第一回合正確註冊
- 新增 HTTP hook 支援，可讓 hooks 將 JSON payload POST 到設定的 URL，而不是執行本機指令
- 在時間線中隱藏 subagent 的思考內容
- 頁尾狀態列現在會顯示自訂 agent 名稱，且可透過 `/statusline` 切換
- 啟動對話框中按下 Escape 不再導致競態條件
- grep 與 glob 工具現在接受多個搜尋路徑

## 1.0.34 - 2026-04-20

- Rate limit 錯誤訊息現在會顯示 "session rate limit"，而不是 "global rate limit"

## 1.0.33 - 2026-04-20

- 以 `--resume` 或 `--continue` 恢復遠端工作階段時，現在會自動沿用 `--remote` 旗標，不需要重新指定
- 新增 `/bug`、`/continue`、`/release-notes`、`/export` 與 `/reset` 指令別名
- 當你輸入未識別或拼錯的斜線指令時，斜線指令選擇器現在會建議相似的指令
- 新增 `/upgrade` 作為 `/update` 指令的別名
- 啟用內容排除政策時，`grep` 在大型儲存庫上不再逾時
- 非互動模式現在會等待所有背景 agents 完成後才結束
- Skill 選擇器現在可正確截斷 CJK/日文描述與長 skill 名稱，不會換行
- 按下 Enter 時，斜線指令選擇器現在會選取高亮的指令
- `ctrl+t` 切換 reasoning 顯示現在會列在 `/help` 與 `?` 覆蓋層中
- auto mode 中的 sub-agents 現在會繼承工作階段模型
- 在使用量達 50% 與 95% 時顯示限制警告，更早提示即將觸及 rate limit
- 在 tasks 對話框中使用 `j/k` 進行 vim 風格導覽，並可按 `x` 終止任務

## 1.0.32 - 2026-04-17

- `--resume` 與 `/resume` 現在允許使用較短的工作階段 ID 前綴（7+ 個十六進位字元），不必輸入完整 ID
- 當工作目錄不可寫入時，`/feedback` 會將 bundle 儲存到 `TEMP`
- 可選擇 `auto` 作為模型，讓 Copilot 自動為每個工作階段挑選最佳可用模型
- 新增 `--print-debug-info` 旗標，可顯示版本、終端機能力與環境變數

## 1.0.31 - 2026-04-16

- Prompt frame 不再導致 Windows 與 Ubuntu 終端機出現渲染問題

## 1.0.30 - 2026-04-16

- 回饋表單連結現在會指向正確的 GitHub 儲存庫
- 當無法使用 rewind（例如不在 git 儲存庫中，或尚未有任何 commits）時，`/undo` 會顯示說明訊息
- 使用 `skills.discover` 時，plugin skills 與 commands 現在可正確被發現
- 新增 `/statusline` 指令（以及 `/footer` 別名），可自訂狀態列中顯示的項目（directory、branch、effort、context window、quota）
- 移除 `--list-env` 旗標；該旗標原本會在 prompt mode 中記錄已載入的 plugins、agents、skills 與 MCP servers
- 修正 bracketed paste 處理回歸後，從剪貼簿貼上圖片再次可正常運作
- 在所有平台上，`Ctrl+V` 與 `Meta+V` 現在都可觸發圖片貼上

## 1.0.29 - 2026-04-16

- Remote MCP server config 現在可省略 `type` 欄位，預設為 `http`
- 閃爍游標現在會維持穩定寬度，不會在閃爍時導致文字位移
- 新增 `--list-env` 旗標，可在 prompt mode 執行時記錄已載入的 plugins、agents、skills 與 MCP servers，協助在 CI pipeline 中驗證環境設定
- 新增對 Claude Opus 4.7 的支援
- Shell commands 與 MCP servers 現在會收到 `COPILOT_AGENT_SESSION_ID` 環境變數
- Agent 現在會從 git remote URL 正確辨識儲存庫擁有者，而不是使用本機使用者名稱
- Windows 上在崩潰退出後，終端機狀態現在可正確還原

## 1.0.51 - 2026-05-20

- `--session-id=<id>` 可恢復已知的工作階段或任務，並可用特定 UUID 啟動新的工作階段
- `/remote` 指令現在會遵守組織的 remote control 與 view from cloud policy，且在停用時顯示明確錯誤
- 現在可在 agent 工作進行中使用 `/remote` 指令
- 終端機頁尾中的可自訂狀態列會顯示模型、context window、git branch 等工作階段資訊
- 對於擁有大量 HTTP 型 MCP server 的使用者，啟動時的 MCP 工具載入速度更快
- 更新設定時，settings 檔案不再累積不相關的 config keys
- 新增 `/security-review` 斜線指令，用於檢查程式碼變更中的安全性弱點
- 為 hook provider 新增 `preMcpToolCall` hook，可控制送出的 MCP 請求 metadata
- 新增 `/chronicle cost-tips` 子指令，提供個人化 token 使用與成本降低建議
- 使用 OAuth 的 MCP server 在驗證於不同工作階段中完成時，仍會保持連線
- 清單項目內的 GFM 表格與 blockquote 現在可正確渲染，不會出現浮動的頂部邊框
- 實驗模式指示器現在會持續顯示在 app header 中，而非只顯示一次通知
- 載入指示器顏色現在會與目前模式（plan、autopilot、shell）一致
- 對採用使用量計費的使用者，工作階段命名現在可正常運作
- 在高亮的子指令補全項目上按 Enter 現在會插入選取內容，而不是送出未完成的指令
- 在發布沒有 changelog 項目的版本時，會使用預設 release notes
- 以 Ctrl+G 啟動的編輯器不再攔截按鍵，也不再需要按兩次鍵
- `/memory show` 會顯示文件連結，方便了解與管理 Copilot Memory
- 新增 `terminalProgress` 設定，可啟用或停用 OSC 9;4 終端機進度指示器
- `postToolUse` hooks 現在可將 `additionalContext` 注入成功的工具結果中
- 只有在透過 `--remote` 明確要求 remote mode，或在使用者設定中啟用時，才會顯示 remote 工作階段啟動失敗
- 即使模型省略 `description` 參數，shell 工具呼叫現在也能成功執行
- 確保輸入 token 使用量包含快取，並更新 token 格式以釐清顯示
- 當 token 儲存退回到不安全的純文字 config 檔時，登入提示現在會更明確地提出警告
- GitHub MCP web search 工具現在可立即使用，不需要先執行 tool search
- Secret scanning 現在也涵蓋 commit message 與 PR description，會在發布前將秘密資訊遮罩
- 輸入區會隨終端機高度自適應增長，而不是限制在 3 行

## 1.0.49 - 2026-05-18

- `postToolUse` hook 的 `additionalContext` 現在會作為模型的 system message 注入，而不再被默默丟棄
- 當輸入包含寬字元（CJK、emoji）時，在 prompt 中用滑鼠點擊現在可正確定位游標
- 新增 `/chronicle search` 子指令，可依關鍵字或主題搜尋所有工作階段內容
- `/user switch` 會重用已取得的使用者清單，並在首次開啟時顯示載入 spinner
- 使用靜態 OAuth client 的 MCP server 現在可正確持久保存註冊資訊，以供 token 重新整理
- 新增在 Alpine Linux（musl libc）上執行 CLI 的支援
- 新增 `/exit print` 選項，可在離開前將工作階段內容輸出到終端機
- 新增 `/rubber-duck` 指令，可對 agent 目前的工作取得獨立批評意見
- 新增 `/session id` 子指令，可顯示目前的工作階段 ID 並將其複製到剪貼簿
- 新增 `auth.redirectPort` config 選項，讓 MCP server 可將 OAuth callback 固定在指定連接埠
- 新增 `/memory on|off|show` 斜線指令，可啟用、停用或檢視記憶狀態（持久化）
- 新增 `copilot plugin update --all`，可一次更新所有已安裝的外掛
- 新增 `/rubber-duck` 指令，可呼叫 rubber duck agent 以取得獨立批評意見（實驗性）
- 輸入提示在空白時會收合為單行，並會隨輸入自然增長
- 對所有編輯工具類型，檔案 diff 現在會正確回報給 ACP client
- 當資料夾已受信任時，`.github/hooks/` 中的 repo hooks 現在會在 prompt mode（`-p`）載入
- 修正 timeline 項目中多出一行的問題
- 在未使用 UTF-8 code page 的 Windows 終端機中，box drawing 與 block 字元現在可正確渲染
- 沒有 `args` 欄位的 MCP server 設定現在會被接受，並視為空的 args 清單
- 文件附件路徑現在會納入 context，讓 agent 可參照貼上的檔案路徑，包括 Windows 的 Copy as path 輸入
- 為保持一致性，MCP stdio server 現在顯示為 'stdio'，而不是 'local'
- 進度列指示器現在可在 tmux 工作階段中正確顯示
- 實驗性斜線指令現在會在 help 對話框與指令選擇器中標註 "(experimental)"
- 自動更新在可用時，現在會下載較小的特定平台套件，而非通用套件
- assistant 回覆中現在會自動連結 GitHub issue 與 PR 參考（`owner/repo#number`）
- 當目前資料夾已受信任時，prompt mode（`-p`）現在會自動載入工作區 MCP sources
- 實驗性：`/mcp search` 指令可從 registry 搜尋並安裝 MCP server
- 實驗性：支援對 MCP 與外部工具進行延遲載入的 tool search
- 在 reasoning effort 選擇器中新增 "None" 選項，可停用模型推理
- 新增 `COPILOT_PLUGIN_DIR_ONLY` 環境變數，可停用自動外掛探索，讓搭配 `--plugin-dir` 時的外掛集合具可重現性
- 從捲動檢視複製文字時，軟換行的行現在會合併，不會帶入額外換行或縮排
- 輸入欄位中的游標定位現在可正確處理寬字元（CJK、emoji）
- Hooks（`preToolUse`、`postToolUse`、`subagentStart`、`subagentStop`）現在會對 sub-agent 工具呼叫正確觸發
- 透過 `--plugin-dir` 載入的外掛，現在會在 prompt mode 中正確將其 agent 註冊為可用的 `task(agent_type=...)` sub-agent
- 當沒有儲存庫 context 時，記憶體儲存現在會正確限制可用 scope
- `--plugin-dir` 與 `--additional-mcp-config` 現在可在 `--server` / `--headless` mode 下運作
- 經內容過濾的模型回應現在會顯示說明，而不是空白的 assistant 回合
- 當外層終端機為 ghostty、WezTerm 或 kitty 時，PromptFrame UI 現在可在 tmux 中渲染（透過 `tmux list-clients` 偵測）。
- MCP OAuth token 查找現在會正確限定在目前工作階段範圍內
- 記憶權限提示現在會指出誰能看見已儲存的記憶：使用者 scope，或儲存庫 scope 對應的特定 `owner/repo`。Timeline 項目也會顯示 scope（`(for user)` / `(shared with repository collaborators)`）。
- 在 Windows 上使用舊版 PowerShell 5.x 時，避免使用 `&&` 串接指令，以減少 PowerShell 語法錯誤

## 1.0.48 - 2026-05-14

- Model picker 現在會為採用 token 計費的使用者顯示實際 token 價格，而不再是圓點指示
- applyTo frontmatter 中未加引號的 glob pattern instruction 檔（例如 `applyTo: *_/*.ts`）現在可正確套用
- 含有 CJK 字元或 emoji 的輸入文字現在渲染時不會在行與行之間出現空白間隙
- `/context` 現在會為所有模型顯示正確的 token 限制，而不再一律顯示 128k
- 在 prompt/headless mode 執行時，若工作區僅使用 Azure DevOps，會自動停用內建的 github-mcp-server，與 interactive mode 的行為一致
- 終端機游標現在會正確停在輸入欄位，而不是選取分頁等裝飾元素上
- 當目前啟用的模型變更時，ACP 用戶端會收到更新後的 config options
- `/ask` 對話框不再提示它無法接收的後續回覆
- 注入到模型中的 skill 內容不再包含 YAML frontmatter metadata

## 1.0.47 - 2026-05-13

- `/fork` 現在接受可選名稱，且分支出的工作階段會在工作階段對話框中顯示其來源
- Copilot Max 訂閱者現在會看到其訂閱層級可用的正確模型
- 在 `/diff` 檢視中支援使用 `j/k` 鍵進行上下導覽
- `--resume` 現在支援 Copilot cloud agent 工作階段，即使 agent 尚未將任何變更推送到其分支也可恢復

## 1.0.46 - 2026-05-12

- 當 CLI 版本已遭棄用且可能失去 premium model 存取權時，會顯示警告
- 當 `pwsh` 是以 .NET global tool shim 安裝時，PowerShell 現在可正確啟動
- diff 檢視中的長行現在會依終端機寬度自動換行，而不是被截斷
- 唯讀的 gh CLI 指令（`list`、`view`、`status`、`diff` 等）現在會自動核准，不再提示使用者確認
- 工作階段不再於回合中途因 `ERR_HTTP2_INVALID_SESSION` 錯誤而崩潰

## 1.0.45 - 2026-05-11

- 新增 `/autopilot` 斜線指令，可在 interactive mode 與 autopilot mode 之間切換
- 在 Windows 上，若無法使用 PowerShell 7+（`pwsh`），會回退為使用 Windows PowerShell（`powershell.exe`）
- OpenTelemetry 輸出現在符合 GenAI semantic conventions：MCP 工具呼叫現在使用標準的 `tool_call` spans，並新增 `gen_ai.client.operation.duration` metric 來追蹤工具執行時間
- 含有 extension 權限提示的工作階段現在可以恢復，不再出現 "Session file is corrupted" 錯誤
- `agentStop` hook 現在會在 agent 透過 `task_complete` 停止時正確觸發
- 在 OSC 色彩查詢支援有限的終端機上，CLI 啟動速度更快，最多可將啟動時間縮短約 1.5 秒
- 新增 `/fork` 指令，可將目前工作階段分支為新的獨立工作階段

## 1.0.44 - 2026-05-08

- `/add-dir` 中的路徑補全不再閃爍，也不會被 `@` 與 `#` 選擇器攔截
- 斜線指令現在可出現在輸入內容中間，且單一訊息中可同時呼叫多個 skills
- `userPromptSubmitted` hooks 現在可直接處理請求，繞過 LLM，並在不發出模型呼叫的情況下直接回傳回應
- 多帳號使用者的 `/user list` 與 `/user switch` 現在更快
- 為 `copilot update` 與 `/update` 新增可選的 `prerelease` 引數，以取得最新的預發行版本
- 透過 `!` 前綴執行的 shell 指令現在可正確搭配所有 shell 設定運作
- shell aliases 與 rc 檔設定現在可在 `!` 指令中生效
- 配額顯示現在會正確顯示 Free 使用者的剩餘用量，而不再一律顯示為已用 100%
- 在 autopilot mode 中授與的工具權限，在執行 `/clear` 後仍會保留
- 透過 `/model` 選擇器切換模型時，effort level 現在會正確套用
- 當權限提示正在等待時按下 Ctrl+C，不再導致 CLI 卡住
- 當沒有任何符合結果時，專案資訊仍會顯示在斜線指令選擇器中
- `settings.json` 中無效的 URL 項目不再導致 CLI 啟動崩潰，而會略過並顯示警告
- 時間線現在會顯示 rubber-duck 子代理實際解析後的模型（例如 `Rubber-duck(claude-opus-4.7)`）

## 1.0.43 - 2026-05-06

- 在 `/statusline` 選擇器中新增使用者名稱切換，可在頁尾顯示目前啟用的帳號
- Auto mode 現在使用伺服器端模型路由，以改善即時模型選擇
- 當有多個工作階段同時啟用時，resume 提示現在會顯示正確的工作階段名稱
- 防範巢狀於專案內的惡意裸儲存庫造成遠端程式碼執行（RCE）
- MCP server 子程序（例如透過 `npx` 或 `uvx` 啟動）現在會在工作階段結束時完整終止
- 執行更新指令時現在會顯示下載進度

## 1.0.42 - 2026-05-06

- 當 MCP server 名稱含有空白字元時，MCP server 失敗警告現在會建議可直接執行的 `/mcp show` 指令
- MCP server 失敗警告現在包含 stderr 輸出，以協助診斷連線錯誤
- 新增 `-C <directory>` 旗標，可在啟動前切換工作目錄，類似 `git -C`
- 當工作階段尚未重新命名時，退出訊息中的 resume 指令現在會顯示工作階段 ID，而不是自動產生的名稱
- 遠端工作階段匯出現在支援非 GitHub 儲存庫與沒有儲存庫的目錄
- 選擇 "Go back" 之後，恢復工作階段不再錯誤顯示 "session in use" 警告
- 取消請求後，Enter 鍵不再永久卡住
- 當工作階段沒有使用者訊息，且也沒有可供 resume 的已儲存工作階段時，會隱藏退出摘要
- Windows 上的 CLI 更新在套件解壓縮期間發生暫時性 EPERM 時，不再因 ENOENT 失敗
- 為 GPT 工作階段新增 rubber-duck agent，由 Claude 提供支援（可於 `/experimental` 使用）

## 1.0.41 - 2026-05-05

- CLI 現在會先立即渲染 UI，同時在背景完成驗證，因此啟動更快
- Shell 補全（bash、zsh、fish）現在會在首次執行時自動安裝，並在 `copilot update` 後更新
- 對接受參數的斜線指令使用 Tab 補全時，現在會自動補上尾隨空白
- 在 Windows 上，當防毒軟體或檔案系統鎖定導致暫時性的 EPERM 錯誤時，套件解壓縮不再崩潰
- 遠端工作階段連線錯誤現在會顯示你目前登入的帳號，以及量身調整的修復步驟
- ask user 提示中的問題現在會渲染 Markdown 格式
- 新增實驗性 MCP Tasks 支援：具有 `taskSupport: "required"` 的 MCP 工具會以不阻塞的背景代理執行，並可透過 `list_agents` 與 `read_agent` 追蹤（僅在啟用 experimental mode 時可用，例如透過 `/experimental on` 或 `--experimental` 旗標）
- Extensions 現在會在 prompt mode (`-p`) 載入。使用者 extensions 預設會載入；專案 extensions 與 management tools 則需要 `GITHUB_COPILOT_PROMPT_MODE_EXTENSIONS=true`
- 助手回應不再包含多餘的 system notification XML 標籤
- 大型輸出指引現在會正確引用已設定的 grep 工具名稱
- 使用 git SSH URL（例如 `git@github.com:owner/repo`）新增 plugin marketplace 現在可正確運作
- 斜線指令選擇器現在會搜尋指令描述，並為符合的字元加上底線
- Memory 工具的確認提示現在在請求儲存記憶權限時，會顯示儲存範圍（repository 或 user）
- 對於 INSERT OR IGNORE/REPLACE 與 blocked 狀態更新，SQL todo 時間線項目現在顯示得更準確
- 在較慢或負載較高的主機上，串流文字與 shimmer 動畫仍可維持流暢
- 在非互動模式（`-p/--prompt`）新增 `--attachment` 旗標，可將檔案（影像或原生文件）附加到初始提示
- `@` 提及補全現在支援 `./` 路徑、不再對目錄補上尾隨空白，並會優先顯示專案檔案而非工作區根目錄
- 透過避開 Node 24.x 中的 V8 崩潰問題來提升 Windows 上的穩定性
- 含有 Unicode line separator 字元的工作階段檔案現在可正確載入
- Reasoning effort 選擇器的提示文字現在會以正確間距顯示 "Esc to cancel"
- 透過更妥善地從模糊或錯位的編輯區塊中恢復，提升檔案編輯的可靠性

## 1.0.40 - 2026-05-01

- PR 分支裝飾現在可在頁尾正確顯示，不受模型名稱長度影響
- `/clear` 與 `/new` 會重設目前啟用的自訂 agent 選擇
- 助手回應串流現在有更平順的文字輸出
- 執行 `copilot plugin update` 之後，`copilot plugin list` 會顯示正確版本
- 為 MCP servers 新增 `client_credentials` OAuth grant type 支援，可在不使用瀏覽器的情況下進行完全無頭的驗證
- 子代理現在會正確依照自己的模型判斷工具搜尋支援，而不再沿用父工作階段的設定
- 透過 `/new` 或 `/resume` 切換工作階段時，不再把待處理訊息帶到新工作階段
- 傳送大型檔案附件時，CLI 不再卡在 100% CPU
- Resume 工作階段選擇器不再對同一個由 Mission Control 支援的工作階段顯示重複項目
- 工作階段恢復選擇器現在會以單行顯示摘要，並依欄寬截斷
- 在 prompt mode 期間按下 Ctrl+C 時，會立即將 "Exiting…" 輸出到 stderr，讓關閉進度可見
- `/research` 現在使用 orchestrator/subagent 模型，以提供更完整且更可靠的深度研究結果
- autopilot mode 現在預設將 continuation messages 限制為 5 則（可用 `--max-autopilot-continues` 設定）
- 自動更新時，會自動清理磁碟上舊的 CLI 套件版本
- 遠端工作階段 statusline 現在顯示遠端工作目錄與分支，而不是本地情境
- `/update` 在重新啟動後不再重新送出原始的 `-i` 提示
- 現在會偵測 Azure DevOps 儲存庫並自動停用 GitHub MCP server
- 工作階段歷史記錄、檔案追蹤與 `/chronicle` 指令現在已對所有使用者開放
- Skills 現在可在 ACP 用戶端中作為斜線指令使用，與 CLI 體驗一致
- 恢復工作階段後，不再在先前 CLI 行程意外結束時誤報該工作階段仍在使用中
- `--config-dir` 現在會正確傳遞到 plugin 子指令；`--config-dir` 已棄用，改以 `COPILOT_HOME` 取代
- 當 `/ask` 回應對話框開啟時，滑鼠選取可正常運作，因此內容可以被反白與複製
- 透過非同步載入自訂 CA 憑證來提升 CLI 啟動速度
- 遠端控制連結現在會在時間線中顯示完整 URL，而不是顯示 'Open in browser'
- ACP 用戶端（例如 Zed）現在會在 agent 處理多步驟任務時顯示其即時計畫
- 在 statusline 選擇器中新增 custom `statusLine.command` 顯示切換
- ACP 用戶端現在可透過 agent config 選項列出並切換自訂 agents
- 當多個 servers 共用相同 URL 但使用不同的靜態 OAuth client ID 時，MCP OAuth tokens 現在可正確快取
- 含有點號或其他無效字元的 MCP 工具名稱現在會被正確清理
- Ctrl+C 與雙擊 Esc 現在會一次移除一則待處理佇列訊息，而不是全部一起移除
- 斜線指令建議現在會將前綴符合排在模糊符合之前
- prompt mode (`-p`) 現在會將 repo hooks 與 workspace MCP 置於需顯式啟用的環境變數之後（`GITHUB_COPILOT_PROMPT_MODE_REPO_HOOKS` 與 `GITHUB_COPILOT_PROMPT_MODE_WORKSPACE_MCP`），以提供預設安全的行為

## 1.0.39 - 2026-04-28

- 允許 ACP 用戶端透過工作階段設定切換 allow-all permission mode
- 為 ACP 工作階段新增 `/compact`、`/context`、`/usage` 與 `/env` 斜線指令
- 按下 ctrl+x 然後 `b`，可將目前正在執行的任務或 shell 指令移到背景
- 子程序 stdio 串流上的暫時性 pipe 錯誤不再導致崩潰或觸發誤判的崩潰回報
- `/remote` 狀態輸出現在會針對每種連線狀態顯示可執行的提示
- 改善 `--resume` 工作階段選擇器，提供更好的分頁配置、狀態顯示與漸進式載入
- 斜線指令參數選擇器現在會在精確的指令邊界立即開啟，不再需要尾隨空白

## 1.0.37 - 2026-04-27

- 位置式權限持久化現在預設啟用，因此相同目錄中的核准可跨工作階段沿用
- 新增 `copilot completion <bash|zsh|fish>` 子指令，可為子指令、旗標與已知選項值產生靜態 shell 補全腳本
- 在工作階段選擇器中按 `s` 可循環切換排序方式：relevance、last used、created 或 name
- ACP 模型設定選項現在包含 description 與 metadata，供使用 configOptions API 的用戶端使用
- 重新選擇相同模型或 effort level 時，不再顯示模型與 effort 變更通知
- 在 Linux 上，寫入剪貼簿不再洩漏 X11 handles
- 在提示框旁，待處理訊息指示器現在可正確顯示
- 切換至 `git branch --show-current` 後，修正 detached HEAD 偵測總是回傳 false 的問題
- 即使 skills 有錯誤或警告，skill 選擇器清單仍可完整顯示
- `/ask` 回應現在會渲染 markdown，包括表格與格式化連結

## 1.0.36 - 2026-04-24

- 子指令選擇器現在會在高亮項目旁顯示選取指示符（❯）
- 當偵測到多個 Copilot 授權時，錯誤訊息更清楚，並提供直接連結
- 修正 `preToolUse.matcher` 被忽略的問題。升級後，帶有 matcher 的 hooks 只會對工具名稱完全符合正規表示式時執行。
- `/keep-alive` 現在無需 experimental mode 即可使用，以防止 Copilot CLI 啟用時系統進入睡眠
- `/remote` 指令現在會顯示目前狀態，並支援 `/remote on` 與 `/remote off` 來切換遠端控制
- 已停用的 skills 不再顯示於斜線指令清單中
- 新增 'changes' statusline 切換，可顯示工作階段的新增/刪除行數
- 位於 `.gitignore` 目錄中的自訂 instruction 檔（例如 `.github/instructions/`）現在可正確載入
- 需要按兩次 Esc 才會取消進行中的工作，以避免誤中斷
- 儲存除錯日誌或回饋 bundle 時，不再覆寫既有封存檔
- Copilot CLI 不再載入來自 `~/.claude/` 的自訂 agents、skills 與 commands
- Claude Opus 4.6 現在預設使用 medium reasoning effort

## 1.0.35 - 2026-04-23

- 斜線指令現在支援參數與子指令的 Tab 補全
- shell escape 指令（`!`）現在在有設定 `$SHELL` 時會使用它，而不再一律呼叫 `/bin/sh`
- 在 CLI TUI 中，權限提示現在可在遠端工作階段中正確顯示
- 工作階段選擇器現在會顯示分支名稱、閒置/使用中狀態，並改進搜尋與游標支援
- 模型變更通知現在會同時顯示先前與新的模型名稱
- `/update` 與 `/version` 指令現在會遵循你設定的更新頻道
- 工作階段同步提示現在使用更清楚的標籤，並說明 GitHub.com 跨裝置同步
- 支援 `COPILOT_GH_HOST` 環境變數作為 GitHub 主機名稱，且優先於 `GH_HOST`
- 在補全彈出視窗（`@` 提及、路徑補全、斜線指令）中，按 Ctrl+Y（除了 Tab 之外）現在也可接受目前高亮選項
- 新增 `/session delete`、`delete <id>` 與 `delete-all` 子指令，並可在工作階段選擇器中按 `x` 刪除
- 現在支援含有空白與特殊字元的 MCP server 名稱
- 作為初始提示透過 `-i` 傳入的 skill 斜線指令（例如 `/skill-name`），現在可在啟動時正確辨識
- 當 `read_bash` 已回傳結果時，shell 補全通知不再重複
- `--continue` 現在會優先恢復來自目前工作目錄的工作階段，而不是最近接觸的工作階段
- Status line script 現在包含與模型徽章及 `/context` 輸出一致的 context window 欄位
- 使用者設定現在儲存在 `~/.copilot/settings.json`，與 `config.json` 中的內部狀態分離
- 可使用 `--name` 為工作階段命名，並透過 `--resume=<name>` 以名稱恢復
- Configure Copilot agent 現在在 Windows 上具有 shell 存取能力
- 當 Linux 上缺少剪貼簿工具（`wl-clipboard` 或 `xclip`）時，會顯示含安裝說明的實用錯誤訊息
- `lsp.json` 中的 LSP server 項目現在支援可設定的 spawn、initialization 與 warmup timeouts
- statusline 中的 context window 指示器現在預設隱藏
- 將 MCP OAuth 移入共用執行階段流程，並在移除 MCP server 時清除相關 OAuth 狀態
- 在 `/usage` 中新增 GitHub 風格的 contribution graph，可依終端機色彩模式調整，並在無色終端機中退回為不同字形
- 代理式迴圈中的自我修正 custom tool calls
- 文字輸入中，游標移動、刪除與渲染現在可正確處理 emoji 與多碼點字元
- 工具可用性偵測現在可在 Windows 上正確運作
- 工作階段 token 在單一回合中到期時，現在會自動處理，無需重新送出訊息
- 在 `/cwd` 與 `/add-dir` 路徑選擇器中，初始的 Tab 與方向鍵導覽現在會選取正確項目
- 當 IDE 或 extension 中斷連線時，暫時性的 I/O 錯誤不再以紅色錯誤條目出現在時間線中
- 位於 `~/.claude/` 的自訂 agents 與 skills 不再被錯誤載入為 Copilot 專案設定
- 登入指令在驗證後會正確恢復互動式輸入
- 顯示大量文字於時間線時，改善渲染效能
- 在 `MULTI_TURN_AGENTS` 下，同步 task 呼叫現在會阻塞直到完成，而不是在 60 秒後自動轉為背景；同步模式也不再回傳可重用的 `agent_id`，若要後續追蹤請使用 `mode: "background"`
- Tab 導覽現在支援 Home/End 鍵，可直接跳到第一個或最後一個分頁
- Plugins 安裝後立即生效，不再需要重新啟動
- 新增 `continueOnAutoMode` 設定選項，可在遇到 rate limit 時自動切換至 auto model，而不是暫停
- 切換到不支援已設定 reasoning effort 的模型時，auto mode 不再失敗並報錯
- 具特定 `applyTo` 模式的 instruction 檔（`.github/instructions/*.instructions.md`）不再於每個工作階段都把完整內容放入 system prompt，藉此減少 context window 使用量
- extension 關閉錯誤不再於每次工作階段退出時顯示為 error-level 日誌雜訊
- 當存在 LSP 設定時，LSP refactoring tools 現在會在第一回合正確註冊
- 新增 HTTP hook 支援，允許 hooks 將 JSON payload POST 到設定的 URL，而不是執行本機指令
- 從時間線隱藏子代理思考內容
- 自訂 agent 名稱現在會顯示於 statusline 頁尾，並可透過 `/statusline` 切換
- 啟動畫面上的對話框按下 Escape 不再導致競態條件
- grep 與 glob 工具現在可接受多個搜尋路徑

## 1.0.34 - 2026-04-20

- Rate limit 錯誤訊息現在會顯示為 "session rate limit"，而不是 "global rate limit"

## 1.0.33 - 2026-04-20

- 透過 `--resume` 或 `--continue` 恢復遠端工作階段時，現在會自動沿用 `--remote` 旗標，無需重新指定
- 新增 `/bug`、`/continue`、`/release-notes`、`/export` 與 `/reset` 作為指令別名
- 當你輸入無法辨識或拼錯的斜線指令時，斜線指令選擇器現在會建議相近指令
- 新增 `/upgrade` 作為 `/update` 指令的別名
- 當啟用內容排除政策時，grep 在大型儲存庫上不再逾時
- 非互動模式現在會等所有背景代理完成後才退出
- skill 選擇器現在可正確截斷 CJK/日文描述與過長的 skill 名稱，而不會換行
- 按下 Enter 時，斜線指令選擇器現在會選取高亮中的指令
- `ctrl+t` 切換推理顯示現在列於 `/help` 與 `?` 覆蓋說明中
- auto mode 下的子代理現在會繼承工作階段模型
- 使用量限制警告現在會在容量達 50% 與 95% 時顯示，讓你能在達到 rate limit 之前更早得知
- 在 tasks 對話框中使用 `j/k` 進行 Vim 風格導覽，並按 `x` 終止任務

## 1.0.32 - 2026-04-17

- 使用 `--resume` 與 `/resume` 時，現在可接受較短的工作階段 ID 前綴（7 個以上十六進位字元），而不必輸入完整 ID
- 當工作目錄不可寫時，`/feedback` 會將 bundle 儲存到 TEMP
- 將 `auto` 選為模型，讓 Copilot 在每個工作階段自動挑選最佳可用模型
- 新增 `--print-debug-info` 旗標，用來顯示版本、終端機能力與環境變數
- 當接近每週使用量上限的 75% 與 90% 時，會顯示警告
- 可將支援的文件檔案附加到提示中，讓 agent 讀取並推理
- 新增 `--connect` 旗標，可依 ID 直接連線到遠端工作階段
- `copilot login --host` 現在可正確使用 GitHub Enterprise Cloud (GHE) 執行個體進行驗證
- agent 情境中的目前日期與時間現在包含本地時區偏移
- 當 agent 正在思考時，終端機進度指示器會保持可見
- 在像 Neovim 這類終端機中，執行 `/clear` 之後，status line 不再顯示零散的 Unicode 字形
- 使用 `/cd` 切換目錄後，rewind 現在可正確運作
- 使用 `/plan` 與 plan mode 時，會保留多行輸入
- 只有在輸入為空時，Backspace 才會正確離開 shell mode
- 滑鼠滾輪現在可在 `/ask` 對話框中正確捲動
- 遭 rate limit 的工作階段現在會暫停排隊中的訊息並自動重試，而不會直接丟棄
- 表格在終端機調整大小時，現在能維持正確欄寬、emoji 支援與穩定邊框
- Rate limit 錯誤訊息現在會依據達到的限制類型顯示具體情境
- 工作階段閒置逾時現在可透過 `--session-idle-timeout` 設定；預設停用
- 即使超出 token 限制，skills 仍可被探索並透過名稱呼叫

## 1.0.31 - 2026-04-16

- 提示框在 Windows 與 Ubuntu 終端機上不再造成渲染問題

## 1.0.30 - 2026-04-16

- 回饋表單現在會連到正確的 GitHub 儲存庫
- 當 rewind 無法使用時（例如不在 git 儲存庫中，或尚未有任何提交），`/undo` 會顯示說明訊息
- 使用 `skills.discover` 時，plugin skills 與 commands 現在可正確被發現
- 新增 `/statusline` 指令（以及 `/footer` 別名），可自訂狀態列中顯示的項目（directory、branch、effort、context window、quota）
- 移除 `--list-env` 旗標；該旗標會在 prompt mode 中記錄已載入的 plugins、agents、skills 與 MCP servers
- 在 bracketed paste 處理回歸之後，從剪貼簿貼上影像現在再次可用
- 在所有平台上，Ctrl+V 與 Meta+V 現在都會觸發影像貼上

## 1.0.29 - 2026-04-16

- 遠端 MCP server 設定現在允許省略 type 欄位，並預設為 http
- 閃爍游標會維持穩定寬度，因此文字不會隨著閃爍而位移
- 新增 `--list-env` 旗標，可在 prompt mode 中記錄已載入的 plugins、agents、skills 與 MCP servers，有助於在 CI pipeline 中驗證環境設定
- 新增對 Claude Opus 4.7 的支援
- shell 指令與 MCP servers 現在會收到 `COPILOT_AGENT_SESSION_ID` 環境變數
- agent 現在會從 git remote URL 正確識別儲存庫擁有者，而不是使用本地使用者名稱
- 在 Windows 上，崩潰退出後終端機狀態現在可正確還原

## 1.0.28 - 2026-04-16

- 在 git submodule 中工作時，權限提示現在會顯示正確的儲存庫路徑
- 當 `read_agent` 已在等待結果時，背景代理完成通知不再重複送出
- MCP 遷移提示現在會連到附有各平台說明的文件，而不是直接內嵌 shell 指令
- 執行 az CLI 指令時，Azure resource IDs 不再誤觸路徑安全警告
- Rewind 選擇器導覽已簡化為方向鍵與 Enter，移除令人困惑的 1-9 快速選取捷徑
- 當設定的編輯器無法啟動時，現在會顯示清楚的錯誤訊息
- 吉祥物啟動時現在會播放簡短的眨眼動畫，而不是持續眨眼
- 可從 `--resume` 選擇器連線到 CLI 遠端控制工作階段
- 支援 `COPILOT_DISABLE_TERMINAL_TITLE` 環境變數，用來停用終端機標題更新

## 1.0.27 - 2026-04-15

- 當 Copilot Pro 試用遭暫停時，會顯示清楚訊息，而不是泛用的政策錯誤
- 狀態列在輸入時會顯示 `@files` 與 `#issues` 提示，而在斜線指令選擇器開啟時顯示 `/help` 提示
- 在 WSL 上，複製到剪貼簿不再將隱形 BOM 字元洩漏到貼上的文字中
- 新增 `/ask` 指令，可快速提問而不影響對話歷史
- 新增 `copilot plugin marketplace update` 指令，可刷新 plugin 目錄

## 1.0.26 - 2026-04-14

- Escape 鍵現在可可靠地關閉 ask_user 與 elicitation 提示，而不會卡住
- `find -exec` 區塊中的引數不再出現多餘的目錄存取提示
- 當情境壓縮在 checkpoint 邊界拆開工具呼叫時，agent 工作階段不再因無法恢復的錯誤而失敗
- 單段、帶斜線前綴的 token（例如 `/help`、`/start`）在 bash 指令中不再被視為檔案路徑
- 使用 Anthropic BYOM 時，檢視影像檔案會正確包含影像資料
- 權限提示通知 hook 現在只會在實際向使用者顯示提示時觸發
- `ctrl+o` 現在會展開所有時間線條目，與 `ctrl+e` 相同
- 遠端分頁現在可正確顯示 Copilot coding agent 任務，並支援 steering，且無需 pull request
- 在 `--remote` 旗標與 `/remote` 指令說明文字中，將 "steering" 重新命名為 "remote control"
- 避免將重複的自訂 instruction 檔（例如內容相同的 `copilot-instructions.md` 與 `CLAUDE.md`）重複送出，以減少每回合浪費的 token
- Plugin hooks 現在會收到 `PLUGIN_ROOT`、`COPILOT_PLUGIN_ROOT` 與 `CLAUDE_PLUGIN_ROOT` 環境變數，其值為 plugin 的安裝目錄
- ACP server 現在只會綁定到 localhost，以避免非預期的網路暴露
- 從 marketplace 安裝名為 `git` 的 plugin 時，不再因 URL 解析錯誤而失敗
- 企業登入現在可接受不含 URL scheme 的主機名稱（例如 `github.example.com`）
- 在 Windows 上，LSP language servers 現在會使用正確的 file URI 路徑完成初始化
- 檔案編輯操作中的相對路徑現在會以工作階段工作目錄為基準解析
- 同步提示中的工作階段範圍選擇器現在更醒目，並可使用左右方向鍵導覽
- 具特定 `applyTo` 模式的 instruction 檔現在會整合成表格，而不是內嵌完整內容，藉此減少 context window 使用量

## 1.0.25 - 2026-04-13

- 可直接在 CLI 中從 registry 安裝 MCP servers，並提供引導式設定
- `/resume` 工作階段查找失敗後，Esc 鍵現在可正確運作
- 將解析後的模型保存到工作階段歷史，並在回合進行中延後模型切換
- ACP 用戶端現在可在啟動或載入工作階段時提供 MCP servers（stdio、HTTP、SSE）
- 選擇啟用中的模型時，現在會正確遵循 `--config-dir` 旗標
- 新增 `/env` 指令，用來顯示已載入的環境細節（instructions、MCP servers、skills、agents、plugins）
- 當自訂輸出路徑未附副檔名時，`/share` 會自動補上正確的副檔名（`.md` 或 `.html`）
- `/add-dir` 現在接受相對路徑（例如 `./src`、`../sibling`），並將其解析為絕對路徑
- 自訂 instruction 檔現在可保留 `&` 與 `<placeholders>` 等特殊字元
- 當清單超出終端機高度時，skill 選擇器清單現在可正確捲動
- MCP client 現在會在與 server 握手時回報正確的 CLI 版本
- 當你是透過 gh CLI、PAT、API key 或環境變數登入時，`/logout` 會顯示警告，因為 `/logout` 只管理 OAuth 工作階段
- Alt+D 現在會刪除文字輸入中游標前方的單字
- `/share html` 現在會顯示 `file://` URL，並支援 Ctrl+X O 直接開啟檔案
- skill 指令現在可在對話回合之間正確保留
- 現在可使用 `--remote` 或 `/remote` 遠端控制你的 CLI 工作階段
- MCP 遠端 server 連線現在會在暫時性網路失敗時自動重試
- Share Research TOC 側邊欄錨點連結現在可在頁面內正確導覽

## 1.0.24 - 2026-04-10

- `preToolUse` hooks 現在會正確套用 `modifiedArgs`/`updatedInput` 與 `additionalContext` 欄位
- 自訂 agent 的 model 欄位現在接受來自 VS Code 的顯示名稱與 vendor 後綴（例如 `"Claude Sonnet 4.5"`、`"GPT-5.4 (copilot)"`）
- CLI 因 OOM 或 segfault 等情況崩潰後，終端機狀態（alt screen、cursor、raw mode）現在可正確還原
- 當首次在 GitHub repo 中執行而出現工作階段同步提示時，會正確遵循 `--remote` 旗標
- 重新設計退出畫面，加入 Copilot 吉祥物與更清爽的使用量摘要版面

## 1.0.23 - 2026-04-10

- 新增 `--mode`、`--autopilot` 與 `--plan` 旗標，可在啟動 CLI 時直接進入指定的 agent mode
- 當 memory backend 無法使用時，agent 不再於第一輪卡住
- Bazel/Buck 建置目標標籤（例如 `//package:target`）不再被誤判為檔案路徑
- Ctrl+L 會清除終端機畫面，但不會清除對話工作階段
- 斜線指令選擇器現在會顯示完整的技能描述，並具備更精緻的捲軸
- `/diff`、`/agent`、`/feedback`、`/ide` 與 `/tuikit` 現在可在 agent 執行中使用
- 當推理 token 使用量非零時，會在各模型的 token 明細中顯示
- 遠端分頁現在可正確顯示 Copilot coding agent 任務，並透過 Tasks API 支援遠端控制
- 含有 BEL 字元的 shell 輸出不再導致終端機反覆發出嗶聲
- 針對 `.vscode/mcp.json` 的遷移提示現在包含一個 `jq` 指令，可將設定遷移到 `.mcp.json`

## 1.0.22 - 2026-04-09

- 具有非標準 JSON schema 的 MCP 工具現在會被清理，以確保與所有模型供應商相容
- 改善對來自 MCP 與 extension 工具之大型影像的處理
- 透過新的簡化行內渲染器改善渲染效能
- 當遠端工作階段因政策而遭封鎖時，會顯示清楚訊息，提示你聯絡組織管理員
- 子代理活動不再顯示重複的工具名稱（例如 "view view the file..."）
- 使用 Anthropic 模型搭配 BYOM/BYOK 設定時，權限檢查與其他 hooks 現在可正確運作
- 斜線指令選擇器現在會顯示在文字輸入框上方，以提供更穩定的版面
- 自訂 agents 現在可宣告 `skills` 欄位，以便在啟動時預先將技能內容載入 agent 情境
- Plugins 現在可在安裝後顯示附帶設定說明的安裝後訊息
- 移除 `.vscode/mcp.json` 與 `.devcontainer/devcontainer.json` 作為 MCP server 設定來源；CLI 現在只會讀取 `.mcp.json`。當偵測到 `.vscode/mcp.json` 但沒有 `.mcp.json` 時，會顯示遷移提示。
- Plugins 現在可跨工作階段維持啟用狀態，並依使用者設定在啟動時自動安裝
- 新增子代理深度與併發限制，以防止代理失控地持續產生更多代理
- 當你恢復一個已被其他 CLI 或應用程式使用中的工作階段時，會顯示警告
- CLI 不再於受 V8 引擎 grapheme segmentation 錯誤影響的系統上崩潰
- 在互動模式中，`sessionStart` 與 `sessionEnd` hooks 現在每個工作階段只會觸發一次，而不是每則提示觸發一次
- Plugin agents 現在會遵循其 frontmatter 中指定的模型

## 1.0.21 - 2026-04-07

- 新增 `copilot mcp` 指令以管理 MCP servers
- 當長時間執行的非同步 shell 命令正在進行時，spinner 不再看起來卡住
- 登入流程中的企業 GitHub URL 輸入現在可接受鍵盤輸入，並可按 Enter 送出
- 斜線指令選擇器在過濾時不再閃爍或推擠輸入框
- 當內容縮減時（例如取消操作或工具完成後），時間線不再整片空白
- 計畫模式的時間線顯示現在會直接呈現使用者文字，不再加上多餘的 "Plan" 前綴

## 1.0.44 - 2026-05-08

- `/add-dir` 中的路徑補全不再閃爍，也不會被 `@` 與 `#` 選擇器攔截
- 斜線指令現在可出現在輸入內容的中間，且單一訊息中可同時呼叫多個 skills
- `userPromptSubmitted` hooks 現在可直接處理請求，繞過 LLM，並在不發出模型呼叫的情況下直接回傳回應
- 多帳號使用者的 `/user list` 與 `/user switch` 現在更快
- 為 `copilot update` 與 `/update` 新增可選的 `prerelease` 引數，以取得最新的預發行版本
- 透過 `!` 前綴執行的 shell 指令現在可正確搭配所有 shell 設定運作
- shell aliases 與 rc 檔設定現在可在 `!` 指令中生效
- 配額顯示現在會正確顯示 Free 使用者的剩餘用量，而不再一律顯示為已用 100%
- 在 Autopilot mode 中授與的工具權限，在執行 `/clear` 後仍會保留
- 透過 `/model` 選擇器切換模型時，effort level 現在會正確套用
- 當權限提示正在等待時按下 Ctrl+C，不再導致 CLI 卡住
- 當沒有任何符合結果時，專案資訊仍會顯示在斜線指令選擇器中
- `settings.json` 中無效的 URL 項目不再導致 CLI 啟動崩潰，而會略過並顯示警告
- 時間線現在會顯示 rubber-duck 子代理實際解析後的模型（例如 `Rubber-duck(claude-opus-4.7)`）

## 1.0.43 - 2026-05-06

- 在 `/statusline` 選擇器中新增使用者名稱切換，可在頁尾顯示目前啟用的帳號
- Auto mode 現在使用伺服器端模型路由，以改善即時模型選擇
- 當有多個工作階段同時啟用時，resume 提示現在會顯示正確的工作階段名稱
- 防範巢狀於專案內的惡意裸儲存庫造成遠端程式碼執行（RCE）
- MCP server 子程序（例如透過 `npx` 或 `uvx` 啟動）現在會在工作階段結束時完整終止
- 執行更新指令時現在會顯示下載進度

## 1.0.42 - 2026-05-06

- 當 MCP server 名稱含有空白字元時，MCP server 失敗警告現在會建議可直接執行的 `/mcp show` 指令
- MCP server 失敗警告現在包含 stderr 輸出，以協助診斷連線錯誤
- 新增 `-C <directory>` 旗標，可在啟動前切換工作目錄，類似 `git -C`
- 當工作階段尚未重新命名時，退出訊息中的 resume 指令現在會顯示工作階段 ID，而不是自動產生的名稱
- 遠端工作階段匯出現在支援非 GitHub 儲存庫與沒有儲存庫的目錄
- 選擇 "Go back" 之後，恢復工作階段不再錯誤顯示 "session in use" 警告
- 取消請求後，Enter 鍵不再永久卡住
- 當工作階段沒有使用者訊息，且也沒有可供 resume 的已儲存工作階段時，會隱藏退出摘要
- Windows 上的 CLI 更新在套件解壓縮期間發生暫時性 EPERM 時，不再因 ENOENT 失敗
- 為 GPT 工作階段新增 rubber-duck agent，由 Claude 提供支援（可於 `/experimental` 使用）

## 1.0.41 - 2026-05-05

- CLI 現在會先立即渲染 UI，同時在背景完成驗證，因此啟動更快
- Shell 補全（bash、zsh、fish）現在會在首次執行時自動安裝，並在 `copilot update` 後更新
- 對接受參數的斜線指令使用 Tab 補全時，現在會自動補上尾隨空白
- 在 Windows 上，當防毒軟體或檔案系統鎖定導致暫時性的 EPERM 錯誤時，套件解壓縮不再崩潰
- 遠端工作階段連線錯誤現在會顯示你目前登入的帳號，以及量身調整的修復步驟
- ask user 提示中的問題現在會渲染 Markdown 格式
- 新增實驗性 MCP Tasks 支援：具有 `taskSupport: "required"` 的 MCP 工具會以不阻塞的背景代理執行，並可透過 `list_agents` 與 `read_agent` 追蹤（僅在啟用 experimental mode 時可用，例如透過 `/experimental on` 或 `--experimental` 旗標）
- Extensions 現在會在 prompt mode (`-p`) 載入。使用者 extensions 預設會載入；專案 extensions 與 management tools 則需要 `GITHUB_COPILOT_PROMPT_MODE_EXTENSIONS=true`
- 助手回應不再包含多餘的 system notification XML 標籤
- 大型輸出指引現在會正確引用已設定的 grep 工具名稱
- 使用 git SSH URL（例如 `git@github.com:owner/repo`）新增 plugin marketplace 現在可正確運作
- 斜線指令選擇器現在會搜尋指令描述，並為符合的字元加上底線
- Memory 工具的確認提示現在在請求儲存記憶權限時，會顯示儲存範圍（repository 或 user）
- 對於 INSERT OR IGNORE/REPLACE 與 blocked 狀態更新，SQL todo 時間線項目現在顯示得更準確
- 在較慢或負載較高的主機上，串流文字與 shimmer 動畫仍可維持流暢
- 在非互動模式（`-p/--prompt`）新增 `--attachment` 旗標，可將檔案（影像或原生文件）附加到初始提示
- `@` 提及補全現在支援 `./` 路徑、不再對目錄補上尾隨空白，並會優先顯示專案檔案而非工作區根目錄
- 透過避開 Node 24.x 中的 V8 崩潰問題來提升 Windows 上的穩定性
- 含有 Unicode line separator 字元的工作階段檔案現在可正確載入
- Reasoning effort 選擇器的提示文字現在會以正確間距顯示 "Esc to cancel"
- 透過更妥善地從模糊或錯位的編輯區塊中恢復，提升檔案編輯的可靠性

## 1.0.40 - 2026-05-01

- PR 分支裝飾現在可在頁尾正確顯示，不受模型名稱長度影響
- `/clear` 與 `/new` 會重設目前啟用的自訂 agent 選擇
- 助手回應串流現在有更平順的文字輸出
- 執行 `copilot plugin update` 之後，`copilot plugin list` 會顯示正確版本
- 為 MCP 伺服器新增 `client_credentials` OAuth grant type 支援，可在不使用瀏覽器的情況下進行完全無頭的驗證
- 子代理現在會正確依照自己的模型判斷工具搜尋支援，而不再沿用父工作階段的設定
- 透過 `/new` 或 `/resume` 切換工作階段時，不再把待處理訊息帶到新工作階段
- 傳送大型檔案附件時，CLI 不再卡在 100% CPU
- Resume 工作階段選擇器不再對同一個由 Mission Control 支援的工作階段顯示重複項目
- 工作階段恢復選擇器現在會以單行顯示摘要，並依欄寬截斷
- 在 prompt mode 期間按下 Ctrl+C 時，會立即將 "Exiting…" 輸出到 stderr，讓關閉進度可見
- `/research` 現在使用 orchestrator/subagent 模型，以提供更完整且更可靠的深度研究結果
- Autopilot mode 現在預設將 continuation messages 限制為 5 則（可用 `--max-autopilot-continues` 設定）
- 自動更新時，會自動清理磁碟上舊的 CLI 套件版本
- 遠端工作階段 statusline 現在顯示遠端工作目錄與分支，而不是本地情境
- `/update` 在重新啟動後不再重新送出原始的 `-i` 提示
- 現在會偵測 Azure DevOps 儲存庫並自動停用 GitHub MCP server
- 工作階段歷史記錄、檔案追蹤與 `/chronicle` 指令現在已對所有使用者開放
- Skills 現在可在 ACP 用戶端中作為斜線指令使用，與 CLI 體驗一致
- 恢復工作階段後，不再在先前 CLI 行程意外結束時誤報該工作階段仍在使用中
- `--config-dir` 現在會正確傳遞到 plugin 子指令；`--config-dir` 已棄用，改以 `COPILOT_HOME` 取代
- 當 `/ask` 回應對話框開啟時，滑鼠選取可正常運作，因此內容可以被反白與複製
- 透過非同步載入自訂 CA 憑證來提升 CLI 啟動速度
- 遠端控制連結現在會在時間線中顯示完整 URL，而不是顯示 'Open in browser'
- ACP 用戶端（例如 Zed）現在會在 agent 處理多步驟任務時顯示其即時計畫
- 在 statusline 選擇器中新增 custom `statusLine.command` 可見性的切換項
- ACP 用戶端現在可透過 agent config option 列出並切換自訂 agent
- 當多個伺服器共用相同 URL 但使用不同的靜態 OAuth client ID 時，MCP OAuth tokens 現在可正確快取
- 帶有點號或其他無效字元的 MCP 工具名稱現在會被正確清理
- Ctrl+C 與雙擊 Esc 現在會一次移除一則待處理佇列訊息，而不是一次全部移除
- 斜線指令建議現在會將前綴符合排在模糊比對之前
- Prompt mode (`-p`) 現在會將 repo hooks 與 workspace MCP 置於 opt-in 環境變數之後（`GITHUB_COPILOT_PROMPT_MODE_REPO_HOOKS` 與 `GITHUB_COPILOT_PROMPT_MODE_WORKSPACE_MCP`），以提供預設安全的行為

## 1.0.39 - 2026-04-28

- 允許 ACP 用戶端透過工作階段設定切換 allow-all 權限模式
- 為 ACP 工作階段新增 `/compact`、`/context`、`/usage` 與 `/env` 斜線指令
- 按 `ctrl+x` → `b` 可將目前執行中的任務或 shell 命令移到背景
- 子行程 stdio streams 的暫時性 pipe 錯誤不再造成崩潰或觸發誤報的崩潰回報
- `/remote` 狀態輸出現在會針對各種連線狀態顯示可採取操作的提示
- 改善 `--resume` 工作階段選擇器，提供更好的分頁版面、狀態顯示與漸進式載入
- 斜線指令參數選擇器現在會在精確的指令邊界立即開啟，不需要尾隨空白

## 1.0.37 - 2026-04-27

- 位置型權限持久化現在預設為啟用，因此相同目錄中的核准會在不同工作階段之間延續
- 新增 `copilot completion <bash|zsh|fish>` 子指令，可產生子指令、旗標與已知選項值的靜態 shell 補全腳本
- 在會話選擇器中按 `s` 可循環切換排序方式：相關性、最近使用、建立時間或名稱
- ACP 模型設定選項現在包含 description 與 metadata，供使用 configOptions API 的用戶端使用
- 當重新選取相同的模型或 effort 等級時，不再顯示模型與 effort 變更通知
- 在 Linux 上，寫入剪貼簿不再洩漏 X11 handles
- 待處理訊息指示器現在可在提示框旁正確顯示
- 修正切換為 `git branch --show-current` 後，detached HEAD 偵測總是回傳 false 的問題
- 當 skills 出現錯誤或警告時，skill 選擇器清單仍會完整顯示
- `/ask` 回應現在會渲染 markdown，包括表格與格式化連結

## 1.0.36 - 2026-04-24

- 子指令選擇器現在會在高亮項目旁顯示選取指示符號 (❯)
- 當偵測到多個 Copilot 授權時，現在會顯示更清楚的錯誤訊息與直接連結
- 修正 preToolUse.matcher 被忽略的問題。升級後，帶有 matcher 的 hooks 只會在工具名稱完整符合 regex 時執行。
- `/keep-alive` 現在無需 experimental mode 即可使用，以防止 Copilot CLI 啟用期間系統進入睡眠
- `/remote` 指令現在會顯示目前狀態，並支援 `/remote on` 與 `/remote off` 來切換遠端控制
- 已停用的 skills 不再顯示於斜線指令清單中
- 新增 `'changes'` statusline 切換項，用來顯示此會話的新增/刪除行數
- 位於 `.gitignored` 目錄中的自訂 instruction 檔案（例如 `.github/instructions/`）現在可正確載入
- 現在必須連按兩次 Esc 才會取消進行中的工作，以避免意外中斷
- 儲存除錯日誌或回饋封裝時，不再覆寫既有的封存檔案
- 來自 `~/.claude/` 的自訂 agents、skills 與 commands 不再由 Copilot CLI 載入
- Claude Opus 4.6 現在預設使用 medium reasoning effort

## 1.0.35 - 2026-04-23

- 斜線指令現在支援參數與子指令的 Tab 補全
- Shell escape 指令 (!) 現在在設定了 $SHELL 時會使用你的 shell，而不再一律呼叫 /bin/sh
- 在遠端會話中，CLI TUI 的權限提示現在可正確顯示
- 會話選擇器現在會顯示分支名稱、閒置/使用中狀態，並改進了搜尋功能以支援游標
- 模型變更通知現在會同時顯示先前與新的模型名稱
- /update 與 /version 指令現在會遵循你設定的更新頻道
- 會話同步提示現在使用更清楚的標籤，並說明 GitHub.com 的跨裝置同步
- 新增支援用於 GitHub 主機名稱的環境變數 COPILOT_GH_HOST，其優先順序高於 GH_HOST
- 在補全彈出視窗（@ 提及、路徑補全、斜線指令）中，除了 Tab 之外，也可按 Ctrl+Y 接受高亮選項
- 新增 /session delete、delete <id> 與 delete-all 子指令，並可在會話選擇器中按 x 刪除
- MCP 伺服器名稱現在支援空白與特殊字元
- 透過 -i 作為初始提示傳入的技能斜線指令（例如 /skill-name），現在會在啟動時正確辨識
- 當 read_bash 已經返回結果時，shell 補全通知不再重複顯示
- --continue 現在會優先恢復目前工作目錄中的會話，而不是最近互動過的會話
- 狀態列腳本現在包含與模型徽章及 /context 輸出一致的 context window 欄位
- 使用者設定現在儲存在 ~/.copilot/settings.json，並與 config.json 中的內部狀態分離
- 可用 --name 為會話命名，並用 --resume=<name> 依名稱恢復
- Configure Copilot agent 現在在 Windows 上具有 shell 存取權
- 在 Linux 上缺少剪貼簿工具（wl-clipboard 或 xclip）時，現在會顯示包含安裝說明的實用錯誤訊息
- lsp.json 中的 LSP 伺服器項目現在支援可設定的啟動、初始化與預熱逾時
- statusline 中的 context window 指示器現在預設隱藏
- 將 MCP OAuth 移入共用執行階段流程，並在移除 MCP 伺服器時清除相關的 OAuth 狀態。
- 在 /usage 中新增 GitHub 風格的貢獻圖，會依終端機色彩模式調整，並在無色彩終端機中退回為不同字元圖示
- 代理式迴圈中的自訂工具呼叫現在可自我修正
- 文字輸入中的游標移動、刪除與渲染現在可正確處理 emoji 與多碼點字元
- 工具可用性偵測現在在 Windows 上可正確運作
- 會話 token 若在某次互動期間過期，現在會自動處理，無需你重新送出訊息
- 在 /cwd 與 /add-dir 路徑選擇器中，初次使用 Tab 與方向鍵導覽時現在會選到正確項目
- IDE 或擴充功能中斷連線時，暫時性的 I/O 錯誤不再以紅色錯誤項目顯示於時間線中
- ~/.claude/ 中的自訂 agents 與 skills 不再被錯誤載入為 Copilot 專案設定
- Login 指令在驗證後現在可正確恢復互動式輸入
- 顯示大量文字於時間線中時的渲染效能已改善
- 在 MULTI_TURN_AGENTS 下，sync 任務呼叫現在會阻塞直到完成，而不是在 60 秒後自動轉為背景；sync 也不再回傳可重複使用的 agent_id，後續互動請改用 mode: "background"
- Tab 導覽現在支援 Home/End 鍵，可跳到第一個與最後一個分頁
- Plugins 安裝後會立即生效，無需重新啟動
- 新增 continueOnAutoMode 設定選項，可在遇到速率限制時自動切換到 auto model，而不是暫停
- Auto mode 在切換到不支援已設定 reasoning effort 的模型時，不再以錯誤失敗
- 樣式特定的指示檔 (.github/instructions/*.instructions.md) 不再於每次會話時把完整內容都放入 system prompt
- 擴充功能關閉時的錯誤不再在每次會話結束時以 error-level log 噪音出現
- 在存在 LSP 設定時，LSP 重構工具現在會在第一輪就正確註冊
- 新增 HTTP hook 支援，讓 hooks 可將 JSON payload 以 POST 傳送到設定的 URL，而不是執行本機命令
- 在時間線中隱藏子代理的思考內容
- 自訂 agent 名稱現在會顯示在 statusline 頁腳，並可透過 /statusline 切換
- 在啟動對話框中按下 Escape 不再導致競態條件
- grep 與 glob 工具現在接受多個搜尋路徑

## 1.0.34 - 2026-04-20

- 速率限制錯誤訊息現在顯示「session rate limit」而不是「global rate limit」

## 1.0.33 - 2026-04-20

- 使用 --resume 或 --continue 恢復遠端會話時會自動沿用 --remote 旗標，無需再次指定
- 新增 /bug、/continue、/release-notes、/export 與 /reset 作為指令別名
- 當你輸入未識別或拼寫錯誤的斜線指令時，斜線指令選擇器會建議相近指令
- 新增 /upgrade 作為 /update 指令的別名
- 在啟用內容排除政策時，Grep 在大型儲存庫中不再逾時
- 非互動模式會在退出前等待所有背景代理完成
- 技能選擇器可正確截斷 CJK/日文描述與過長技能名稱而不換行
- 在斜線指令選擇器中按 Enter 會選取高亮的指令
- `ctrl+t` 用於切換推理顯示，現在列在 /help 與 ? 覆蓋說明中
- auto 模式中的子代理現在會沿用會話模型
- 在使用上限達到 50% 與 95% 時顯示警告，讓你在觸及速率限制前更早收到通知
- 在任務對話框中使用 j/k 進行 Vim 風格導覽，並用 x 結束任務

## 1.0.32 - 2026-04-17

- 在 --resume 與 /resume 中允許使用短的工作階段 ID 前綴（7+ 個十六進位字元），不再必須完整 ID
- /feedback 在工作目錄不可寫入時，會將封裝檔儲存到 TEMP
- 將模型選為 `auto`，讓 Copilot 為每個會話自動選擇最佳可用模型
- 新增 --print-debug-info 旗標以顯示版本、終端機能力與環境變數
- 當接近每週使用上限的 75% 與 90% 時顯示警告
- 可將支援的文件檔附加到提示中，供代理閱讀與推理
- 新增 --connect 旗標，可依 ID 直接連線到遠端會話
- copilot login --host 現在可正確與 GitHub Enterprise Cloud (GHE) 執行個體驗證
- 代理情境中的目前日期與時間現在包含本地時區偏移
- 代理思考期間終端機進度指示器會保持顯示
- 在像 Neovim 這類終端機中，/clear 後狀態列不再顯示多餘的 Unicode 字形
- 使用 /cd 變更目錄後，Rewind 可正確運作
- 使用 /plan 與計畫模式時，多行輸入會被保留
- 只有在輸入為空時，Backspace 才會正確退出 Shell 模式
- 在 /ask 對話框中，滑鼠滾輪捲動可正確運作
- 遭遇速率限制的會話現在會暫停佇列訊息並自動重試，而不是丟棄它們
- 表格現在以正確欄寬渲染，支援表情符號，且在終端機調整大小時邊框保持穩定
- 速率限制錯誤訊息現在會根據達到的限制類型顯示具體情境
- 工作階段閒置逾時現在可透過 --session-idle-timeout 設定；預設停用
- 超過 token 限制的技能仍可被發現，且可透過名稱呼叫

## 1.0.31 - 2026-04-16

- 提示框不再在 Windows 與 Ubuntu 終端機造成渲染問題

## 1.0.30 - 2026-04-16

- 回饋表單連結到正確的 GitHub 儲存庫
- /undo 在無法使用 rewind 時會顯示說明訊息（例如不在 git 儲存庫中或尚無提交）
- 使用 skills.discover 時，外掛技能與指令可正確被發現
- 新增 /statusline 指令（含 /footer 別名）以自訂狀態列中顯示的項目（directory、branch、effort、context window、quota）
- 移除 --list-env 旗標，該旗標會在提示模式記錄已載入的外掛、代理、技能與 MCP 伺服器
- 修復括號貼上處理回歸後，從剪貼簿貼上影像恢復正常
- 所有平台上 Ctrl+V 與 Meta+V 都會觸發影像貼上

## 1.0.29 - 2026-04-16

- 遠端 MCP 伺服器設定現在允許省略 type 欄位，預設為 http
- 游標閃爍時維持穩定寬度，文字不再在閃爍期間位移
- 新增 `--list-env` 旗標，在提示模式執行時記錄已載入的外掛、代理、技能與 MCP 伺服器，協助在 CI 流水線中驗證環境設定
- 新增對 Claude Opus 4.7 的支援
- Shell 指令與 MCP 伺服器現在會收到 COPILOT_AGENT_SESSION_ID 作為環境變數
- 代理現在會從 git remote URL 正確辨識儲存庫擁有者，而不是使用本機使用者名稱
- Windows 上發生當機退出後，終端機狀態可正確還原

## 1.0.28 - 2026-04-16

- 在 git 子模組內工作時，權限提示會顯示正確的儲存庫路徑
- 當 read_agent 已在等待結果時，不再重複送出背景代理完成通知
- MCP 遷移提示現在改為連結到含各平台指示的文件，而不是內嵌 shell 指令
- 執行 az CLI 指令時，Azure 資源 ID 不再觸發錯誤的路徑安全警告
- Rewind 選擇器導覽簡化為方向鍵與 Enter，移除令人困惑的 1-9 快速選擇捷徑
- 當設定的編輯器無法啟動時會顯示明確的錯誤訊息
- 吉祥物在啟動時會播放短暫的眨眼序列，而不是持續眨眼
- 可從 —resume 選擇器連線到 CLI 遠端控制會話
- 支援 COPILOT_DISABLE_TERMINAL_TITLE 環境變數，可停用終端機標題更新

## 1.0.27 - 2026-04-15

- Copilot Pro 試用被暫停時會顯示清楚訊息，而不是一般的政策錯誤
- 狀態列在輸入時顯示 @files 與 #issues 提示，當斜線指令選擇器開啟時顯示 /help 提示
- WSL 上複製到剪貼簿不再在貼上文字中夾帶不可見的 BOM 字元
- 新增 /ask 指令，可快速提問且不影響對話歷史
- 新增 `copilot plugin marketplace update` 指令以重新整理外掛目錄

## 1.0.26 - 2026-04-14

- Esc 鍵現在可穩定關閉 ask_user 與 elicitation 提示，不會卡住
- 在 find -exec 區塊內的引數不再出現多餘的目錄存取提示
- 當情境壓縮在檢查點邊界將工具呼叫拆分時，代理會話不再因無法復原的錯誤而失敗
- bash 命令中的單段以斜線開頭權杖（例如 /help、/start）不再被視為檔案路徑
- Anthropic BYOM 在檢視影像檔案時會正確包含影像資料
- 權限提示通知 hook 只會在實際向使用者顯示提示時觸發
- ctrl+o 現在會像 ctrl+e 一樣展開所有時間軸項目
- 遠端分頁會正確顯示 Copilot coding agent 任務，並支援引導而不需要 Pull Request
- 在 --remote 旗標與 /remote 指令說明中，將「steering」重新命名為「remote control」
- 避免傳送重複的自訂指令檔（例如內容相同的 copilot-instructions.md 與 CLAUDE.md），以減少每回合浪費的 token
- 外掛 hooks 會收到 PLUGIN_ROOT、COPILOT_PLUGIN_ROOT 與 CLAUDE_PLUGIN_ROOT 環境變數，其值為外掛的安裝目錄
- ACP 伺服器只綁定在 localhost，避免非預期的網路暴露
- 從 marketplace 安裝名為 'git' 的外掛不再因錯誤的 URL 解析而失敗
- 企業登入現在接受不含 URL scheme 的主機名稱（例如 'github.example.com'）
- LSP 語言伺服器在 Windows 上可使用正確的檔案 URI 路徑正確初始化
- 檔案編輯操作中的相對路徑會以會話工作目錄作為解析基準
- 同步提示中的會話範圍選擇器現在更醒目，並可用左右方向鍵進行鍵盤導覽
- 具有特定 applyTo 模式的指令檔會整合為表格，而不是內嵌完整內容，以減少情境視窗使用量

## 1.0.25 - 2026-04-13

- 在 CLI 中從 registry 安裝 MCP 伺服器，並提供引導式設定
- /resume 會話查找失敗後，Esc 鍵可正常運作
- 在會話歷史中持久保存解析後的模型，並在進行中的回合期間延後模型變更
- ACP 用戶端現在可在啟動或載入會話時提供 MCP 伺服器（stdio、HTTP、SSE）
- 選擇目前模型時，現在會遵循 `--config-dir` 旗標
- 新增 /env 指令以顯示已載入的環境細節（指令、MCP 伺服器、技能、代理、外掛）
- /share 在自訂輸出路徑未含副檔名時，會自動補上正確副檔名（.md 或 .html）
- /add-dir 可接受相對路徑（例如 ./src、../sibling），並會解析為絕對路徑
- 自訂指令檔現在會保留 & 與 <placeholders> 等特殊字元
- 技能選擇器清單在超過終端機高度時可正確捲動
- MCP 用戶端在與伺服器握手時會回報正確的 CLI 版本
- /logout 在透過 gh CLI、PAT、API key 或環境變數登入時會顯示警告，因為 /logout 只管理 OAuth 會話
- Alt+D 現在會刪除文字輸入中游標前的單字
- /share html 會顯示 file:// URL，並支援 Ctrl+X O 直接開啟檔案
- 技能指示在對話回合之間可正確持久保存
- 現在可使用 --remote 或 /remote 遠端控制 CLI 會話
- MCP 遠端伺服器連線在暫時性網路失敗時會自動重試
- Share Research 的目錄側欄錨點連結現在可在頁面內正確導覽

## 1.0.24 - 2026-04-10

- preToolUse hooks 現在會遵循 modifiedArgs/updatedInput 與 additionalContext 欄位
- 自訂代理的 model 欄位現在接受來自 VS Code 的顯示名稱與供應商尾碼（例如 "Claude Sonnet 4.5"、"GPT-5.4 (copilot)"）
- CLI 因 OOM 或 segfault 等崩潰後，終端機狀態（替代螢幕、游標、raw 模式）可正確還原
- 在 GitHub 儲存庫首次執行時出現會話同步提示時，會正確遵循 `--remote` 旗標
- 退出畫面重新設計，加入 Copilot 吉祥物並提供更乾淨的使用摘要版面

## 1.0.23 - 2026-04-10

- 新增 `--mode`、`--autopilot` 與 `--plan` 旗標，可讓 CLI 直接以特定代理模式啟動
- 當記憶體後端不可用時，代理在第一輪不再卡住
- Bazel/Buck 建置目標標籤（例如 `//package:target`）不再被誤判為檔案路徑
- Ctrl+L 現在會清除終端機畫面，但不會清除對話會話
- 斜線指令選擇器現在顯示完整技能說明，並改進捲動條
- 代理執行中仍可使用 `/diff`、`/agent`、`/feedback`、`/ide` 與 `/tuikit`
- 當推理 token 使用量不為零時，會在每個模型的 token 分解中顯示
- 遠端分頁會正確顯示 Copilot coding agent 任務，並支援透過 Tasks API 進行引導
- 含有 BEL 字元的 Shell 輸出不再造成終端機反覆嗶聲
- 針對 .vscode/mcp.json 的遷移提示現在包含 jq 指令，可將你的設定遷移到 .mcp.json

## 1.0.22 - 2026-04-09

- 針對採用非標準 JSON schema 的 MCP 工具，現在會進行清理以相容所有模型供應商
- 對來自 MCP 與擴充工具的大型影像有更好的處理
- 以新的簡化行內渲染器提升渲染效能
- 當遠端會話被政策封鎖時，會顯示明確訊息提醒聯絡你的組織管理員
- 子代理活動不再顯示重複的工具名稱（例如 "view view the file..."）
- 透過 BYOM/BYOK 設定使用 Anthropic 模型時，權限檢查與其他 hooks 現在可正確運作
- 斜線指令選擇器現在顯示在文字輸入框上方，以提供更穩定的版面
- 自訂代理現在可以宣告 `skills` 欄位，在啟動時預先載入技能內容到代理情境中
- 外掛安裝後現在可顯示包含設定說明的安裝後訊息
- 移除 .vscode/mcp.json 與 .devcontainer/devcontainer.json 作為 MCP 伺服器設定來源；CLI 現在只讀取 .mcp.json。當偵測到沒有 .mcp.json 的 .vscode/mcp.json 時，會顯示遷移提示。
- 外掛在跨會話時仍會保持啟用，並依使用者設定在啟動時自動安裝
- 新增子代理深度與並行限制，以防止代理無限制生成
- 當恢復的會話已被其他 CLI 或應用程式使用時會顯示警告
- CLI 在受 V8 引擎字素分割（grapheme segmentation）錯誤影響的系統上不再當機
- 在互動模式下，sessionStart 與 sessionEnd hooks 現在每個會話只觸發一次，而不是每次提示都觸發
- 外掛代理會遵循其 frontmatter 中指定的模型

## 1.0.21 - 2026-04-07

- 新增 `copilot mcp` 指令以管理 MCP 伺服器
- 當長時間執行的非同步 shell 命令進行中時，旋轉指示器不再看起來卡住
- 登入流程中的企業 GitHub URL 輸入現在可接受鍵盤輸入並在按下 Enter 時提交
- 斜線指令選擇器在過濾時不再閃爍或移動輸入框
- 當內容縮減時（例如取消或工具完成後），時間軸不再空白
- 計畫模式的時間軸顯示使用者文字時，不再有多餘的「Plan」前綴
- 透過自動關閉不再需要的 shell 會話來降低記憶體使用量
- 使用 PascalCase 事件名稱設定的 hooks 現在會收到與 VS Code 相容的 snake_case payload，包含 hook_event_name、session_id 與 ISO 8601 時間戳

## 1.0.20 - 2026-04-07

- 新增 `copilot help monitoring` 主題，包含 OpenTelemetry 設定細節與範例
- 旋轉指示器會一直保持啟動，直到背景代理與 shell 命令完成，且使用者輸入全程可用
- Azure OpenAI BYOK 在未設定 API 版本時，預設使用 GA 的無版本 v1 路徑
- 降低即時回應串流期間的 UI 遲滯
- `/yolo` 與 `--yolo` 現在行為一致，且 `/yolo` 狀態會在 `/restart` 後持續保留

## 1.0.19 - 2026-04-06

- `/mcp enable` 與 `/mcp disable` 現在會跨會話持續生效
- OpenTelemetry 監控：子代理 span 現在使用 `INTERNAL` span 類型，而聊天 span 會包含 `github.copilot.time_to_first_chunk` 屬性（僅串流）
- 在 macOS 上，缺少可執行權限的外掛 hook 腳本現在可正確執行
- 當代理顯示名稱與檔名不同時，恢復會話會正確還原自訂代理
- 當會話已被另一個用戶端使用時，會略過 IDE 自動連線
- 斜線指令時間軸項目現在包含指令名稱（例如 "Review"、"Plan"），以提供更完整的情境

## 1.0.18 - 2026-04-04

- 新的 Critic 代理會使用互補模型自動審查計畫與複雜實作，以提早捕捉錯誤（Claude 模型的實驗模式可用）
- 會話恢復選擇器在首次使用時會依分支與儲存庫正確分組會話
- preToolUse hook 的 permissionDecision 設為 'allow' 時，現在會抑制工具核准提示
- 新增通知 hook 事件，會在 shell 完成、權限提示、elicitation 對話框與代理完成時非同步觸發

## 1.0.17 - 2026-04-03

- CLI 現在內建技能，首先提供的是自訂 Copilot 雲端代理環境的指南
- MCP OAuth 流程現在可透過自簽憑證備援支援 HTTPS 重新導向 URI，提升與要求 HTTPS 的 OAuth 供應商相容性（例如 Slack）
- /resume 會話選擇器載入速度顯著提升，尤其在大型會話歷史時

## 1.0.16 - 2026-04-02

- 當透過 excludedTools 或 availableTools 排除 sql 工具時，SQL 提示標籤不再出現
- MCP 工具呼叫在時間軸中會顯示工具名稱與參數摘要
- 工作目錄變更時，MCP 伺服器會以有效驗證正確重新連線
- 新增 PermissionRequest hook，允許腳本以程式方式核准或拒絕工具權限請求
- 移除已棄用的 `marketplaces` 儲存庫設定（改用 `extraKnownMarketplaces`）
- 登入、切換使用者與 /mcp reload 後，MCP 伺服器會正確載入
- BYOK Anthropic 供應商現在會遵守已設定的 maxOutputTokens 上限
- 移除已棄用的 `marketplaces` 儲存庫設定（改用 `extraKnownMarketplaces`）

## 1.0.15 - 2026-04-01

- 移除對 gpt-5.1-codex、gpt-5.1-codex-mini 與 gpt-5.1-codex-max 模型的支援
- 在互動模式下，Copilot 吉祥物現在會有細微眨眼動畫
- 使用者切換器與 `/user list` 現按字母順序顯示帳號
- 新增 mcp.config.list、mcp.config.add、mcp.config.update 與 mcp.config.remove 伺服器 RPC，用於管理持久化的 MCP 伺服器設定
- 在無介面與 CI 環境中，新增裝置代碼流程（RFC 8628）作為 MCP OAuth 的備援
- 新增 `/mcp auth` 指令與 MCP OAuth 伺服器的重新驗證 UI，並支援帳號切換
- 新增 postToolUseFailure hooks 以處理工具錯誤，且 postToolUse 只會在工具成功呼叫後執行
- 新增 `/share html` 指令，可將會話與研究報告匯出為自包含的互動式 HTML 檔案
- 按下 Escape 或 Ctrl+C 取消後，Autopilot 不再繼續
- CLI 載入期間輸入的按鍵不再遺失
- 大型工具輸出預覽會顯示正確的字元數，並最多顯示 500 個字元
- diff 檢視器新增 Home/End 與 Page Up/Page Down 導航
- 會話結束後，CLI 會立即退出，不再等待最多 10 秒
- 設定項目 askUser、autoUpdate、storeTokenPlaintext、logLevel、skillDirectories 與 disabledSkills 現改用 camelCase 名稱（仍接受 snake_case）
- 許多設定鍵現在偏好 camelCase 名稱（snake_case 名稱仍可使用）
- Ctrl+D 不再排入訊息；請改用 Ctrl+Q 或 Ctrl+Enter 進行排隊
- 連線較慢的 MCP 伺服器不再阻塞代理啟動
- 在 WSL 環境中，從 Windows 剪貼簿貼上圖片現在可正常運作

## 1.0.14 - 2026-03-31

- 使用 BYOM 時，影像會正確傳送到 Anthropic 模型
- 模型選擇器的選擇現在會正確覆寫目前會話的 `--model` 旗標
- 錯誤退出時，終端機輸出不再清空或跳動
- 在支援 Kitty keyboard protocol 的終端機中，Shift+Enter 會插入換行
- 當 Git marketplace URL clone 失敗時，顯示底層錯誤細節
- 在 macOS 上，暫存檔操作不再觸發不必要的權限提示
- 允許 SDK 會話參與者透過 `handlePendingElicitation` API 回應 elicitation 請求
- 會話結束時會正確清理 Shell 程序
- 無論是否設定直接回呼，SDK 的 exit_plan_mode.requested 事件現在一律會發送
- 使用 Microsoft Entra ID 驗證的 MCP 伺服器不再在每次登入時顯示同意畫面
- Grep 與 glob 搜尋在達到逾時時會即時回傳結果
- 在 elicitation 對話框中快速輸入時不再掉字
- 在原生 Windows 上，複製到剪貼簿的文字不再在貼上開頭多出 U+FEFF 字元
- 修正在恢復會話時忽略 `--config-dir`，導致路徑悄悄回退到 `~/.copilot` 的問題
- 被 allowlist 政策封鎖的 MCP 伺服器現在會在 `/mcp show` 中隱藏
- 使用 Bring Your Own Model (BYOM) 供應商時，推理強度設定現在會正確套用
- 使用傳統 PAT 時會顯示清楚的錯誤訊息
- `grep` 工具可處理大型檔案與長行而不會耗盡記憶體
- CLI 於 ACP 模式執行時，MCP 伺服器 OAuth 驗證可正常運作
- 以空白分割 `$BROWSER`
- 啟用滑鼠支援時，貼上的文字不再毀損
- 解除安裝 marketplace 外掛時會移除其磁碟上的快取資料
- 透過最佳化旋轉指示器渲染與任務輪詢，降低串流期間的 CPU 使用率
- 透過並行執行終端機偵測、驗證與 git 操作，縮短 CLI 啟動時間
- MCP registry 查詢加入自動重試與請求逾時後更可靠
- V8 編譯快取降低重複啟動的解析與編譯時間，CLI 因此啟動更快
- 移除對 `gemini-3-pro-preview` 模型的支援

## 1.0.13 - 2026-03-30

- 會話結束時會正確清理 Shell 程序
- 透過最佳化旋轉指示器渲染與任務輪詢，降低串流期間的 CPU 使用率
- 無論是否設定直接回呼，SDK 的 exit_plan_mode.requested 事件現在一律會發送
- 使用 Microsoft Entra ID 驗證的 MCP 伺服器不再在每次登入時顯示同意畫面
- Grep 與 glob 搜尋在達到逾時時會即時回傳結果
- 在 elicitation 對話框中快速輸入時不再掉字
- 在原生 Windows 上，複製到剪貼簿的文字不再在貼上開頭多出 U+FEFF 字元
- 修正在恢復會話時忽略 `--config-dir`，導致路徑悄悄回退到 `~/.copilot` 的問題
- 透過並行執行終端機偵測、驗證與 git 操作，縮短 CLI 啟動時間
- `/rewind` 與連按兩次 Esc 現在會開啟時間軸選擇器，可回復到對話歷史中的任何時間點，而不僅是前一個快照
- MCP registry 查詢加入自動重試與請求逾時後更可靠
- V8 編譯快取降低重複啟動的解析與編譯時間，CLI 因此啟動更快
- MCP 伺服器可透過新的審核提示，在使用者核准後請求 LLM 推論（sampling）
- 被 allowlist 政策封鎖的 MCP 伺服器現在會在 `/mcp show` 中隱藏
- 使用 Bring Your Own Model (BYOM) 供應商時，推理強度設定現在會正確套用
- 使用傳統 PAT 時會顯示清楚的錯誤訊息
- `grep` 工具可處理大型檔案與長行而不會耗盡記憶體
- CLI 於 ACP 模式執行時，MCP 伺服器 OAuth 驗證可正常運作
- 以空白分割 `$BROWSER`
- 啟用滑鼠支援時，貼上的文字不再毀損
- 解除安裝 marketplace 外掛時會移除其磁碟上的快取資料
- 移除對 `gemini-3-pro-preview` 模型的支援

## 1.0.12 - 2026-03-26

- 在工作目錄是 git 根目錄時，.mcp.json 中定義的 MCP 伺服器可正確啟動
- 在 Windows 上，當 PATH 中的非系統 clip.exe 覆蓋系統版本時，剪貼簿複製可正確運作
- `/diff` 檢視在有行內高亮時可正確渲染所有行
- 外掛 hooks 現在會收到 `CLAUDE_PROJECT_DIR` 與 `CLAUDE_PLUGIN_DATA` 環境變數，並在 hook 設定中支援 `{{project_dir}}` 與 `{{plugin_data_dir}}` 範本變數
- 工作區 MCP 伺服器現在會正確載入並對代理可見
- `/clear` 會在新會話中保留 MCP 伺服器
- 模型顯示標頭現在會在模型名稱旁顯示目前的推理強度（例如 "(high)"）
- `/session rename` 在未提供名稱參數時會從對話歷史自動產生會話名稱
- 移除 `--alt-screen` 旗標與 `alt_screen` 設定；替代螢幕現在一律啟用
- OSC 8 超連結現在可在 VS Code 終端機中點擊
- PowerShell 的 /flag 參數（例如 /all、/enum-devices）不再被誤判為檔案路徑
- 受信任資料夾存取提示不再在 Windows OneDrive 路徑與不區分大小寫的檔案系統上錯誤出現
- 狀態列 payload 現在除了 `session_id` 之外也包含 `session_name` 欄位
- `@` 檔案選擇器不再顯示 `.git` 目錄內容
- 調整終端機大小時捲動位置會保持不變
- 使用 `/clear` 開始新會話後，`/yolo` 的路徑權限仍會保留
- 在終端機文字選取時，Emoji 字元可正確被選取與高亮
- 具有進行中工作的會話不再被過期會話清理器移除
- 恢復會話會還原先前選擇的自訂代理
- 執行產生大量輸出的 Shell 指令時，CLI 不再因記憶體不足而當機
- 在取消 autopilot 時連按多次 Escape 不再導致會話卡住
- 將 `.claude/settings.json` 與 `.claude/settings.local.json` 讀取為額外的儲存庫設定來源
- 模型選擇器現在以全螢幕檢視開啟，並可用 ← / → 方向鍵就地調整推理強度
- OTEL hook 執行現在記錄為 span events 而非子 span，減少追蹤雜訊
- 使用者提示在按下 Enter 後會立即出現在對話中
- `/allow-all`（`/yolo`）現在支援 `on`、`off` 與 `show` 子命令，用於啟用、停用或檢查 allow-all 模式
- 在計畫模式下按 Ctrl+Y，當尚無計畫時會開啟最新的研究報告

## 1.0.11 - 2026-03-23

- 確保模型在選擇器中正確顯示，並在可能時顯示模型名稱
- 當 MCP 伺服器因政策（例如 allowlist 強制）被封鎖時顯示警告
- 第三方 MCP 伺服器的組織政策現在對所有使用者強制生效
- 新增 ~/.agents/skills/ 作為個人技能探索目錄，與 VS Code 的 GHCP4A 擴充功能預設一致
- 來自多個擴充功能的 hooks 現在會合併，而非互相覆寫或覆寫 hooks.json 中的 hooks
- sessionStart hook 的 additionalContext 現在會注入到對話中
- /clear 現在會完全放棄目前的會話，而 /new 會開始新的對話（保留舊會話在背景）
- 連線到遠端主機時，會遵循 GitHub MCP 伺服器的使用者設定
- 程序暫停與恢復（Ctrl+Z / fg）後，終端機畫面可正確重繪
- MCP OAuth 驗證可在支援 Dynamic Client Registration、但將授權中繼資料放在非標準 URL 的 MCP 伺服器（例如 Atlassian Rovo MCP Server）上正常運作
- /cd 會為每個會話維持獨立工作目錄，切換會話時會還原
- 自訂指令、MCP 伺服器、技能與代理現在會從工作目錄一路往上到 git 根目錄的每個目錄層級進行探索，完整支援 monorepo
- 啟動時的 'Environment loaded' 訊息現在會顯示已載入的 hooks 數量
- 背景代理進度（目前意圖與已完成的工具呼叫）現在會顯示在 read_agent 與 task timeout 的回應中
- statusLine.command 路徑現在支援 ~ 與環境變數（例如 $HOME、${VAR:-default}）
- /new 與 /clear 指令可接受選擇性的提示，讓新會話以第一則訊息開始

## 1.0.10 - 2026-03-20

- 在完整檢視大型檔案時降低記憶體使用量
- /login 裝置流程在 Codespaces 與遠端終端機環境中可正確運作
- 在使用遠端會話的 --server 模式時可正確偵測工作目錄
- 在使用 application keypad mode 的終端機中，方向鍵可正確運作
- 使用提示模式（-p 旗標）時，儲存庫 hooks（.github/hooks/）現在會正確觸發
- 在 Windows 上，/copy 會把格式化 HTML 寫入剪貼簿，方便貼到 Word、Outlook 與 Teams
- SDK 用戶端在啟動或加入會話時可註冊自訂斜線指令
- SDK 用戶端可透過 session.ui.elicitation 向使用者顯示 elicitation 對話框
- 新增多個並行會話的實驗性支援
- 新增 `--effort` 作為 `--reasoning-effort` 的縮寫別名
- 新增 /undo 指令，可復原上一輪並還原檔案變更
- 在 alt-screen 模式下，當內容包含硬換行時，Markdown 項目清單可正確渲染
- Elicitation 表單會顯示 Shift+Tab 提示，用於反向在欄位間導覽
- 遠端會話 URL 會顯示為精簡可點擊的 'Open in browser' 連結，而不是重複的原始 URL
- 透過 /quit、Ctrl+C 或 restart 退出時，會話歷史不再遺失
- 巢狀 hook 結構中定義的 hook matcher 過濾器，現在會正確套用到內層 hook 項目
- 使用 .claude-plugin/ 或 .plugin/ manifest 目錄的外掛，現在可正確載入其 MCP 與 LSP 伺服器
- /terminal-setup 不再對 WSL 使用者顯示誤導性的錯誤
- 模型選擇器會依使用者方案與政策，將模型重新整理為 Available、Blocked/Disabled 與 Upgrade 分頁
- 來自 .mcp.json、.vscode/mcp.json 與 devcontainer.json 的工作區 MCP 伺服器，現在只會在資料夾信任確認後載入
- 設定項目已改為 camelCase：`includeCoAuthoredBy`、`effortLevel`、`autoUpdatesChannel`、`statusLine`（舊名稱仍可使用）
- 複製助理回應時，若所選行都含有前置 2 個空白的 UI 縮排，會自動移除該縮排
- 透過 --plugin-dir 載入的外掛，現在會在 /plugin 清單中以獨立的「External Plugins」區段顯示

## 1.0.9 - 2026-03-19

- 在 SSH 中斷或關閉終端機時，時間軸中不再出現多餘的 I/O 錯誤訊息（ENOTCONN、EIO）
- 新增 include_gitignored 設定選項，可在 @ 檔案搜尋中包含被 gitignore 的檔案
- 在 WSL 複製文字時可正確保留 CJK 與其他非 ASCII 字元
- 從縮短網址（例如 aka.ms 連結）安裝 marketplace 與外掛現在可正常運作

## 1.0.8 - 2026-03-18

- 代理模式的標籤與邊框在非 truecolor 終端機（tmux、SSH、screen）上顯示正確的色彩
- 為了更乾淨的終端機體驗，現在預設啟用替代螢幕緩衝區
- 當擴充功能子程序加入作用中會話時，exit plan mode 工具仍可使用
- 儲存庫層級 hooks 只會在資料夾信任確認後載入，而不是在信任對話框顯示前
- 閒置子代理不再擠滿 /tasks 檢視——在 2 分鐘未活動後會隱藏
- 新增 extension mode 設定以控制可擴充性
- 使用實驗性的 MCP_ALLOWLIST 功能旗標時，可依設定的 registry 驗證 MCP 伺服器
- 允許 `--resume` 除了 session ID 之外也接受 task ID
- 支援在 `settings.json`、`settings.local.json` 與 `config.json` 中定義 hooks
- 在 macOS Terminal.app 與其他不支援 SGR mouse encoding 的終端機中，捲動現在可正確運作
- 從外部編輯器返回後，tmux 中的滑鼠捲動可正確運作
- 提示模式下按 Ctrl+C 現在會立即退出，不再等待請求完成
- 旋轉指示器動畫不再延遲可見輸出出現在時間軸中
- 對話框標題在所有對話框內顯示一致

## 1.0.7 - 2026-03-17

- 改善各 CLI 主題的色彩對比度，以提升可讀性與可近用性
- 使用者訊息會以淡色背景顯示，以與助理訊息做視覺區隔
- 新增 gpt-5.4-mini 模型支援
- 分頁列的選取分頁使用精簡的 [label] 樣式並有更乾淨的間距
- 在 system message 設定中新增 "customize" 模式，以進行區段層級的 system prompt 覆寫
- 按兩次 Esc：有文字時清空輸入；提示為空時觸發復原，且在第一次按 Esc 後會顯示提示
- 1.0.6 之前建立的會話在恢復時不再出現 'Session file is corrupted' 而失敗
- 標頭中的分支指示器可區分未暫存變更（*）、已暫存變更（+）與未追蹤檔案（%）
- 新增實驗性的 SDK 會話 API，可列出與管理技能、MCP 伺服器與外掛，並可選擇從工作目錄自動探索設定
- 新增 subagentStart hook，在子代理生成時觸發，並支援把額外情境注入子代理提示
- Pro 與試用使用者現在能在模型選擇器中看到所有有權使用的模型
- CLI 重新啟動時不再把 `-i/--interactive` 提示重新送到新會話
- 修正自動更新在 Windows 上可能留下不完整套件的邊緣案例

## 1.0.6 - 2026-03-16

- Autopilot 的續行不再因前一輪錯誤而永久被阻擋
- 在 autopilot 中，現在必須提供 task_complete 摘要，且會以 Markdown 呈現
- 螢幕閱讀器不再在每次提交提示時朗讀輸入框 placeholder 文字
- Shell 指令解析後會釋放 tree-sitter WASM 物件以防止記憶體洩漏
- `/help` 對話框在 alt-screen 模式下預設捲動到頂部
- 自動更新現在可在 Windows 上正確處理競態條件並復原
- 當另一個執行個體仍在執行時進行更新，CLI 在 Windows 上不再載入失敗
- 透過移除每次子程序啟動時重複的環境變數複製來降低記憶體用量
- 剩餘請求小工具不再對 Copilot Free 使用者顯示不準確的配額資料
- 修正子代理運作時因 HTTP/2 連線池競態導致的會話當機
- 自動更新後，CLI 會載入自己的最新版本
- kill 指令驗證不再錯誤阻擋部分合法命令，例如 Python 腳本中的 `p.kill()`
- 指令檔 frontmatter 的 applyTo 欄位同時接受字串與陣列值
- 改善串流與工具輸出時的記憶體使用
- Claude 模型可透過 tool search 動態發現並使用工具
- 在恢復先前會話時，hooks 會正確觸發
- alt-screen 模式下的提示輸入會完整渲染所有行而不截斷
- 在 VS Code 整合式終端機中，點擊連結與右鍵貼上不再觸發兩次
- Hook 設定檔現在可在 VS Code、Claude Code 與 CLI 之間免修改通用，因為除了 camelCase 事件名稱外也接受 PascalCase
- 原生模組預建檔（例如 Windows ARM64 的 conpty.node）在首次啟動時可可靠載入
- /tasks 檢視中的子代理耗時在閒置時會凍結，重新活動時繼續
- 使用 SDK（ACP 模式）時，`--enable-all-github-mcp-tools`、`--add-github-mcp-toolset` 與 `--add-github-mcp-tool` 旗標現在會生效
- 使用 `COPILOT_CUSTOM_INSTRUCTIONS_DIRS` 時，自訂指令檔路徑可正確載入
- 當某個指令導致 shell 結束時，指令輸出不再遺失
- 透過 `--plugin-dir` 載入時，使用 `.claude-plugin/plugin.json` 的外掛可被正確發現
- 修正在 VS Code 中使用舊版 /terminal-setup 設定時 shift+enter 的處理
- 代理建立精靈會顯示正確的使用者代理目錄路徑
- 支援 Open Plugin 規格的檔案位置，用於載入外掛與 marketplace 的 manifest
- 顯示更友善的錯誤訊息，並提供鍵盤快捷鍵在瀏覽器開啟事件連結
- 擴充功能工具現在與權限系統整合，可在每個工具上使用 `skipPermission` 略過權限提示
- Hook 設定檔現在支援 Claude Code 的巢狀 matcher/hooks 結構與可選的 type 欄位
- 由 task 工具啟動的子代理會依名稱指派可讀 ID（例如 `math-helper-0`），不再是通用的 `agent-0`
- `create_pull_request` 工具的輸出現在包含 PR URL，讓代理可分享直接連結
- `read_agent` 輸出包含在多回合代理中觸發每一輪的入站訊息
- 提升與 Open Plugins 規格的相容性：支援 `.lsp.json`、PascalCase hook 事件名稱、`exclusive` 路徑模式與 `:` 命名空間分隔符

## 1.0.5 - 2026-03-13

- 執行 /clear 或 /new 後，終端機標題會重設為預設值
- 新增 /extensions 指令，可檢視、啟用與停用 CLI 擴充功能
- @ 檔案提及現支援專案外路徑：絕對路徑 (@/usr/...)、家目錄 (@~/...)、相對父層路徑 (@../...)
- 使用 /experimental on|off 切換實驗模式會自動重啟 CLI 以立即套用變更
- 右鍵貼上會進入目前作用中的對話輸入欄位，而非主對話輸入欄位
- 推出 /pr，協助建立與檢視 PR，自動修復 CI 失敗、處理審查回饋並解決合併衝突
- 封鎖網路 (UNC) 路徑，避免透過 SMB 驗證造成憑證外洩
- 可透過 write_agent 工具向背景代理送出後續訊息，以進行多輪對話
- 記憶儲存錯誤現在會指出儲存庫不存在或你缺乏寫入權限
- 當環境變數設定傳統 Personal Access Token (ghp_) 時，會顯示明確錯誤而非靜默退出
- Diff 檢視在 Windows 上可正確顯示，不再出現文字損毀或被覆寫
- 修正在結束時顯示 Kitty 鍵盤通訊協定逸出序列的問題
- 將 claude-sonnet-4.6 設為預設模型現在可正確保留
- 外掛解除安裝會依據已儲存的安裝路徑可靠移除檔案
- 新增 /version 指令，可在會話中顯示 CLI 版本並檢查更新
- 新增實驗性的向量嵌入動態檢索，在每一回合取得 MCP 與技能指令
- /diff 支援語法高亮，涵蓋 17 種程式語言
- 新增 preCompact hook，可在情境壓縮開始前執行指令
- 當重試用盡後仍發生錯誤時，API 的 request ID 現會顯示在時間軸中
- 在 Windows/PowerShell 上，包含反引號格式程式碼的 PR 描述可正確渲染
- 當將檔案路徑當作 CLI 指令傳入時，會顯示有用的錯誤訊息
- 當權杖無效或過期時，會話會回報驗證錯誤而不是卡住
- View 工具在大型單行檔案（例如壓縮的 JS、巨大 JSON blob）上會顯示部分內容，而非空白輸出
- /changelog 支援 `last <N>`、`since <version>` 與 `summarize`，可一次瀏覽與摘要多個版本說明
- 省略 version 欄位的 hooks 設定檔現在也能被 CLI 接受

## 1.0.4 - 2026-03-11

- 新增 `session.shell.exec` 與 `session.shell.kill` RPC 方法，用於執行 Shell 指令並串流 stdout/stderr 輸出
- 在 ACP 模式下，來自 --plugin-dir 外掛的自訂代理現在可正確載入
- 新增具備動態色彩模式與互動式主題選擇器的自適應色彩引擎。在色彩有限的終端機與 Windows 上會優雅降級
- 當回呼連接埠變更或使用 Microsoft Entra ID 時，MCP OAuth 重新驗證可穩定運作
- 以 /pr view [local|web] 取代 /pr open，可在本機檢視 PR 狀態或在瀏覽器開啟
- 啟用 OpenTelemetry 儀器化，以觀測代理會話、LLM 呼叫與工具執行
- 擴充功能現在可用 CommonJS 模組撰寫 (extension.cjs)
- 在 Environment loaded 啟動訊息中顯示已載入的擴充功能數量
- 支援 disableAllHooks 旗標，可從設定檔停用所有 hooks
- 在會話紀錄中支援 Azure DevOps 儲存庫識別
- 在共享 gist 的會話匯出標頭中，會將每個欄位獨立成行呈現
- 自動更新在 SAML 強制錯誤時會改為不帶驗證權杖重試
- Autopilot 模式在 API 錯誤後會停止繼續，而非無限迴圈
- 狀態列的情境視窗百分比改以最後一次呼叫的輸入與輸出權杖計算，不再因累積總量而膨脹
- 在使用 alt-screen 時，暫停後會正確停用 Kitty 鍵盤通訊協定
- 只有在僅有推理文字可用時才顯示 reasoning 標題
- CLI 當機時終端機會正確重置，避免 Shell 損壞
- /update 指令會自動重新啟動以套用更新，無需手動退出
- OAuth 驗證現在可在 Microsoft Entra ID 與其他 OIDC 伺服器上穩定運作，並正確處理 resource 指示器與 refresh token 支援
- 在 /instructions 選擇器中顯示個別指令檔名，對注入的檔案加上 [external] 標籤
- 路徑權限對話框除了將路徑加入允許清單外，還提供一次性核准選項
- 新增 --reasoning-effort CLI 旗標以設定推理強度
- Hooks 現可透過 'ask' 權限決策在工具執行前請求使用者確認
- 新增 configure-copilot 子代理，可透過 task 工具管理 MCP 伺服器、自訂代理與技能
- 互動式 Shell 初始化在慢速機器上不再逾時
- Windows 上的 Shell 指令更快，因為略過 PowerShell 設定檔載入
- 改進 CLI 說明文件，改用標準 --option=value 格式與逗號分隔清單語法

## 1.0.3 - 2026-03-09

- 對員工使用者預設啟用 alt-screen 緩衝區
- 擴充功能現以實驗性功能提供——可要求 Copilot 使用 @github/copilot-sdk 為自己撰寫自訂工具與 hooks
- 在說明中記錄 GH_HOST、HTTP_PROXY、HTTPS_PROXY、NO_COLOR 與 NO_PROXY 環境變數
- 從 .devcontainer/devcontainer.json 讀取 MCP 伺服器設定
- 新增 --binary-version 旗標，可在不啟動 CLI 的情況下查詢二進位版本
- 新增 /restart 指令，可在保留會話的情況下熱重啟 CLI
- 背景任務通知會在時間軸顯示，並可展開細節
- 除了 'exit' 之外，輸入 'quit' 也可離開 CLI
- 新增 extraKnownMarketplaces 儲存庫設定，用於取代 marketplaces
- /terminal-setup 指令新增 Windows Terminal 支援
- /reset-allowed-tools 現可完全撤銷 /allow-all，並重新觸發 autopilot 權限對話框
- 改善 SQL 工具對批次查詢的處理
- 當系統鑰匙圈無回應時，Ubuntu 上的登入流程不再卡住
- CLI 意外當機時，終端機會正確重置
- 在螢幕閱讀器模式下，表格會停用邊框以避免朗讀裝飾字元
- outputSchema 不符合規範的 MCP 伺服器現在可使用
- /plugin update 現可用於 GitHub 安裝的外掛
- /add-dir 加入的目錄會在 /clear 與 /resume 等會話變更後持續保留
- 避免將 env 指令視為可在未經核准下允許的安全指令
- 在狹窄終端機換行時，placeholder 文字色彩會正確顯示
- /plugin update 現可搭配專案設定中定義的 marketplaces 使用
- 在伺服器錯誤復原期間，重試狀態訊息現在會顯示以呈現進度
- 在 diff 模式抓取變更時顯示載入旋轉指示器
- 當 .github/instructions/ 含有指令時，抑制 /init 建議
- 為了一致性，將 merge_strategy 設定更名為 mergeStrategy
- 抑制技能與指令 frontmatter 中未知欄位的警告
- 允許安全的 sed 指令在無需確認下執行

## 1.0.2 - 2026-03-06

為了紀念 GitHub Copilot CLI 在上週正式推出，我們將主版本號提升到 1.0！

- 輸入單獨的 'exit' 命令即可關閉 CLI
- `ask_user` 表單現在可用 Enter 鍵提交，且 enum 欄位允許自訂回覆
- 在 hook 設定中支援 `command` 欄位作為 bash/powershell 的跨平台別名
- Hook 設定現在接受 `timeout` 作為 `timeoutSec` 的別名
- 修正搭配控制鍵的 meta 鍵處理（包含從 /terminal-setup 使用 shift+enter）

## 0.0.423 - 2026-03-06

- 對可能包含危險展開或替換用途的 shell 指令會提示使用者確認，新增防範惡意利用的防護
- 對 EMU 與 GHE Cloud 使用者封鎖 /share gist，並提供明確的錯誤訊息
- Elicitation 的 enum 與 boolean 欄位現在需要按 Enter 確認選取，已確認值以 ✓ 標示，瀏覽游標以 ❯ 標示
- MCP 伺服器現在可要求使用者造訪 URL 進行帶外互動，例如 OAuth 流程或輸入 API 金鑰
- 透過更好的脈絡共享，提升 explore agent 精準度與大型儲存庫支援
- 在 Windows 上含 CRLF 行結尾時，Diff 模式可正確顯示

## 0.0.422 - 2026-03-05

- 在驗證與授權錯誤訊息中顯示 request ID，以利除錯
- 除儲存庫層級的 .github/hooks 外，也會載入 ~/.copilot/hooks 的個人 hooks
- 時間軸現在會以方框顯示問題，且當 ask_user 被自動回覆時會顯示 'Making best guess on autopilot'
- 新增 GPT-5.4 模型支援
- 外掛快取可在 clone 損毀或不完整時自動復原，無需手動介入
- 當未安裝 git 且使用遠端外掛或 marketplace 時，會顯示清楚且可操作的錯誤訊息
- 在 alt-screen 中，複製到剪貼簿後文字選取仍會保留
- 在回應串流期間或彈出視窗開啟時捲動，檢視不再跳回較早的訊息
- 新增 copy_on_select 設定選項，可在 alt-screen 模式自動將選取文字複製到剪貼簿
- 在 CJK 輸入時，IME 候選視窗會出現在正確的游標位置
- 在 alt-screen 模式中，/diff 支援滑鼠滾輪捲動
- 在長時間會話中降低 alt-screen 模式的記憶體用量
- 當設定 git color.diff=always 時，Diff 模式可正確運作
- 在 Windows 上開啟連結時可正確處理帶有 & 查詢參數的 URL
- @-mention 檔案補全會始終反映目前工作目錄的狀態
- 在 tmux 與其他非 kitty 終端機中，使用 ESC 取消可正確運作
- 點擊提示輸入框即可重新定位文字游標
- 新增 /copy 指令，可將最後一則回應複製到剪貼簿
- alt-screen 模式下連結會以下劃線樣式渲染以提高可見性
- 在多遠端儲存庫中，/delegate 會提示選擇目標遠端並釐清確認文字
- 在同時具有 Azure DevOps 與 GitHub 遠端的儲存庫中，GitHub MCP 伺服器會保持啟用
- Markdown 表格中的內嵌程式碼冒號可正確渲染
- 在說明對話框按 Ctrl+C 現在可乾淨地關閉
- 外掛提供的 LSP 伺服器現在會被載入、啟動，並顯示於 /lsp show
- 在必填的 enum 欄位按 Enter 會選取反白的選項
- 隱藏干擾性的 todo 紀錄查詢，並在時間軸顯示相依性細節
- 在包含大量檔案的目錄中工作時，CLI 不再卡住數分鐘
- 新增 --output-format json 旗標，在 prompt 模式輸出 JSONL 以利程式化整合
- 新增 exitPlanMode.request 協定方法，支援 SDK 的計畫核准
- 背景 shell 指令與代理完成時會自動通知
- GitHub MCP 伺服器連線狀態會被正確追蹤並在狀態指示器中計數
- 按 Ctrl+R 以反向增量搜尋（如 Bash）搜尋指令歷史
- 較長的 diff 行在 diff 檢視中不再溢出，並會正確換行
- 新增啟動提示 hooks，可在會話開始時自動送出提示或斜線指令
- 游標在行尾時按 Ctrl+K 會合併行，符合標準 Emacs/終端機行為
- 跨輸入分塊拆分的逸出序列不再漏入文字輸入
- 將 `launch_messages` 設定改名為 `companyAnnouncements`
- 當終端機交由外部編輯器時會顯示等待訊息
- 設定檔支援 enabledPlugins，可在啟動時自動安裝外掛
- 改善反向歷史搜尋的鍵盤綁定：Ctrl+J 接受、Ctrl+G 取消
- 將儲存庫設定從 `.github/copilot/config.json` 更名為 `settings.json`
- 支援從 ssh:// URL 安裝外掛
- 每次會話結束後，會話使用度量（requests、tokens、code changes）會持久化到 events.jsonl

## 0.0.421 - 2026-03-03

- Autopilot 權限對話框改為在第一次提交提示時出現，而非在模式切換時
- AUTO 主題現在會讀取你的終端機 ANSI 色盤並直接使用，讓色彩符合你的終端機主題
- 使用 MCP Elicitations（實驗性）為 ask_user 工具新增結構化表單輸入
- Plugin 指令會從專案層級的 .claude/settings.json 讀取 extraKnownMarketplaces，以支援 Claude 相容性
- Git hooks 可透過 COPILOT_CLI=1 環境變數偵測 Copilot CLI 子程序，以略過互動式提示
- 在會話恢復或終端狀態切換期間，時間軸不再出現多餘的「write EIO」錯誤條目
- 以 Python 為基礎的 MCP 伺服器不再因 stdout 緩衝而逾時
- 當 --model 旗標指定不可用模型時會顯示錯誤
- MCP 伺服器可用性在登入、切換帳號或登出後會正確更新
- 在狀態列的分支名稱旁顯示可點擊的 PR 參考
- 新增 --plugin-dir 旗標，可從本機目錄載入外掛
- 滑鼠選取的文字會自動複製到 Linux 的主要選取緩衝區（中鍵貼上）
- 修正 VS Code 的 shift+enter 與 ctrl+enter 多行輸入快捷鍵
- 自動更新改用一致的 ~/.copilot/pkg 路徑，而非 XDG_STATE_HOME
- ACP 用戶端可透過會話設定選項調整推理強度
- 點擊終端機中的連結即可在預設瀏覽器開啟
- 透過 .github/copilot/config.json 支援儲存庫層級設定，可共用 marketplace 與啟動訊息等專案設定
- 在 alt-screen 模式下執行時，串流輸出不再被截斷
- Windows 上右鍵貼上不再產生亂碼
- Windows 上的 Shell 指令輸出不再在時間軸顯示為 "No changes detected"
- 使用 # 參考選擇器時，GitHub API 錯誤不再以原始 HTTP 訊息顯示在終端機
- Markdown 表格以正確的欄寬、文字換行與可配合終端寬度的 Unicode 邊框呈現
- MCP elicitation 表單會顯示更高的多行文字輸入欄位、在單欄位表單時隱藏分頁列，並修正欄位導覽時的錯誤閃爍

## 0.0.420 - 2026-02-27

- 自動更新現在也會更新二進位可執行檔，不僅是 JS 套件
- Plugin 與 marketplace 的 git 儲存庫在強制推送與以 tag 安裝後可正確更新
- 502 Bad Gateway 錯誤會自動重試，不再以原始 HTML 輸出導致會話當機
- 複製提示在 macOS 的 Ghostty 中顯示 cmd+c，並在所有終端機顯示右鍵作為替代方式
- 輸入 # 可引用 GitHub issues、pull requests 與 discussions

## 0.0.419 - 2026-02-27

- 新增 /chronicle 指令，提供 standup、tips 與 improve 子指令，並由會話歷史驅動（實驗性）
- 左右捲動不再觸發非預期的滑鼠按鍵按下
- 在 alt-screen 檢視中新增 Ctrl+F/Ctrl+B 作為 Page Down/Up 捲動快捷鍵
- 新增 --mouse/--no-mouse 旗標與 mouse 設定，可在 alt screen 停用滑鼠模式
- Home 與 End 鍵可跳到 alt-screen 捲動緩衝區的頂部與底部
- 新增 Ctrl+G 鍵盤快捷鍵，用於在外部編輯器編輯提示並關閉 UI 元素
- /mcp enable 可用於先前在設定前自動停用的內建伺服器
- 代理完成工作後 CLI 旋轉指示器會停止，且最終回應可見
- AUTO 主題現在使用終端機實際的 ANSI 色盤，在任何終端主題下色彩更精準
- MCP 伺服器在 command、args 或 cwd 欄位引用的 env 變數會自動加入伺服器環境
- 當尚未啟動任何會話時，/diagnose 會顯示有用的訊息
- MCP 伺服器名稱現在支援點號、斜線與 @ 字元，使 @modelcontextprotocol/server 與 io.github/server 這類 npm 風格名稱可用

## 0.0.418 - 2026-02-25

🎉 Copilot CLI 現已[正式推出](https://github.blog/changelog/2026-02-25-github-copilot-cli-is-now-generally-available) 🎉

- 代理已受保護，避免意外終止自身
- 移除 --disable-parallel-tools-execution 旗標與 parallel_tool_execution 設定選項
- 在 plugin.json 中以檔案路徑指定的外掛代理可正確載入

## 0.0.417 - 2026-02-25

- 新增 /research 指令，提供深度研究並可匯出報告
- MCP 伺服器在開啟新會話時不再間歇性載入失敗
- 安裝後外掛代理與技能無需重啟即可立即可用
- 外掛技能與指令可從 plugin.json 中宣告的自訂路徑載入
- Alt+backspace 現在會正確識別為 backspace 而非 delete

## 0.0.416 - 2026-02-24

- 擴充 `--help` 內容，加入描述、範例並排序旗標
- 當 Copilot MCP 政策不允許時，封鎖第三方 MCP 伺服器
- 串流回應大小計數器在工具呼叫與推理期間會持續更新，並在每次請求之間重設
- 狹窄終端機時狀態列會自動切換為雙行版面，讓 CWD、分支與模型資訊在任何寬度下都可讀
- Undo 操作現在一律需要確認

## 0.0.415 - 2026-02-23

- 以 UTF-8 BOM 儲存的技能檔（Windows 編輯器常見）現在可正確載入，不再因 frontmatter 解析錯誤而失敗
- 自訂代理支援 `model` 欄位用於指定模型；未知欄位現在只會警告，不再阻擋代理載入
- 計畫核准選單會顯示由模型整理的動作，並先高亮建議選項，其中包含可平行化工作的 autopilot+fleet
- 環境載入指示器在 MCP 啟動錯誤或恢復會話時不再無限卡住
- 新增 show_file 工具，用於向使用者呈現程式碼與差異
- 新增環境載入指示器，顯示技能、MCP、外掛等正在載入
- MCP 工具結果若為超長單行，會正確截斷
- `/plugin marketplace add` 與 `/plugin install` 支援包含空白的本機路徑
- `/mcp show` 會將伺服器分組為 User、Workspace、Plugins 與 Built-in 區段，並讓所有伺服器都可瀏覽
- 代理被詢問時，現在知道驅動自己的模型是哪一個
- Ctrl+A/E 會在換行後的視覺行之間循環；Home/End 在單一視覺行內移動；Ctrl+Home/End 跳至文字邊界

## 0.0.414 - 2026-02-21

- Explore agent 現在在可用時可使用 GitHub MCP 工具
- 在 autopilot 下接受計畫時會顯示權限提升對話框，以避免工具被自動拒絕的錯誤

## 0.0.413 - 2026-02-20

- 修正 Copilot API URL 未被套用的問題
- 在 gpt 模型中顯示 reasoning 的標題內容
- 將 LSP 請求逾時從 30s 提高到 90s，以降低逾時失敗
- 修正在工具呼叫完成時 alt-screen 時間軸條目不更新的問題（特別是子代理呼叫）
- 現在可在 alt-screen 檢視中使用 ctrl+insert 複製選取文字
- 修正 read_bash、write_bash 和 stop_bash 進行中圖示顯示實心點而非空心圓
- 在使用 `--experimental` 旗標執行時預設啟用 alt-screen 模式
- 改善大型儲存庫的程式碼搜尋速度
- alt-screen 模式下，會話資訊會在主檢視頁尾呈現
- allowed-tools 使用 YAML 陣列語法的技能檔案現在可正確載入
- marketplace.json 的 plugin 項目支援遠端來源（GitHub 儲存庫與 git URL）
- 啟動時會自動將使用者從 claude-sonnet-4.5 遷移到目前的預設模型
- Ctrl+A、Ctrl+E 與 Ctrl+U 會移動到邏輯行邊界（換行），而非視覺換行邊界
- 新增可設定的狀態列支援，可透過自訂 shell 腳本顯示動態會話資訊

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
