# 分鏡板(storyboard) 

## 圖 1：首頁 
<img width="394" height="333" alt="螢幕擷取畫面 2025-12-22 125540" src="https://github.com/user-attachments/assets/494bcfe2-3ff1-4150-b07b-45b6e6aed40d" />

## A. 輸入欄位 (Input Fields)

| 欄位名稱 (Field Name) | 資料型態 (Data Type) | 驗證規則 / 觸發行為 (Validation Rules / Triggered Actions) |
| :--- | :--- | :--- |
| **帳號 (account)** | 字符串 (String) | 1. **必填**。2. 必須為有效 Email 格式。 |
| **密碼 (Password)** | 字符串 (String) | 1. **必填**。2. **👁 圖標**：切換顯示/隱藏。 |
| **登入 (Login)** | 按鈕 (Button) | 點擊：使用帳號與密碼進行**身份驗證**，成功後導向首頁。 |
| **忘記密碼？ (Forgot Password?)** | 連結/按鈕 (Link/Button) | 點擊：導向**忘記密碼**流程頁面。 |
| **前往註冊 (Go to Register)** | 按鈕 (Button) | 點擊：導向**使用者註冊**頁面。 |

---
## B. 螢幕顯示欄位 (Output Fields)

| 欄位名稱 (Field Name) | 功能描述 (Description) |
| :--- | :--- |
| **🔒 使用者登入 (User Login)** | 頁面標題。 |
| **帳號 (account)** | 帳號輸入框的標籤。 |
| **密碼 (Password)** | 密碼輸入框的標籤。 |
| **👁 圖標 (Eye Icon)** | 切換密碼內容顯示/隱藏。 |
---


## 圖 2：註冊頁面 
<img width="310" height="382" alt="螢幕擷取畫面 2025-12-22 125250" src="https://github.com/user-attachments/assets/bedba7c5-96fd-4c22-bc65-44e92c7bda34" />

## A. 輸入欄位 (Input Fields)

| 欄位名稱 (Field Name) | 資料型態 (Data Type) | 驗證規則 / 觸發行為 (Validation Rules / Triggered Actions) |
| :--- | :--- | :--- |
| **帳號 (account)** | 字符串 (String) | 1. **必填**。2. 必須為有效帳號格式。3. 系統中**唯一**。 |
| **密碼 (Password)** | 字符串 (String) | 1. **必填**。2. 建議有複雜度限制。3. **👁 圖標**：切換顯示/隱藏。 |
| **再次確認密碼 (Confirm Password)** | 字符串 (String) | 1. **必填**。2. 必須與 **密碼** 欄位的值**完全一致**。3. **👁 圖標**：切換顯示/隱藏。 |
| **註冊 (Register)** | 按鈕 (Button) | 點擊：執行所有欄位驗證，成功後建立帳號並導向指定頁面。 |
| **返回登入頁面 (Back to Login Page)** | 按鈕 (Button) | 點擊：導向「使用者登入」頁面。 |
---

## B. 螢幕顯示欄位 (Output Fields)

| 欄位名稱 (Field Name) | 功能描述 (Description) |
| :--- | :--- |
| **📋 註冊新帳號 (Register New Account)** | 頁面標題。 | 
| **請輸入帳號 (Please enter account)** | 帳號輸入框的標籤。 |
| **請輸入密碼 (Please enter password)** | 密碼輸入框的標籤。 |
| **請再次確認密碼 (Please confirm password again)** | 確認密碼輸入框的標籤。 |
| **👁 圖標 (Eye Icon)** | 切換密碼內容顯示/隱藏。 |
---


## 圖 3：使用者介面
<img width="924" height="384" alt="螢幕擷取畫面 2025-12-22 125604" src="https://github.com/user-attachments/assets/d3a529e6-c4c0-497d-b665-7216393c7ae1" />

## A. 輸入欄位 (Input Fields)

| 欄位名稱 (Field Name) | 資料型態 (Data Type) | 驗證規則 / 觸發行為 (Validation Rules / Triggered Actions) |
| :--- | :--- | :--- |
| **暱稱 (Nickname)** | 字符串 (String) | 1. **必填**。2. 必須為有效帳號格式。3. 系統中**唯一**。 |
| **年齡 (age)** | 字符串 (String) | 1. **必填**。2. 必須為有效帳號格式。|
| **體重 (weight)** | 字符串 (String) | 1. **必填**。2. 必須為有效帳號格式。|
| **品種 (Register)** | 字符串 (String) | 1. **必填**。2. 必須為有效帳號格式。 |
| **健康狀況/過敏原 (Health status/allergens)** | 字符串 (String) | 1. **必填**。2. 必須為有效帳號格式。 |
| **儲存所有變更 (Store all changes) ( | 按鈕 (Button) | 點擊：儲存並導向「功能」頁面。 |
---

| 欄位名稱 (Field Name) | 功能描述 (Description) |
| :--- | :--- |
| **暱稱 (Nickname)** | 暱稱輸入框的標籤。 | 
| **年齡 (age)** | 年齡輸入框的標籤。 |
| **體重 (weight)** | 體重輸入框的標籤。 |
| **品種 (Register)** | 品種輸入框的標籤。 |
| **健康狀況/過敏原 (Health status/allergens)** | 健康狀況/過敏原輸入框的標籤。 |
---

## 圖 4：功能頁面
<img width="1062" height="579" alt="螢幕擷取畫面 2025-12-22 131414" src="https://github.com/user-attachments/assets/c4e138c6-4e6d-4255-918b-9915e11dc135" />

## A. 輸入欄位 (Input Fields)

| 欄位名稱 (Field Name) | 資料型態 (Data Type) | 驗證規則 / 觸發行為 (Validation Rules / Triggered Actions) |
| :--- | :--- | :--- |
| **登出 (Logout)** | 按鈕 (Button) | 點擊：執行**登出**操作，清除使用者會話 (Session/Token)，導向「使用者登入」頁面。 |
| **輸入框 (Input box) | 字符串 (String) | 1. **必填**。2. 必須為有效文字格式。|
| **送出 (Send)** | 按鈕 (Button) | 點擊：**送出**功能，AI會找出資訊並回應需求。 |
---

## B. 螢幕顯示欄位 (Output Fields)

| 欄位名稱 (Field Name) | 功能描述 (Description) |
| :--- | :--- |
| **花生** | 顯示當前**登入的使用者暱稱或 ID** (圖中為 `花生`)。 |
| **分隔線 (Horizontal Line 1 & 2)** | 視覺分隔線，用於區分側邊欄的不同區域 (如：個人資訊區與操作區)。 |
| **✨ 歡迎來到台灣旅遊小幫手** | 頁面主標題，歡迎使用者並說明產品名稱。 |
| **AI 智慧諮詢 (全新升級)** | **功能區塊標題 1**，介紹 AI 諮詢功能。 |
| **AI 介紹 (Description for AI)** | 描述 AI 智慧排程的功能細節，包括自動排程、排序、計算交通等。 |
| **手動自由配置** | **功能區塊標題 2**，介紹手動自由配置功能。 |
| **手動配置介紹 (Description for Manual)** | 描述手動配置的功能細節，包括自訂旅遊天數、搜尋資料圖片、自由加入行程。 |
---
