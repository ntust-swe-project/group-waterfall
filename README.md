# group-waterfall

期中專題 — **Waterfall + AI 組**。

## 共同輸入

共同輸入與共用規則在 [`project-common`](https://github.com/ntust-swe-project/project-common)：

| 檔案 | 說明 |
| --- | --- |
| `docs/VISION.md` | 起始文件。三組唯一的共同輸入 |
| `docs/COMMIT_CONVENTION.md` | commit message 規則，四個 repo 共用 |

## 本 repo

放本組的產出：需求分析、設計文件、UML、會議與客戶訪談紀錄、AI 使用紀錄，以及 prototype 程式碼。

| 檔案／目錄 | 說明 |
| --- | --- |
| `docs/PLAN.md` | 分工、排程、閘門與 PR 一覽 |
| `docs/req/SRS.md` | 軟體需求規格（SRS），閘門 1 簽核，tag `srs-v1.0` |
| `docs/uml/` | UML 系統設計與追溯表（Mermaid），閘門 2 簽核，tag `uml-v1.0` |
| `docs/meeting/` | 客戶訪談紀錄與訪談範本 |
| `docs/ai-log/` | AI 使用紀錄（`AI_LOG.md`），以及訪談題目的 AI 草稿 |
| `docs/TIMESHEET.md` | 工時紀錄 |
| `docs/COMMIT_CONVENTION.md` | commit 規則：共用規則的副本與本組自訂的 scope |
| `docs/report/` | 期中報告草稿（`docs/report-a` 分支） |
| `project.godot` | Godot 專案設定（三組共用的骨架） |

## 規則重點

- **不要**在本 repo 另存 `VISION.md` 副本。起始文件只有 `project-common` 那一份，定案後要改須經三組同意。
- 交付物為 **prototype 與相關文件**；prototype 完成即視為本組完成。
- 完成前不讀取其他組的 repo。
- 引擎與 AI 工具的版本見 `project-common` 的 `docs/VISION.md` 第 10 節，三組必須一致。

## 開始前

```bash
git config commit.template .gitmessage
```
