# UML 系統設計

Waterfall 的**設計階段**產出。依據 SRS v1.0（tag `srs-v1.0`，閘門 1 已簽核），兩人簽核**閘門 2** 後定版為 UML v1.0（tag `uml-v1.0`）。

## 圖表清單

| 圖 | 檔案 | 負責 | 狀態 |
| --- | --- | --- | --- |
| use case 圖 | [`usecase.md`](usecase.md) | 張晏碩 | ☑ |
| 太空站與危機類別圖 | [`class-station-crisis.md`](class-station-crisis.md) | 施家瑋 | ☑ |
| 殖民者與控制類別圖 | [`class-colonist-control.md`](class-colonist-control.md) | 張晏碩 | ☑ |
| 殖民者狀態圖 | [`state-colonist.md`](state-colonist.md) | 張晏碩 | ☑ |
| 危機觸發循序圖 | [`seq-crisis.md`](seq-crisis.md) | 施家瑋 | ☑ |
| 指令循序圖 | [`seq-command.md`](seq-command.md) | 張晏碩 | ☑ |
| 追溯表（需求 ↔ UML） | [`traceability.md`](traceability.md) | 施家瑋（B 的需求列由張晏碩檢查） | ☑ |

## 寫法約定

- 全部用 **Mermaid**，一張圖一個 `.md` 檔，GitHub 會直接顯示。
- 每個檔案依序寫：圖名、負責人、對應的需求編號 → ` ```mermaid ` 區塊 → 「設計說明」（只寫 SRS 沒寫、畫圖時才決定的事）。
- **類別名稱用英文**，中文寫在設計說明。兩人圖上都會出現的類別，名稱要一樣；對方負責的類別只畫名稱和關聯，不畫屬性。

| 類別 | 意思 | 主要在誰的圖 |
| --- | --- | --- |
| `Colonist` | 殖民者 | 張晏碩 |
| `TaskDispatcher` | 工作分派 | 張晏碩 |
| `Task` | 工作（含特殊自我照顧任務） | 張晏碩 |
| `Facility`（`ManualFacility`、`AutoFacility`、`FunctionFacility`） | 設施 | 施家瑋 |
| `Station` | 太空站（完整度、受損清單） | 施家瑋 |
| `SupplyStock` | 物資庫存（F／R／A） | 施家瑋 |
| `CrisisManager`、`Crisis` | 危機排程與事件 | 施家瑋 |
| `GameClock` | 天數與勝敗判定 | 施家瑋 |

- **use case 圖**：Mermaid 沒有 use case 圖，以 `flowchart` 模擬：參與者寫成 `P["👤 玩家"]`，使用案例用圓角節點 `([...])`，系統邊界用 `subgraph`。
- UML 只表達「有哪些類別、怎麼互動」，不決定 Godot 的 node、signal 或函式簽名；那些留到實作。
