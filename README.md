# Neonatal Hemodynamic Echo — GitHub Pages

此版本已包含 IOWA Score、Bedside 建議及五張測量教學圖。所有圖片皆使用相對路徑，適用 GitHub Pages 專案網站。

## 發布方式（使用 GitHub 網頁介面）

1. 在 GitHub 新建一個 public repository（例如 `neonatal-echo`）。
2. 將此 ZIP **解壓縮後**，上傳根目錄的 `index.html`、`.nojekyll`、`README.md` 和整個 `measurement_guides` 資料夾到 repository 的根目錄。不要直接上傳 ZIP 當作網站內容。
3. 前往 Repository → Settings → Pages。
4. 在 Build and deployment 中選 `Deploy from a branch`；Branch 選 `main`，Folder 選 `/(root)`，按 Save。
5. 部署完成後，前往 `https://<你的GitHub使用者名稱>.github.io/<repository名稱>/`。

## 注意事項

- 此版本是純前端靜態網頁，不需要伺服器或安裝相依套件。
- 不需要將患者個人資訊輸入此 APP；欄位資料儲存於目前瀏覽器的 localStorage。
- 為研發及測試版，臨床判讀規則須於正式使用前獨立驗證。
