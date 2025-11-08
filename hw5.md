# UML類別圖
```mermaid
classDiagram
direction LR

%% === 左側：使用者與貓咪資料 ===
class 貓咪飼主 {
    +飼主ID: String
    +姓名: String
    +餵食偏好: List~String~
    --
    +註冊/登入()
    +輸入貓咪資料(Cat): Void
}

class 貓咪 {
    +貓咪ID: String
    +名稱: String
    +年齡: Int (月)
    +體重: Float (kg)
    +健康狀態: Enum (如: 健康, 腎臟病, 糖尿病)
    +歷史紀錄: Map
}

%% === 中央：推薦核心與產品 ===
class 飼料產品 {
    +產品ID: String
    +名稱: String
    +品牌: String
    +核心營養成分: Map~String:Float~
    +適用狀態: List
}

class 推薦引擎 {
    +AI模型: Object
    --
    +生成推薦(貓咪, 偏好): 推薦結果
    +計算匹配分數(): Float
}

class 推薦結果 {
    +結果ID: String
    +推薦時間: DateTime
    +目標貓咪ID: String
}

class 推薦項目 {
    +項目ID: String
    +排序: Int
    +匹配分數: Float
    +即時價格: Float
}

%% === 右側：外部服務與知識庫 ===
class 獸醫營養API {
    +查詢疾病營養指南(HealthStatus): JSON
    +獲取最新研究(): JSON
}

class 供應商API {
    +查詢即時價格(ProductID): JSON
    +檢查庫存(ProductID): JSON
}

%% === 關聯 ===
貓咪飼主 "1" -- "1..*" 貓咪 : 擁有
貓咪 "1" -- "0..*" 推薦結果 : 針對

推薦結果 "1" -- "1..*" 推薦項目 : 包含
推薦項目 "1" -- "1" 飼料產品 : 對應

推薦引擎 "1" -- "0..*" 推薦結果 : 產生

推薦引擎 ..> 獸醫營養API : 調用 (健康規則)
推薦引擎 ..> 供應商API : 調用 (產品數據)

```
## 使用案例 使用者登入系統
### 循序圖
```mermaid
sequenceDiagram
    actor 飼主
    participant 介面 as 系統介面
    participant P1 as P1: 資料管理模組
    participant D1 as D1: 飼主/貓咪資料庫

    飼主->>介面: 1. 輸入註冊資訊與貓咪健康資料
    介面->>P1: 2. 傳送註冊/新增貓咪資料
    P1->>P1: 3. 驗證資料完整性與邏輯性 (如年齡/體重)
    alt 資料驗證通過
        P1->>D1: 4. 寫入飼主與貓咪紀錄
        D1-->>P1: 5. 回覆寫入成功
        P1-->>介面: 6. 顯示成功訊息
    else 資料驗證失敗
        P1-->>介面: 7. 顯示錯誤訊息 (e.g., 體重數值不合理)
    end
    介面-->>飼主: 8. 顯示結果/提示
```
### 活動圖
```mermaid
flowchart LR
    A0([開始])
    A1[飼主輸入註冊資訊與貓咪健康資料]
    A2[系統接收並傳送至資料管理模組（P1）]
    A3[P1 驗證資料完整性與邏輯性]
    D1{資料是否有效？}
    A4[寫入 D1: 貓咪與飼主資料庫]
    A5[顯示成功訊息：資料儲存完畢]
    A6[顯示錯誤訊息：請修正輸入]
    A7([結束])

    A0 --> A1 --> A2 --> A3 --> D1
    D1 -- 否 --> A6 --> A7
    D1 -- 是 --> A4 --> A5 --> A7

```

## 使用案例 AI 推薦景點
### 循序圖
```mermaid
sequenceDiagram
    actor 飼主
    participant 介面 as 系統介面
    participant P2 as P2: AI 推薦引擎
    participant V as E2: 獸醫營養API
    participant D1 as D1: 貓咪資料庫
    participant D3 as D3: 營養學知識庫

    飼主->>介面: 1. 請求推薦 (指定目標貓咪)
    介面->>D1: 2. 獲取貓咪健康狀態與飼主偏好
    D1-->>介面: 3. 回傳數據
    介面->>P2: 4. 傳送特徵數據與偏好
    P2->>D3: 5. 載入營養規則與 AI 模型
    D3-->>P2: 6. 回傳知識庫數據
    P2->>V: 7. 查詢特定疾病的最新營養指南
    V-->>P2: 8. 回傳專業營養建議
    P2->>P2: 9. 執行推薦演算法 (計算匹配分數)
    P2-->>介面: 10. 回傳推薦產品ID清單 (排序結果)
    介面-->>飼主: 11. 顯示推薦結果
```
### 活動圖
```mermaid
flowchart LR
    A0([開始])
    A1[飼主請求飼料推薦]
    A2[讀取貓咪健康數據與飼主偏好（D1）]
    A3[載入營養學規則與知識庫（D3）]
    A4[調用獸醫API獲取最新指南]
    fork
      A5_1[將貓咪數據轉為AI特徵]
      A5_2[整合API與知識庫數據]
    end
    A6[執行AI推薦模型並計算匹配分數]
    A7[產生推薦產品ID清單並排序]
    A8[顯示推薦清單給飼主]
    A9([結束])

    A0 --> A1 --> A2 --> A3 --> A4
    A4 --> A6
    A6 --> A7 --> A8 --> A9

```
## 使用案例 動態更新路線建議
### 循序圖
```mermaid
sequenceDiagram
    actor 飼主
    participant 介面 as 系統介面
    participant P3 as P3: 產品查詢模組
    participant S as E3: 供應商API
    participant D2 as D2: 產品核心數據庫

    飼主->>介面: 1. 查看推薦清單
    介面->>P3: 2. 傳送推薦產品ID清單
    P3->>D2: 3. 獲取產品靜態細節 (成分、評分)
    D2-->>P3: 4. 回傳產品細節
    
    loop 針對清單中每項產品
        P3->>S: 5. 查詢即時價格與庫存
        S-->>P3: 6. 回傳即時價格與庫存狀態
    end
    
    P3->>P3: 7. 彙整數據並生成購買連結
    P3-->>介面: 8. 回傳最終呈現清單
    介面-->>飼主: 9. 顯示包含即時價格的推薦清單
```
### 活動圖
```mermaid
flowchart LR
    A0([開始])
    A1[飼主請求查看推薦清單]
    A2[產品查詢模組（P3）接收推薦產品ID清單]
    A3[讀取靜態產品細節（D2）]
    A4(調用供應商API查詢價格與庫存)
    D1{清單中產品是否皆已查詢？}
    A5[整合靜態細節與即時市場數據]
    A6[生成購買連結並排序]
    A7[顯示最終推薦清單給飼主]
    A8([結束])

    A0 --> A1 --> A2 --> A3 --> A4
    A4 --> D1
    D1 -- 否 --> A4
    D1 -- 是 --> A5 --> A6 --> A7 --> A8

```
