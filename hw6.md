# 分鏡板(storyboard) 

## 圖 1：AI 聊天室 (Chat Interface)
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/0c9e5eb7-2b0f-4909-a628-06f320abf887" />

A. 輸入欄位 (Input Fields)
| 欄位名稱 | 資料型態 | 驗證規則 (Validation Rules) |
| :--- | :--- | :--- |
| **輸入您的需求 (對話框)** | Text Area (長文字) | 1. 必填 (才可發送) 2. 允許輸入中文、英數符號 3. 建議設定最大字元數限制 (防止 Token 溢出) 4. XSS 惡意代碼過濾 |
| **發送按鈕 (送出圖示)** | Action (動作) | 1. 僅在輸入框非空時啟用 (Enable) 2. 點擊後送出文字並清空輸入框 |

B. 螢幕顯示欄位 (Output Fields)
| 欄位名稱 | 功能描述 |
| :--- | :--- |
| **使用者名稱** | 顯示當前登入者身分 |
| **AI 訊息氣泡** | 顯示系統/AI 回覆的內容 (包含歡迎詞、規劃結果描述)|
| **使用者訊息氣泡** | 顯示使用者發送的歷史訊息 (藍色底) |
| **預設引導文字** | (若輸入框為空) 顯示 placeholder 提示文字「請描述您貓咪的狀況...」 |

---
