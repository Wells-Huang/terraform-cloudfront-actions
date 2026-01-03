# Vue 靜態網站自動化部署範例

本專案是一個 Vue.js 應用程式，展示如何透過 **GitHub Actions** 實現自動化部署，並利用 **AWS S3** 與 **CloudFront** 進行安全且高效的網站託管。
AWS S3及 CloudFront部署程式碼置於: https://github.com/Wells-Huang/terraform_static_vuepage_deployment

## 🎯 核心目標

1. **自動化部署**：程式碼推送到 `main` 分支後，自動觸發建置並更新至 AWS。
2. **安全性管控**：
   - 網站檔案存放於私有 S3 儲存桶，拒絕任何直接存取。
   - 強制透過 CloudFront CDN 存取。
   - **地區限制**：目前設定僅允許 **台灣 (Taiwan)** 地區 IP 存取。
3. **效能優化**：透過 CloudFront 進行內容快取與傳遞，確保載入速度。

## 🚀 執行步驟

### 1. 自動觸發 (推薦)
- 在本地完成程式碼修改。
- 將變更 `git push` 到 `main` 分支。
- GitHub Actions 會自動開始執行部署流程。

### 2. 手動觸發
- 前往 GitHub Repository 的 **Actions** 分頁。
- 點選左側的 **"Deploy Vue App to S3 and Invalidate CloudFront"**。
- 點擊右側的 **Run workflow** 按鈕即可立即執行。

## ✅ 驗證方法

1. **檢查部署狀態**
   - 確認 GitHub Actions 的執行結果為綠色的 ✅ **Success**。

2. **確認網站更新**
   - 瀏覽 CloudFront 網址，確認內容已更新為最新版本。
   - *(提示：因有 CloudFront 快取，若未看到更新可嘗試透過 Actions 強制刷新或等待 cache 過期)*

3. **權限驗證**
   - **台灣使用者**：應能正常瀏覽網頁。
   - **非台灣使用者**：應看到 `403 Forbidden` 錯誤畫面。
