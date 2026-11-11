# 追溯表（需求 ↔ UML）

- **負責人**：施家瑋（A）；張晏碩負責的需求（`FR-COL`、`FR-CTL`、`UI`、`IF-01`、`02`、`04`）由張晏碩填寫、檢查
- **依據**：SRS v1.0（tag `srs-v1.0`）
- 用途：確認每條需求都有對應的設計，也確認設計裡沒有 SRS 沒要求的東西。

## A 負責的需求

| 需求 | 對應的 UML 元素 | 圖 |
| --- | --- | --- |
| `FR-CORE-01` | GameClock.day、tick() | [`class-station-crisis`](class-station-crisis.md) |
| `FR-CORE-02` | GameClock.secondsInDay、tick() | [`class-station-crisis`](class-station-crisis.md) |
| `FR-CORE-03` | GameClock.day → 使用者介面（IF-06） | [`class-station-crisis`](class-station-crisis.md) |
| `FR-CORE-04` | IF-06 不提供剩餘時間 | [`class-station-crisis`](class-station-crisis.md) |
| `FR-CORE-05` | GameClock.endGame(WON) | [`class-station-crisis`](class-station-crisis.md) |
| `FR-CORE-06` | GameClock.checkFailure() 每一幀執行 | [`class-station-crisis`](class-station-crisis.md)、[`seq-crisis`](seq-crisis.md) |
| `FR-CORE-07` | FailReason（只有 3 個值） | [`class-station-crisis`](class-station-crisis.md) |
| `FR-CORE-08` | GameClock.checkFailure() ← Station.integrity | [`class-station-crisis`](class-station-crisis.md)、[`seq-crisis`](seq-crisis.md) |
| `FR-CORE-09` | GameClock.commDownSeconds ← Station.isCommDown() | [`class-station-crisis`](class-station-crisis.md)、[`seq-crisis`](seq-crisis.md) |
| `FR-CORE-10` | GameClock.checkFailure() ← Colonist 存活人數（IF-08） | [`class-station-crisis`](class-station-crisis.md)、[`seq-crisis`](seq-crisis.md) |
| `FR-CORE-11` | GameClock ..> Settlement | [`class-station-crisis`](class-station-crisis.md) |
| `FR-CORE-12` | Settlement.dayReached、GameClock.failReason | [`class-station-crisis`](class-station-crisis.md) |
| `FR-CORE-13` | Settlement 的 4 項指標 | [`class-station-crisis`](class-station-crisis.md) |
| `FR-CORE-14` | Settlement.computeScore()、daysSurvived | [`class-station-crisis`](class-station-crisis.md) |
| `FR-CORE-15` | 使用者介面（張晏碩 UI-07）→ GameClock 重新開局 | （實作） |
| `FR-STN-01` | Station（單一地圖）、Facility.position | [`class-station-crisis`](class-station-crisis.md) |
| `FR-STN-02` | Station.requestBuild() → TaskDispatcher（IF-03） | [`class-station-crisis`](class-station-crisis.md) |
| `FR-STN-03` | FacilitySpec.buildCost、SupplyStock.available() | [`class-station-crisis`](class-station-crisis.md) |
| `FR-STN-04` | Facility 子類別、FacilityCategory | [`class-station-crisis`](class-station-crisis.md) |
| `FR-STN-05` | ManualFacility.operator（0..1）、isAssignable() | [`class-station-crisis`](class-station-crisis.md) |
| `FR-STN-06` | ManualFacility.produce()：沒有操作者時為 0 | [`class-station-crisis`](class-station-crisis.md) |
| `FR-STN-07` | AutoFacility.produce() | [`class-station-crisis`](class-station-crisis.md) |
| `FR-STN-08` | FacilitySpec（人工農田、自動化農田、通訊設施） | [`class-station-crisis`](class-station-crisis.md) |
| `FR-STN-09` | ManualFacility.produce()、AutoFacility.produce() | [`class-station-crisis`](class-station-crisis.md) |
| `FR-STN-10` | FacilitySpec.buildCost、outputPerDay | [`class-station-crisis`](class-station-crisis.md) |
| `FR-STN-11` | FacilitySpec.buildCost | [`class-station-crisis`](class-station-crisis.md) |
| `FR-STN-12` | Station.integrity | [`class-station-crisis`](class-station-crisis.md) |
| `FR-STN-13` | Station.computeIntegrity()（公式見類別圖設計說明） | [`class-station-crisis`](class-station-crisis.md)、[`seq-crisis`](seq-crisis.md) |
| `FR-STN-14` | Station.getDamagedFacilities() → 使用者介面（IF-05） | [`class-station-crisis`](class-station-crisis.md) |
| `FR-STN-15` | Facility.isOperating()（damage < 100） | [`class-station-crisis`](class-station-crisis.md) |
| `FR-STN-16` | Station.onFacilityDamaged() → TaskDispatcher；Facility.repair() | [`class-station-crisis`](class-station-crisis.md)、[`seq-crisis`](seq-crisis.md) |
| `FR-STN-17` | Station.dailyDecay()、Facility.neighbors() | [`class-station-crisis`](class-station-crisis.md)、[`seq-crisis`](seq-crisis.md) |
| `FR-STN-18` | Crisis.severity（換算在實作時確保上限） | [`class-station-crisis`](class-station-crisis.md) |
| `FR-STN-19` | FunctionFacility（開局建立） | [`class-station-crisis`](class-station-crisis.md) |
| `FR-STN-20` | Station.isCommDown() | [`class-station-crisis`](class-station-crisis.md) |
| `FR-STN-21` | SupplyStock.total 初值、Station 開局設施 | [`class-station-crisis`](class-station-crisis.md) |
| `FR-STN-22` | SupplyStock.reserve()、release()、consume() | [`class-station-crisis`](class-station-crisis.md) |
| `FR-STN-23` | Station.onFacilityDamaged()（不重複建立） | [`class-station-crisis`](class-station-crisis.md)、[`seq-crisis`](seq-crisis.md) |
| `FR-STN-24` | Station *-- SupplyStock（唯一一份） | [`class-station-crisis`](class-station-crisis.md) |
| `FR-CRI-01` | CrisisManager.scheduleWave()、Wave *-- 1..* Crisis | [`class-station-crisis`](class-station-crisis.md)、[`seq-crisis`](seq-crisis.md) |
| `FR-CRI-02` | Wave.triggerSecond（由 seed 決定） | [`class-station-crisis`](class-station-crisis.md)、[`seq-crisis`](seq-crisis.md) |
| `FR-CRI-03` | 觸發前不通知使用者介面 | [`seq-crisis`](seq-crisis.md) |
| `FR-CRI-04` | CrisisManager.baseIntensity(day) | [`class-station-crisis`](class-station-crisis.md)、[`seq-crisis`](seq-crisis.md) |
| `FR-CRI-05` | Crisis 的 4 個子類別 | [`class-station-crisis`](class-station-crisis.md) |
| `FR-CRI-06` | MeteorStrike ..> Facility | [`class-station-crisis`](class-station-crisis.md)、[`seq-crisis`](seq-crisis.md) |
| `FR-CRI-07` | CommInterference ..> FunctionFacility | [`class-station-crisis`](class-station-crisis.md)、[`seq-crisis`](seq-crisis.md) |
| `FR-CRI-08` | EquipmentFailure ..> Facility | [`class-station-crisis`](class-station-crisis.md)、[`seq-crisis`](seq-crisis.md) |
| `FR-CRI-09` | ColonistDeterioration.level、durationSeconds ..> Colonist（IF-07） | [`class-station-crisis`](class-station-crisis.md)、[`seq-crisis`](seq-crisis.md) |
| `FR-CRI-10` | CrisisManager.coefficient、evaluateDevelopment() | [`class-station-crisis`](class-station-crisis.md)、[`seq-crisis`](seq-crisis.md) |
| `FR-CRI-11` | DevelopmentMetrics | [`class-station-crisis`](class-station-crisis.md)、[`seq-crisis`](seq-crisis.md) |
| `FR-CRI-12` | evaluateDevelopment()：限制在 0.7～1.3 | [`seq-crisis`](seq-crisis.md) |
| `FR-CRI-13` | evaluateDevelopment()：每天最多變 0.1 | [`seq-crisis`](seq-crisis.md) |
| `FR-CRI-14` | writeDebugLog() 只寫檔；UI-11 不含係數 | [`class-station-crisis`](class-station-crisis.md)、[`seq-crisis`](seq-crisis.md) |
| `IF-03` | Station ..> TaskDispatcher、TaskDispatcher ..> SupplyStock | [`class-station-crisis`](class-station-crisis.md)、[`seq-crisis`](seq-crisis.md) |
| `IF-05` | Station → 使用者介面 | [`class-station-crisis`](class-station-crisis.md) |
| `IF-06` | GameClock、Settlement → 使用者介面 | [`class-station-crisis`](class-station-crisis.md) |
| `IF-07` | ColonistDeterioration ..> Colonist | [`class-station-crisis`](class-station-crisis.md)、[`seq-crisis`](seq-crisis.md) |
| `IF-08` | GameClock、CrisisManager 讀取 Station、Colonist | [`class-station-crisis`](class-station-crisis.md)、[`seq-crisis`](seq-crisis.md) |
| `NFR-07` | FacilitySpec（數值集中在設定） | [`class-station-crisis`](class-station-crisis.md) |
| `NFR-08` | CrisisManager.seed | [`class-station-crisis`](class-station-crisis.md)、[`seq-crisis`](seq-crisis.md) |
| `NFR-09` | CrisisManager.writeDebugLog() | [`class-station-crisis`](class-station-crisis.md)、[`seq-crisis`](seq-crisis.md) |

