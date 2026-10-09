---
name: init
description: 在目前資料夾建立「文件治理起手式」：從公開範本下載 CLAUDE.md、決策紀錄、用途目錄與授權檔。使用者說「建立治理架構」「套用文件治理起手式」「初始化治理」時使用。
---

# init：建立文件治理起手式

範本正本在公開 repo `SynchronicEros/eros-kmu-learning-example`（CC BY 4.0）。本 skill 不內建範本內容，一律在執行當下下載最新版。

## 一、動手前（一律先做，只讀）

1. 說明目前資料夾的絕對路徑，請使用者確認就是要建立治理架構的地方。
2. 檢查以下檔案是否已存在：`CLAUDE.md`、`決策紀錄.md`、`治理擴增指南.md`、`README.md`、`LICENSE`、`社團文件/`、`研究計畫/`、`自學筆記/`。
   - **任何一項已存在就停下來**，列出衝突項目，請使用者選擇：(甲) 換一個空資料夾；(乙) 只建立不存在的項目、已存在者一律不動。**不得覆寫既有檔案。**
3. 問使用者要哪些用途目錄（可複選）：`社團文件/`、`研究計畫/`、`自學筆記/`。
4. 列出將建立的檔案清單，等使用者說「開始」才下載。

## 二、下載

範本網址前綴（中文路徑已編碼，Windows 的 Git Bash 也能用）：

```bash
B=https://raw.githubusercontent.com/SynchronicEros/eros-kmu-learning-example/main
```

| 檔案 | 網址後段 |
|---|---|
| `CLAUDE.md` | `CLAUDE.md` |
| `決策紀錄.md` | `%E6%B1%BA%E7%AD%96%E7%B4%80%E9%8C%84.md` |
| `治理擴增指南.md` | `%E6%B2%BB%E7%90%86%E6%93%B4%E5%A2%9E%E6%8C%87%E5%8D%97.md` |
| `README.md` | `README.md` |
| `LICENSE` | `LICENSE` |
| `社團文件/README.md` | `%E7%A4%BE%E5%9C%98%E6%96%87%E4%BB%B6/README.md` |
| `研究計畫/README.md` | `%E7%A0%94%E7%A9%B6%E8%A8%88%E7%95%AB/README.md` |
| `自學筆記/README.md` | `%E8%87%AA%E5%AD%B8%E7%AD%86%E8%A8%98/README.md` |

用途目錄的 `README.md` 只下載使用者在第一節第 3 步選的那幾個；其餘 5 個檔案一律下載。

每個檔案用 `curl -fsSL "$B/<網址後段>" -o "<檔案>"` 下載（用途目錄先 `mkdir -p`）。**一律用 curl 原樣下載，不要用網頁讀取工具，也不要自己改寫或摘要內容。**任何一個下載失敗就停下來回報，不要用記憶補寫。

## 三、下載後

1. 若使用者沒選全部三個用途目錄：把 `CLAUDE.md`「目錄結構」表與 `README.md`「目錄結構」表中沒建立的列刪掉，並告知使用者兩個檔各改了哪幾列。兩檔其餘內容一律不動。
2. `LICENSE` 與 `README.md` 的〈授權與致謝〉一節是範本的授權標示，保留原樣；README 其他段落可由使用者日後自行改寫。
3. 若此資料夾還不是 git repo，詢問是否執行 `git init`；同意才執行。提醒：要放上 GitHub 時請建 **private** repo，社團與研究文件不適合公開。
4. 回報：實際建立了哪些檔案、哪些因已存在而略過、`CLAUDE.md` 與 `README.md` 各改了哪幾列。
5. 告訴使用者下一步：先讀 `CLAUDE.md`；在 `決策紀錄.md` 從 D2 開始寫自己的決定；架構不夠用時說「升級治理架構」（`upgrade` skill）。

## 不做的事

- 不覆寫、不刪除任何既有檔案。
- 不自行 commit 或 push。
- 不建立公開 repo。
