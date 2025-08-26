# 學生進度追蹤系統 Student Progress Tracker

一個用於追蹤學生學習進度並自動發送課前訊息的網頁應用程式。

## 🚀 功能特色

- **學生管理**: 新增、編輯、刪除學生資料
- **進度追蹤**: 依據年級選擇對應章節與 Part
- **智慧篩選**: 依上課日、年級、姓名搜尋
- **自動訊息**: 生成標準化的課前訊息格式
- **數據匯出**: 支援 JSON 格式匯入匯出
- **n8n 整合**: 自動發送今日學生名單到 webhook
- **響應式設計**: 支援手機與桌面裝置
- **深色模式**: 護眼的深色主題

## 📱 線上預覽

**GitHub Pages**: [https://joshtsang916.github.io/student-progress-tracker/](https://joshtsang916.github.io/student-progress-tracker/)

## 🛠️ 本地開發

### 方法一：使用 Python 內建伺服器
```bash
# 在專案根目錄執行
python3 -m http.server 5500

# 開啟瀏覽器訪問
# http://localhost:5500/index.html
```

### 方法二：直接開啟檔案
直接用瀏覽器開啟 `index.html` 會因為 CORS 政策無法載入 JSON 資料，請使用方法一。

## 📁 專案結構

```
03-student-progress/
├── index.html              # 主要應用程式 (單檔 SPA)
├── curriculum.json         # 課程章節資料
├── students.json           # 學生初始資料
├── n8n-workflow.json       # n8n 工作流配置
└── README.md
```

## 🔧 n8n 整合

### Webhook 設定
- **Production URL**: `https://flows.josh0916.com/webhook/student-preclass`
- **觸發時間**: 每日上午 8:00 (可調整)
- **資料格式**: 標準 JSON payload

### 工作流匯入
1. 將 `n8n-workflow.json` 匯入到你的 n8n 實例
2. 啟用工作流
3. 測試 webhook 連接

## 💾 資料儲存

- **初始資料**: 從 `data/students.json` 載入
- **運行資料**: 儲存於瀏覽器 localStorage
- **備份**: 可透過匯出功能下載 JSON 檔案

### localStorage Keys
- `sp/v1/students`: 學生陣列資料
- `sp/v1/settings`: UI 偏好設定

## 📋 使用說明

### 1. 學生管理
- **新增**: 點選「新增學生」填寫基本資料
- **編輯**: 點選學生卡片的「編輯」按鈕
- **刪除**: 點選「刪除」並確認

### 2. 進度設定
- 每個學生卡片都有進度下拉選單
- 選擇章節後會自動載入對應的 Part 選項
- 進度會即時儲存到本地

### 3. 訊息複製
複製格式為三行訊息：
```
hi {學生姓名}
等一下準備好要上課的時候跟我說一聲 我們就繼續往後學
{YouTube 連結 或 （尚未設定連結）}
```

### 4. 資料管理
- **匯出**: 下載當前所有學生資料為 JSON
- **匯入**: 選擇覆蓋或合併現有資料

## 🌐 GitHub Pages 部署

1. 將專案推送到 GitHub
2. 前往 Settings → Pages
3. Source 選擇 "Deploy from a branch"
4. Branch 選擇 "main"
5. Folder 選擇 "/ (root)"

## 🔗 深連結

支援 URL hash 定位特定學生：
```
https://joshtsang916.github.io/student-progress-tracker/#student=a041b947
```

## 🎨 主題

- **淺色模式**: 預設主題
- **深色模式**: 點選 🌙 按鈕切換

## 📱 RWD 支援

- ✅ 桌面版 (1200px+)
- ✅ 平板版 (768px - 1199px)
- ✅ 手機版 (320px - 767px)

## 🔒 安全性

- 純前端應用，無後端伺服器
- 資料僅存於本地瀏覽器
- n8n webhook 使用 HTTPS 加密傳輸

## 🛡️ 瀏覽器支援

- ✅ Chrome 80+
- ✅ Firefox 75+
- ✅ Safari 13+
- ✅ Edge 80+

## 📝 授權

MIT License

## 🤝 貢獻

歡迎提交 Issue 和 Pull Request！

---

🤖 Generated with [Claude Code](https://claude.ai/code)