* ERD圖
```mermaid
erDiagram
    %% 1. 飼主與使用者檔案
    OWNER {
        int owner_id PK "1"
        string username "飼主名稱"
    }

    %% 2. 貓咪檔案 (推薦目標)
    CAT {
        int cat_id PK "101"
        int owner_id FK "1"
        int age_month "年齡 (月)"
        float weight_kg "體重 (kg)"
        string health_status "健康狀態"
    }

    %% 3. 飼料產品資料庫
    PRODUCT {
        int product_id PK "5001"
        string name "產品名稱"
        string brand "品牌"
        float protein_rate "蛋白質百分比"
        string target_life_stage "適用階段 (成貓/幼貓)"
        string product_type "產品類別 (乾糧/濕食)"
    }

    %% 6. 組合實體 1: AI 推薦結果快照 (M:N)
    RECOMMENDATION_SNAPSHOT {
        int snapshot_id PK "20251201_01"
        int cat_id FK "101"
        datetime timestamp "推薦執行時間"
        string engine_version "AI模型版本"
    }

    %% 7. 組合實體 2: 推薦細項 (M:N)
    RECOMMENDATION_ITEM {
        int item_id PK "1"
        int snapshot_id FK "20251201_01"
        int product_id FK "5001"
        float match_score "AI匹配分數 (0.95)"
        int rank "排序名次"
        float price_realtime "即時價格"
        boolean is_available "是否有庫存"
    }


    %% 關聯定義
    OWNER ||--o{ CAT : "擁有 (Owns)"
    CAT ||--o{ RECOMMENDATION_SNAPSHOT : "針對 (For)"
        
    %% M:N 關係 1: 推薦快照與產品
    RECOMMENDATION_SNAPSHOT ||--|{ RECOMMENDATION_ITEM : "包含 (Includes)"
    PRODUCT ||--o{ RECOMMENDATION_ITEM : "被推薦 (Is Recommended)"
