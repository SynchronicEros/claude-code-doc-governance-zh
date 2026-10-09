# doc-governance（文件治理起手式）

用 git＋Claude Code 管理社團文件、研究計畫與自學筆記的最小治理架構，做成兩個 skill：

| Skill | 對 Claude 說 | 做什麼 |
|---|---|---|
| `setup` | 「建立治理架構」（不要打 `/init`） | 在目前資料夾下載範本：`CLAUDE.md`、`決策紀錄.md`、`治理擴增指南.md`、用途目錄與授權檔；已存在的檔案一律不覆寫 |
| `upgrade` | 「升級治理架構」 | 甲：比對範本最新版，列出你還沒有的新條文，逐項由你決定要不要加；乙：遇到具體問題時，依治理擴增指南擬條文，你同意才寫入，並記入決策紀錄 |

## 安裝

- 需要 **Claude Code（付費方案）**；Codex 免費版不能安裝（只有 Codex 的人，改照[範本 repo 的「只用 Codex 的人」](https://github.com/SynchronicEros/eros-kmu-learning-example#只用-codex不用-claude-code的人)）。
- 還沒裝 Claude Code：見[官方安裝說明](https://code.claude.com/docs/zh-TW/setup)。
- 須能連上 GitHub，並有 `curl`（macOS 內建）。
- Mac 第一次安裝可能跳出安裝「命令列開發者工具」的視窗：按「安裝」，裝完再重跑一次指令。
- Windows 需要 Git Bash：安裝 [Git for Windows](https://git-scm.com/downloads/win) 就有（選項都用預設即可），裝完重開 Claude Code。

**指令貼在哪裡**：貼在**終端機**，貼上後按 Enter（Mac：按 ⌘＋空白鍵開 Spotlight，搜尋「終端機」；Windows：在開始選單搜尋「PowerShell」）。不是貼在 Claude Code 的對話框。若終端機回應 `command not found`（找不到指令），表示終端機裡還沒有 Claude Code：照上面的官方安裝說明安裝；只用桌面版的人，改用下方「對話框裡」的寫法。

```bash
claude plugin marketplace add SynchronicEros/claude-code-doc-governance-zh
```

```bash
claude plugin install doc-governance@claude-code-doc-governance-zh
```

**對話框裡**（已經在 Claude Code 裡，或只用桌面版）：改打 `/plugin marketplace add SynchronicEros/claude-code-doc-governance-zh`，再打 `/plugin install doc-governance@claude-code-doc-governance-zh`；會跳出英文選單，選第一個 **Install for you (user scope)**。

安裝時若出現英文訊息「SSH not configured, cloning via HTTPS」或「userConfig options not yet set」，可以忽略（沒設定就用預設值）。

裝好後要**開新的 session（一次新對話）**才會生效：終端機版先打 `/exit` 離開，再打 `claude`；桌面版開一個新對話。

**總目錄與本 repo 二擇一**：同一個 Mod 或 skill 只從一處安裝（skill 兩處都裝會出現兩份）。用 `claude plugin list` 檢查；若同時看到 `doc-governance@claude-code-doc-governance-zh` 與 `doc-governance@claude-code-mods-zh`，**保留總目錄那份**，移除本 repo 這份（只執行一次）：

```bash
claude plugin uninstall doc-governance@claude-code-doc-governance-zh
```

再用 `claude plugin list` 確認只剩一份。重複執行，或對沒裝的東西執行時，出現 ✘ 與「not installed」或「already disabled」都無害。對話框裡：打 `/plugin`、按 Tab 切到 Installed 分頁檢查，打 `/plugin uninstall` 開啟面板移除。桌面版：按輸入框旁的「＋」→ Plugins → Manage plugins，可停用或移除。

## 更新

有新版時，在終端機執行兩行，再開新的 session。從本 repo 裝的：

```bash
claude plugin marketplace update claude-code-doc-governance-zh
```

```bash
claude plugin update doc-governance@claude-code-doc-governance-zh
```

從總目錄裝的：

```bash
claude plugin marketplace update claude-code-mods-zh
```

```bash
claude plugin update doc-governance@claude-code-mods-zh
```

看到「already at the latest version」就代表已是最新版。對話框裡：先打 `/plugin marketplace update <上面的來源名稱>`，再打 `/plugin`、按 Tab 切到 Installed 分頁，選這個 plugin → Update now。桌面版的更新方式官方文件沒有說明，找不到的話請改用終端機。

0.1.3 起 skill `init` 改名為 `setup`：更新後改打 `/doc-governance:setup`，或照舊說「建立治理架構」。

全部 Mod 與 skill 見總目錄 [claude-code-mods-zh](https://github.com/SynchronicEros/claude-code-mods-zh)。

## 使用

先建一個新資料夾，在裡面開 Claude Code（不要在家目錄或桌面直接跑）。終端機版依序執行：

```bash
mkdir ~/我的治理
```

```bash
cd ~/我的治理
```

```bash
claude
```

桌面版則開新對話時選擇該資料夾。接著對 Claude 說「建立治理架構」，或打 `/doc-governance:setup`。（別跟 Claude Code 內建的 `/init` 搞混：那個指令會依資料夾裡的程式碼另寫一份 `CLAUDE.md`，不是本範本。）升級同理，說「升級治理架構」或打 `/doc-governance:upgrade`。

## 範本從哪裡來

範本內容的正本是公開範本 repo [eros-kmu-learning-example](https://github.com/SynchronicEros/eros-kmu-learning-example)。兩個 skill 都在執行當下用 `curl` 下載最新版，不在 plugin 裡另存一份，所以範本更新後不必更新 plugin，執行 `upgrade` 就比對得到。

也可以不裝 plugin，直接在範本 repo 按「Use this template」建立自己的 repo（建議設為 private）；只有 Codex 的人也走這條路，見範本 README「只用 Codex 的人」一節。

## 授權

- plugin（兩個 skill 的步驟說明）：MIT（見 [LICENSE](LICENSE)）。
- 下載到你資料夾的範本內容：依範本 repo 的 **CC BY 4.0**，作者 eros_tsung_pao_lin；`LICENSE` 與 README〈授權與致謝〉一節請保留。

---

**English:** Two skills for a minimal document-governance starter kit (git + Claude Code) aimed at student clubs, research projects and study notes. `setup` (say 「建立治理架構」 or type `/doc-governance:setup`; not the built-in `/init`) downloads the template (CLAUDE.md, decision log, expansion guide, folders, license) into the current folder without overwriting anything; `upgrade` compares your files with the latest template and lists only what you do not yet have, or drafts new rules from the expansion guide when you hit a concrete problem. Template content lives in [eros-kmu-learning-example](https://github.com/SynchronicEros/eros-kmu-learning-example) (CC BY 4.0) and is fetched with `curl` at run time; the plugin itself is MIT.

**Install / License (English):** Requires Claude Code (a paid plan); the free Codex tier cannot install it. Needs GitHub access and curl (on Windows, Git Bash from Git for Windows). `claude plugin marketplace add SynchronicEros/claude-code-doc-governance-zh`, then `claude plugin install doc-governance@claude-code-doc-governance-zh`; takes effect in new sessions. Install from either this repo or the index, not both (keep the index copy). To update, run `claude plugin marketplace update <source>`, then `claude plugin update <name>@<source>`. All mods and skills: [claude-code-mods-zh](https://github.com/SynchronicEros/claude-code-mods-zh). MIT.