## B 負責的需求

| 需求 | 對應的 UML 元素 | 圖 |
| --- | --- | --- |
| `FR-COL-01`～`FR-COL-28` | 【待張晏碩填】Colonist 的屬性與狀態 | `class-colonist-control.md`、`state-colonist.md` |
| `FR-CTL-01`～`FR-CTL-14` | 【待張晏碩填】TaskDispatcher、Task | `class-colonist-control.md`、`seq-command.md` |
| `UI-01`～`UI-11` | 【待張晏碩填】 | `usecase.md` |
| `IF-01`、`IF-02`、`IF-04` | 【待張晏碩填】 | `class-colonist-control.md` |

## 不在 UML 範圍的需求

| 需求 | 原因 |
| --- | --- |
| `NFR-01`～`NFR-06`、`NFR-10` | 效能、可用性、可攜性與試玩驗證，屬於實作與測試階段，類別圖和循序圖無法表達 |
| `FR-CORE-15` | 「從結算畫面開新局」是介面操作，類別圖只表示 `GameClock` 可以重新開始；實際流程在實作時處理 |

## 檢查結果

- A 負責的 `FR-CORE`、`FR-STN`、`FR-CRI` 共 53 條需求，都至少對應到一個 UML 元素。
- A 的兩張圖沒有出現 SRS 沒要求的功能；圖上的設計決定（例如設施分類用繼承、換日時先算連鎖損壞）都寫在各圖的「設計說明」。
