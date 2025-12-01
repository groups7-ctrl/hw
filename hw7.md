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

    %% === 樣式 (Mermaid 內建樣式) ===
    classDef system fill:#b2dfdb,stroke:#263238,stroke-width:2px,color:#000
    classDef entity fill:#f5f5f5,stroke:#263238,stroke-width:2px,color:#000
    class P0 system
    class E1,E2,E3 entity

    %% === 資料流 ===
    E1 -- "註冊/登入、貓咪資料(健康/偏好)" --> P0
    P0 -- "推薦飼料清單、購買連結、健康分析報告" --> E1

    P0 -- "健康數據查詢請求 (病症代碼)" --> E2
    E2 -- "疾病與營養學關聯數據" --> P0

    P0 -- "產品數據/價格查詢" --> E3
    E3 -- "飼料產品規格、即時價格/庫存" --> P0
