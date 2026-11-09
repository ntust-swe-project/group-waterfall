# Commit Message 規則 — group-waterfall

共用規則以 [`project-common/docs/COMMIT_CONVENTION.md`](https://github.com/ntust-swe-project/project-common/blob/main/docs/COMMIT_CONVENTION.md) 為準，三個 repo 一致。本檔是本組的副本，並另外記錄**本組自訂的程式碼 scope**（共用規則要求記在各組自己 repo 的這份文件裡）。共用版有更新時，以共用版為準、同步回本檔。

格式採 [Conventional Commits](https://www.conventionalcommits.org/)。

## 格式

```
<type>(<scope>): <subject>

* <body bullet>
* <body bullet>

<footer>
```

- **第一行**：`type(scope): subject`，不超過 72 字元
- **空一行**
- **body**：用 `*` 開頭的條列，一條講一件事
- **footer**：選用，見下方

## type

| type | 用在 |
| --- | --- |
| `feat` | 新增功能（遊戲機制、系統、工具） |
| `fix` | 修 bug |
| `docs` | 文件（需求、UML、會議紀錄、報告） |
| `refactor` | 重構，行為不變 |
| `test` | 測試 |
| `chore` | 雜事（依賴、設定、檔案搬移） |
| `build` | 建置流程、Godot 專案設定、匯出設定 |

只有文件變動就用 `docs`，不要用 `feat`。需求規格、設計文件、UML 都算 `docs`。

## scope

一個 repo 就是一組，所以 scope **不標組別**，標的是「動到專案的哪一塊」。

**共用（三個 repo 一致，不可自行增改）**

| scope | 範圍 |
| --- | --- |
| `vision` | 起始文件（`VISION.md`，在 `project-common`） |
| `req` | 需求分析產出（需求規格、use case） |
| `uml` | UML 圖 |
| `meeting` | 會議紀錄、客戶訪談紀錄 |
| `ai-log` | AI 使用紀錄 |
| `repo` | repo 結構、README、`.gitignore`、CI |

**本組自訂（程式碼）**

設計階段定案後在這裡補上。新增 scope 時先加到這張表，再開始用。

| scope | 範圍 |
| --- | --- |
| （待設計階段決定） | |

## subject

- 英文、祈使句、小寫開頭：`add`、`update`、`remove`、`fix`
- 句尾不加句號
- 寫「做了什麼」，不寫「改了哪個檔案」

```
✅ docs(req): add functional requirements for crisis waves
❌ docs(req): SRS 改了一下
❌ docs(req): updated SRS.md.
```

## body

- 每條 bullet 以動詞開頭，一條一件事
- 可用中文（這是給組員和助教看的），但同一個 commit 內不要中英混寫
- 「為什麼這樣改」比「改了什麼」重要，尤其是推翻先前決定時

## footer

**修改起始文件**

`VISION.md` 只有一份，放在 `project-common`。定案後若要修改，依文件第 11 節需三組同意，commit 推到 `project-common`，**不要在本 repo 另存副本修改**。格式見共用版。

**AI 參與**

課程要求記錄 AI 使用。若這個 commit 的內容主要由 AI 產生或大幅協助，加上實際使用的模型：

```
Co-Authored-By: Claude Opus 5.5 <noreply@anthropic.com>
```

模型若有更換，這裡和 `docs/ai-log/AI_LOG.md` 第 1 節要一起更新。commit 層面的紀錄不取代 `docs/ai-log/`，只是讓歷史對得起來。

## 範例

```
docs(uml): add use case diagram for crisis response

* add actors, use cases, and relations for wave handling
* 依 11/07 客戶訪談紀錄調整，原本漏掉通訊中斷的情境
```

```
docs(ai-log): add AI usage log

* add tool disclosure for Claude Code and Claude Opus 5.5
* add first usage entries for repo setup

Co-Authored-By: Claude Opus 5.5 <noreply@anthropic.com>
```

## commit 範本

每個人在 repo 內跑一次，`git commit` 就會帶出格式提示：

```bash
git config commit.template .gitmessage
```
