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


## 2026-10-10 單位更新：mm → cm
- LA length (A4C)、LVDd、LVDs、Hes、SVC diameter max/min、PDA diameter (PDAd) 改為 **cm** 輸入。
- 已同步更新 LAV、Expected LVDd、SVC flow、PLASE v1/v2、IOWA PDA size/weight 與 Bedside LVDd 門檻。
- 已有舊版 localStorage 數值會在第一次開啟新版時由 mm 自動轉成 cm（只轉換一次）。
- GitHub Pages：將本資料夾「內部所有檔案」上傳至 Repository 根目錄。


## Report (2026-10-10)
Added fifth tab: editable PDA/Hemodynamic report with detailed/brief modes and copy action.
New fields: manual LVEF %, PDA shunt direction, PDA flow pattern. Manual LVEF overrides calculated LVEF when provided.
PDA diameter blank is rendered as 'No PDA' by requested workflow convention, and is not proof of absence; always verify before pasting into clinical notes.

## 本次更新
- PDA report 改為精簡的逗號分隔單行格式，例如：`PDA (0.18cm, L->R, pulsatile), LA/Ao 1.5, Mitral E 85cm/s, IVRT 25ms`。
- 未填入的量測項目不顯示；PDA 直徑未填時維持 `No PDA`。
- PDA Risk（PLASE v1、v2、NT-proBNP + GA）完整移至 Bedside，移除獨立底部標籤。
- 保留 Hemodynamic report、Impression、自訂編輯與複製功能。

## Report & Navigation update
- 底部四個分頁平均分配寬度（各 25%）。
- PDA report 於 PLASE v2 可計算時顯示其預測風險百分比。
- 於 NT-proBNP + GA 可計算時顯示其預測風險百分比。
- IOWA 七項資料全部可計算時才顯示總分（x/14），不顯示部分總分。
- PLASE v1 不會出現在報告中；Bedside 的模型與原有計算規則均保留。
- 注意：報告曾經手動修改時，按「重新產生」才能更新新分數。

## PDA select styling
PDA shunt direction 與 flow pattern 的選單已統一採用一般 measurement input 的邊框、圓角、字級、箭頭及 focus 樣式。無更動分數和報告計算。
