# 危機觸發循序圖

- **負責人**：施家瑋（A）
- **依據**：SRS v1.0 `FR-CRI-01`～`04`、`06`～`14`、`FR-STN-16`、`17`、`23`、`FR-CORE-06`、`08`、`IF-03`、`IF-07`、`IF-08`、`UI-11`、`NFR-08`、`NFR-09`
- 類別見 `class-station-crisis.md`。`TaskDispatcher`、`Colonist`、使用者介面由張晏碩負責，本圖只畫訊息。
- 情境：一個遊戲天之內，從排程危機波次、觸發事件，到換日時評估發展狀況。

```mermaid
sequenceDiagram
    autonumber
    participant GC as GameClock
    participant CM as CrisisManager
    participant W as Wave
    participant ST as Station
    participant F as Facility
    participant TD as TaskDispatcher
    participant C as Colonist
    participant UI as 使用者介面

    Note over GC,CM: 第 d 天開始
    GC->>CM: onNewDay(d)
    CM->>CM: 強度 = baseIntensity(d) × coefficient
    CM->>W: scheduleWave(d)：用 seed 決定事件與觸發秒數
    Note over CM,UI: 觸發前不通知介面（FR-CRI-03 無預警）

    loop 每一幀
        GC->>GC: tick(delta)
        GC->>CM: tick(秒數)
        opt 到達觸發秒數
            CM->>W: trigger()
            loop 波次中的每個危機事件
                alt 隕石撞擊
                    W->>ST: 隨機選 1 個已建成的設施
                    ST->>F: takeDamage(嚴重度)（含相鄰設施）
                else 通訊干擾
                    W->>ST: 選 1 座通訊設施
                    ST->>F: takeDamage(嚴重度)
                else 設備故障
                    W->>ST: 隨機選 1 個運作中的設施
                    ST->>F: takeDamage(嚴重度)
                else 殖民者狀態惡化（IF-07）
                    W->>C: receiveCrisis(等級 L, 30 秒)
                    Note right of C: D = max(0, L − 耐受性)<br/>效果依 FR-COL-19、20<br/>前一次未結束時覆蓋，不疊加
                end
                opt 有設施受損
                    ST->>ST: onFacilityDamaged()、computeIntegrity()
                    opt 該設施還沒有有效的維修工作
                        ST->>TD: 建立維修工作（IF-03）
                    end
                end
                W-->>UI: 危機發生的提醒（UI-11）
            end
        end
        GC->>ST: 讀取完整度、通訊中斷（IF-08）
        GC->>C: 讀取存活人數（IF-08）
        opt 完整度 < 25%、通訊中斷滿 120 秒或全員死亡
            GC->>GC: endGame(LOST, 失敗條件)
        end
    end

    Note over GC,CM: 第 d 天結束
    GC->>ST: dailyDecay()：連鎖損壞
    GC->>CM: onDayEnd(d)
    CM->>ST: 取得物資、完整度、自動化設施數（IF-08）
    CM->>C: 取得殖民者狀態（IF-08）
    CM->>CM: evaluateDevelopment()：係數限制在 0.7～1.3、比前一天最多變 0.1
    CM->>CM: writeDebugLog(d)：只寫進紀錄檔（NFR-09）
```

## 設計說明

只寫 SRS 沒有規定、畫圖時才決定的事：

- **危機在換日時就排好**：`onNewDay()` 用亂數種子決定當天的事件與觸發秒數，同一個種子、同樣的操作會得到同樣的序列（`NFR-08`）；排好之後到觸發前都不通知介面，所以沒有任何預兆（`FR-CRI-03`）。
- **失敗判定每一幀都做**：`GameClock` 在每次 `tick` 後檢查三個失敗條件，所以觸發的當下就結束遊戲，不必等到換日（`FR-CORE-06`）。
- **換日的順序**：先做連鎖損壞（`dailyDecay()`），再評估發展狀況。這樣評估用的完整度已經包含當天的連鎖損壞，隔天的係數比較能反映玩家的實際狀況。
- **危機提醒在事件之後才送出**：`UI-11` 的提醒只在 `trigger()` 之後出現，提醒的內容不包含調整係數（`FR-CRI-14`）。
