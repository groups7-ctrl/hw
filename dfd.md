
## 1. 系統環境圖 (Data Flow Diagram, Context Diagram)
```mermaid
flowchart LR
    %% 方向採 LR 來營造「左右外部、中央系統」的版面
    %% === 節點 ===
    P0["0. AI 智能貓咪飼料推薦系統"]

    subgraph EXL[ ]
      direction TB
      E1["E1: 貓咪飼主"]
    end

    subgraph EXR[ ]
      direction TB
      E2["E2: 獸醫資料庫 / 診所系統"]
      E3["E3: 飼料產品供應商 API"]
    end

    %% === 樣式 ===
    classDef system    fill:#b2dfdb,stroke:#263238,stroke-width:2px,color:#000
    classDef entity    fill:#f5f5f5,stroke:#263238,stroke-width:2px,color:#000
    class P0 system
    class E1,E2,E3 entity

    %% === 資料流（加粗箭頭、清楚標籤）===
    E1 -- "註冊/登入、貓咪資料(健康/偏好)" --> P0
    P0 -- "推薦飼料清單、購買連結、健康分析報告" --> E1

    P0 -- "健康數據查詢請求 (病症代碼)" --> E2
    E2 -- "疾病與營養學關聯數據" --> P0

    P0 -- "產品數據/價格查詢" --> E3
    E3 -- "飼料產品規格、即時價格/庫存" --> P0
```

## 2.系統流程圖 0 (Data Flow Diagram, Level 0)
```mermaid
flowchart LR
    %% DFD Level 0
    %% 外部實體
    C["E1: 貓咪飼主"]
    V["E2: 獸醫/營養 API"]
    S["E3: 產品供應商 API"]

    %% 核心流程
    subgraph PROC[ ]
      direction TB
      P1["P1: 貓咪資料與偏好管理<br/>（輸入、驗證、儲存）"]
      P2["P2: AI 智能推薦引擎<br/>（特徵工程、模型運算）"]
      P3["P3: 產品查詢與呈現<br/>（即時數據獲取、結果排序）"]
    end

    %% 資料儲存
    subgraph DATA[ ]
      direction LR
      D1["D1: 貓咪與飼主資料庫"]
      D2["D2: 飼料產品核心數據庫"]
      D3["D3: 營養學/疾病知識庫"]
    end

    %% 外部互動（資料流）
    C -- "健康資料/偏好輸入" --> P1
    P1 -- "個人化設定確認" --> C
    P3 -- "推薦飼料清單、購買連結" --> C

    %% P1 流程 <-> 資料庫
    P1 <--> D1

    %% P2 AI 智能推薦引擎（核心邏輯）
    P1 -- "貓咪特徵數據" --> P2
    D1 --> P2
    D3 --> P2
    P2 -- "推薦排序結果（ID清單）" --> P3

    %% P2 與外部 API 互動
    P2 -- "營養需求查詢" --> V
    V -- "營養學建議" --> P2

    %% P3 產品呈現
```
