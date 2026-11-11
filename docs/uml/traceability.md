# 追溯表（需求 ↔ UML）

- **負責人**：施家瑋（A）；張晏碩負責的需求（`FR-COL`、`FR-CTL`、`UI`、`IF-01`、`02`、`04`）由施家瑋依張晏碩各圖開頭的「對應需求」整理，**待張晏碩在 PR #7 檢查**
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
| `FR-CORE-15` | use case「從結算畫面開始新局」（`UC_RESTART`）；GameClock.startNewGame()：從第 1 天、開局狀態（`FR-STN-21`）重新開始 | [`usecase`](usecase.md)、[`class-station-crisis`](class-station-crisis.md) |
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
| `IF-03` | Station ..> TaskDispatcher、TaskDispatcher ..> Station（物資預留） | [`class-station-crisis`](class-station-crisis.md)、[`seq-crisis`](seq-crisis.md) |
| `IF-05` | Station → 使用者介面 | [`class-station-crisis`](class-station-crisis.md) |
| `IF-06` | GameClock、Settlement → 使用者介面 | [`class-station-crisis`](class-station-crisis.md) |
| `IF-07` | ColonistDeterioration ..> Colonist | [`class-station-crisis`](class-station-crisis.md)、[`seq-crisis`](seq-crisis.md) |
| `IF-08` | GameClock、CrisisManager 讀取 Station、Colonist | [`class-station-crisis`](class-station-crisis.md)、[`seq-crisis`](seq-crisis.md) |
| `NFR-07` | 設定檔中的初值：FacilitySpec（建造成本、產出）、CrisisManager 的強度倍率與係數上下限、完整度公式係數 0.2、開局物資；TaskDispatcher.instructionDelaySeconds 與 Colonist 數值初值（見張晏碩類別圖設計說明第 2 點） | [`class-station-crisis`](class-station-crisis.md)、[`class-colonist-control`](class-colonist-control.md) |
| `NFR-08` | CrisisManager.seed | [`class-station-crisis`](class-station-crisis.md)、[`seq-crisis`](seq-crisis.md) |
| `NFR-09` | CrisisManager.writeDebugLog() | [`class-station-crisis`](class-station-crisis.md)、[`seq-crisis`](seq-crisis.md) |

## B 負責的需求

依張晏碩各圖開頭的「對應需求」整理，**待張晏碩檢查**。

| 需求 | 對應的 UML 元素 | 圖 |
| --- | --- | --- |
| `FR-COL-01`～`03`、`FR-COL-15`～`17` | Colonist 的屬性（hp、satiety、stress、三項專長、tolerance、isAlive） | [`class-colonist-control`](class-colonist-control.md) |
| `FR-COL-04`～`09`、`FR-COL-11`～`12`、`FR-COL-21` | Colonist.updateVitals()、calculateEfficiency() | [`class-colonist-control`](class-colonist-control.md)、[`state-colonist`](state-colonist.md) |
| `FR-COL-10`、`FR-COL-13`～`14`、`FR-COL-26`～`28` | TaskDispatcher.checkSelfCare()、settleReservation()；Task（EAT、REST）、Task.reservedSupply；Eating、Resting 狀態 | [`class-colonist-control`](class-colonist-control.md)、[`seq-command`](seq-command.md)、[`state-colonist`](state-colonist.md) |
| `FR-COL-18`～`20` | Colonist.receiveCrisis()、currentCrisisImpact、endCrisisEffect() | [`class-colonist-control`](class-colonist-control.md)、[`state-colonist`](state-colonist.md) |
| `FR-COL-22`～`25` | Colonist.isCollapsed、isAlive；CollapsedResting、RecoveryResting、Dead 狀態 | [`class-colonist-control`](class-colonist-control.md)、[`state-colonist`](state-colonist.md) |
| `FR-CTL-01`～`04`、`FR-CTL-14` | TaskDispatcher.submitPlayerTask()、instructionDelaySeconds；TaskStatus.PENDING_DELAY；循序圖的 par 區塊（延遲與移動期間仍可操作） | [`class-colonist-control`](class-colonist-control.md)、[`seq-command`](seq-command.md) |
| `FR-CTL-05`～`07`、`FR-CTL-13` | TaskDispatcher.interruptAndSaveProgress()、resumeTask()；Task.progress、creationOrder | [`class-colonist-control`](class-colonist-control.md)、[`seq-command`](seq-command.md)、[`state-colonist`](state-colonist.md) |
| `FR-CTL-08`～`12` | TaskDispatcher.dispatch()、cancelTask()；TaskKind；Task → Facility；Task.markWaiting() | [`class-colonist-control`](class-colonist-control.md)、[`seq-command`](seq-command.md)、[`usecase`](usecase.md) |
| `UI-01`、`UI-03` | use case「查看天數及太空站完整度」（主畫面常駐顯示） | [`usecase`](usecase.md) |
| `UI-02`、`UI-04` | use case「查看殖民者個體資訊」 | [`usecase`](usecase.md) |
| `UI-05` | use case 設計說明第 5 點：個體面板不顯示目前工作與工作優先度，優先度在工作指派介面設定 | [`usecase`](usecase.md) |
| `UI-06` | use case「下達建造／維修／操作設施工作指令」；指令循序圖第 1 步（選目標與優先度，預設 3） | [`usecase`](usecase.md)、[`seq-command`](seq-command.md) |
| `UI-07` | use case「查看勝敗結算、指標與總分」 | [`usecase`](usecase.md) |
| `UI-08` | use case「查看物資總量、預留量與可用量」 | [`usecase`](usecase.md) |
| `UI-09`、`UI-11` | use case「查看殖民者及當前危機提醒」 | [`usecase`](usecase.md) |
| `UI-10` | use case「查看一般工作等待原因」；指令循序圖的 WAITING 分支 | [`usecase`](usecase.md)、[`seq-command`](seq-command.md) |
| `IF-01`、`IF-02` | TaskDispatcher --> Colonist（assigns） | [`class-colonist-control`](class-colonist-control.md)、[`seq-command`](seq-command.md) |
| `IF-04` | Colonist 的屬性（hp、satiety、stress、三項專長、tolerance、isCollapsed、isAlive）提供給介面；use case「查看殖民者個體資訊」 | [`class-colonist-control`](class-colonist-control.md)、[`usecase`](usecase.md) |

## 不在 UML 範圍的需求

| 需求 | 原因 |
| --- | --- |
| `NFR-01`～`NFR-06`、`NFR-10` | 效能、可用性、可攜性與試玩驗證，屬於實作與測試階段，類別圖和循序圖無法表達 |

## 檢查結果

- A 負責的 `FR-CORE`、`FR-STN`、`FR-CRI` 共 53 條需求，都至少對應到一個 UML 元素。
- B 負責的 `FR-COL` 28 條、`FR-CTL` 14 條、`UI` 11 條，依上表都對應到 B 的圖（待張晏碩確認）。
- A 的兩張圖沒有出現 SRS 沒要求的功能；圖上的設計決定（例如設施分類用繼承、換日時先算連鎖損壞）都寫在各圖的「設計說明」。
