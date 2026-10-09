# doc-governance（文件治理起手式）

用 git＋Claude Code 管理社團文件、研究計畫與自學筆記的最小治理架構，做成兩個 skill：

| Skill | 對 Claude 說 | 做什麼 |
|---|---|---|
| `setup` | 「建立治理架構」（不要打 `/init`） | 在目前資料夾下載範本：`CLAUDE.md`、`決策紀錄.md`、`治理擴增指南.md`、用途目錄與授權檔；已存在的檔案一律不覆寫 |
| `upgrade` | 「升級治理架構」 | 甲：比對範本最新版，列出你還沒有的新條文，逐項由你決定要不要加；乙：遇到具體問題時，依治理擴增指南擬條文，你同意才寫入，並記入決策紀錄 |

## 安裝

在 Claude Code 裡貼上這段話：

> 請幫我安裝 https://github.com/SynchronicEros/claude-code-mods-zh 裡的 doc-governance（照該 README「給協助安裝的 AI」一節），遇到問題幫我處理，裝好告訴我怎麼讓它生效。

要更新時說「請幫我把 doc-governance 更新到最新版」。

<details>
<summary>給協助安裝的 AI</summary>

- 需要 Claude Code（付費方案）；只有 Codex 的使用者無法安裝。
- 安裝（user scope，在終端機或 Bash 工具執行）：`claude plugin marketplace add SynchronicEros/claude-code-mods-zh`，再 `claude plugin install doc-governance@claude-code-mods-zh`。
- 更新：`claude plugin marketplace update claude-code-mods-zh`，再 `claude plugin update doc-governance@claude-code-mods-zh`；顯示 already at the latest version 即為最新。
- 一律保留總目錄那份；若同時裝了 `doc-governance@claude-code-doc-governance-zh`，執行 `claude plugin uninstall doc-governance@claude-code-doc-governance-zh`。
- 安裝或更新後須開新的 session 才生效（終端機版 `/exit` 後重打 `claude`；桌面版開新對話）。桌面版 Code 分頁不能用 `/plugin` 指令。
- Windows 上 skill 的指令需要 Git Bash（隨 Git for Windows 安裝）。
- 0.1.3 起 skill `init` 改名為 `setup`（`/doc-governance:setup`），不要與內建 `/init` 混淆。

</details>

## 使用

在要建立治理架構的新資料夾裡開 Claude Code，對 Claude 說「建立治理架構」；之後要比對範本更新或擴增規範，說「升級治理架構」。

## 範本從哪裡來

範本內容的正本是公開範本 repo [eros-kmu-learning-example](https://github.com/SynchronicEros/eros-kmu-learning-example)。兩個 skill 都在執行當下用 `curl` 下載最新版，不在 plugin 裡另存一份，所以範本更新後不必更新 plugin，執行 `upgrade` 就比對得到。

多數人直接照範本 repo README 的「快速開始」，請 Claude 或 Codex 協助按「Use this template」建立自己的 private repo 即可，不必裝本 plugin。

## 授權

- plugin（兩個 skill 的步驟說明）：MIT（見 [LICENSE](LICENSE)）。
- 下載到你資料夾的範本內容：依範本 repo 的 **CC BY 4.0**，作者 eros_tsung_pao_lin；`LICENSE` 與 README〈授權與致謝〉一節請保留。

---

**English:** Two skills for a minimal document-governance starter kit (git + Claude Code) aimed at student clubs, research projects and study notes. `setup` (say 「建立治理架構」 or type `/doc-governance:setup`; not the built-in `/init`) downloads the template (CLAUDE.md, decision log, expansion guide, folders, license) into the current folder without overwriting anything; `upgrade` compares your files with the latest template and lists only what you do not yet have, or drafts new rules from the expansion guide when you hit a concrete problem. Template content lives in [eros-kmu-learning-example](https://github.com/SynchronicEros/eros-kmu-learning-example) (CC BY 4.0) and is fetched with `curl` at run time; the plugin itself is MIT.

**Install / License (English):** Requires Claude Code (a paid plan). Ask Claude Code to install `doc-governance` from https://github.com/SynchronicEros/claude-code-mods-zh, or run `claude plugin marketplace add SynchronicEros/claude-code-mods-zh`, then `claude plugin install doc-governance@claude-code-mods-zh`; takes effect in new sessions. MIT.
