# doc-governance（文件治理起手式）

用 git＋Claude Code 管理社團文件、研究計畫與自學筆記的最小治理架構，做成兩個 skill：

| Skill | 對 Claude 說 | 做什麼 |
|---|---|---|
| `setup` | 「建立治理架構」（不要打 `/init`） | 在目前資料夾下載範本：`CLAUDE.md`、`決策紀錄.md`、`治理擴增指南.md`、用途目錄與授權檔；已存在的檔案一律不覆寫 |
| `upgrade` | 「升級治理架構」 | 甲：比對範本最新版，列出你還沒有的新條文，逐項由你決定要不要加；乙：遇到具體問題時，依治理擴增指南擬條文，你同意才寫入，並記入決策紀錄 |

## 安裝

**需要 Claude Code（付費方案）；Codex 免費版不能安裝。** 還沒裝 Claude Code，見[官方安裝說明](https://code.claude.com/docs/zh-TW/setup)。

須能連上 GitHub，並有 `curl`（macOS 內建）。

Windows 需要 Git Bash：安裝 [Git for Windows](https://git-scm.com/downloads/win) 就有（選項都用預設即可），裝完重開 Claude Code。

下面兩行指令貼在**終端機**（Mac：「終端機」App；Windows：PowerShell），貼上後按 Enter；不是貼在 Claude Code 的對話框。已經在 Claude Code 對話框裡的話，改打 `/plugin marketplace add …` 與 `/plugin install …`（去掉開頭的 `claude`，改成斜線）。

```bash
claude plugin marketplace add SynchronicEros/claude-code-doc-governance-zh
```

```bash
claude plugin install doc-governance@claude-code-doc-governance-zh
```

安裝時若出現英文訊息「SSH not configured, cloning via HTTPS」或「userConfig options not yet set」，可以忽略（沒設定就用預設值）。

裝好後要**開新的 session（一次新對話）**才會生效：終端機版先打 `/exit` 離開，再打 `claude`；桌面版開一個新對話。

**總目錄與單一 repo 二擇一**：同一個 Mod 或 skill 只從一處安裝（skill 兩處都裝會出現兩份）。用 `claude plugin list` 檢查；若同時看到 `doc-governance@claude-code-doc-governance-zh` 與 `doc-governance@claude-code-mods-zh`，移除其中一份：

```bash
claude plugin uninstall doc-governance@claude-code-mods-zh
```

全部 Mod 與 skill 見總目錄 [claude-code-mods-zh](https://github.com/SynchronicEros/claude-code-mods-zh)。

**怎麼叫出來**：直接對 Claude 說「建立治理架構」，或打 `/doc-governance:setup`。（別跟 Claude Code 內建的 `/init` 搞混：那個指令會依資料夾裡的程式碼另寫一份 `CLAUDE.md`，不是本範本。）升級同理，說「升級治理架構」或打 `/doc-governance:upgrade`。

## 範本從哪裡來

範本內容的正本是公開範本 repo [eros-kmu-learning-example](https://github.com/SynchronicEros/eros-kmu-learning-example)。兩個 skill 都在執行當下用 `curl` 下載最新版，不在 plugin 裡另存一份，所以範本更新後不必更新 plugin，執行 `upgrade` 就比對得到。

也可以不裝 plugin，直接在範本 repo 按「Use this template」建立自己的 repo（建議設為 private）。

## 需求

- 能連上 GitHub（`raw.githubusercontent.com`）。
- 系統有 `curl`（macOS 內建；Windows 上的 Claude Code 需要 Git Bash，安裝 [Git for Windows](https://git-scm.com/downloads/win) 就有，已附 curl）。

## 授權

- plugin（兩個 skill 的步驟說明）：MIT（見 [LICENSE](LICENSE)）。
- 下載到你資料夾的範本內容：依範本 repo 的 **CC BY 4.0**，作者 eros_tsung_pao_lin；`LICENSE` 與 README〈授權與致謝〉一節請保留。

---

**English:** Two skills for a minimal document-governance starter kit (git + Claude Code) aimed at student clubs, research projects and study notes. `setup` (say 「建立治理架構」 or type `/doc-governance:setup`; not the built-in `/init`) downloads the template (CLAUDE.md, decision log, expansion guide, folders, license) into the current folder without overwriting anything; `upgrade` compares your files with the latest template and lists only what you do not yet have, or drafts new rules from the expansion guide when you hit a concrete problem. Template content lives in [eros-kmu-learning-example](https://github.com/SynchronicEros/eros-kmu-learning-example) (CC BY 4.0) and is fetched with `curl` at run time; the plugin itself is MIT.

**Install / License (English):** Requires Claude Code (a paid plan); the free Codex tier cannot install it. Needs GitHub access and curl (on Windows, Git Bash from Git for Windows). `claude plugin marketplace add SynchronicEros/claude-code-doc-governance-zh`, then `claude plugin install doc-governance@claude-code-doc-governance-zh`; takes effect in new sessions. Install from either this repo or the index, not both. All mods and skills: [claude-code-mods-zh](https://github.com/SynchronicEros/claude-code-mods-zh). MIT.
