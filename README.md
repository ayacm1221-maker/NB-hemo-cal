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


## 單位更新（2026-10-11）
- IVRT 改為秒（s），IOWA 門檻 0.030/0.050 s；報告以三位小數顯示。
- Pulmonary vein D velocity 改為 cm/s，IOWA 門檻 30/50 cm/s；報告以一位小數顯示。
- localStorage 已存舊值自動執行一次性轉換（ms→s、m/s→cm/s）；不更動其他公式。
- 更新後對同一患者進行臨床使用前，仍請核對已存數值。


## 2026-10-11 測量順序整合
- 輸入頁新增「🧭 測量順序」捷徑按鈕，直接顯示使用者提供之總覽圖片。
- 教學圖庫首張為 Workflow，後面八張原有教學圖維持原樣。
- 手機顯示 Workflow 時可水平捲動瀏覽圖中文字。
- IOWA、PLASE、Bedside、Report、前次單位換算規則均維持不變。


## 本次更新
- 已將測量順序圖替換為手機友善的直式版本（measurement_guides/00_echo_workflow.png）。
- 其餘教學圖、計算功能、Report、Bedside 與分頁設定維持不變。


## 圖片顯示改善
- 測量順序圖預設依手機／桌面畫面縮放至可視高度（而非固定 1100px 寬），不需左右滑動即可看到全圖。
- 點選「放大查看」才進入細節瀏覽模式，並可點「縮小至全圖」返回。
- 九張圖片內容與其他 APP 計算功能均未修改。


## 本次更新
- 已將「左房面積與長徑（A4C）」教學圖替換為使用者最新提供版本（measurement_guides/01_la_a4c.png）。
- 其他教學圖、Workflow、Report、Bedside、IOWA、PLASE 與分頁設定均維持不變。


## TAPSE / cTAPSE / Z-score (2026-10-14)
- 輸入 TAPSE、RV Length（均 cm）及 PNA（天），原本 GA 欄位共用為出生胎齡。
- 出生後 ≤2 天且出生 GA 26–41 週：Koestenberger et al. Neonatology 2011 模型：TAPSE_pred (cm) = -0.471 + 0.036 × GA（週）；Z = (TAPSE - TAPSE_pred)/0.065。
- 出生後 >2 天且出生 GA ≥37 週：Koestenberger et al. JASE 2009 年齡分組：0–30 天、1–3 月、4–6 月、7–12 月。以文獻 Table 1 平均值與 ±2 SD 推估 SD=(upper−lower)/4，僅估算組內 Z，不代表連續年齡模型。
- 早產兒出生後 >2 天及其他超出研究族群者：不輸出 Z-score，不將 2009 健康兒童表格當作已驗證的 NICU 早產兒標準。
- cTAPSE = TAPSE(cm)/RV Length(cm)×100%，此數值不使用一般 TAPSE Z-score 評估。
- Results、Bedside 和 Hemodynamic Report 同步顯示可計算項目；舊 PDA / PLASE / IOWA 演算法保持原樣。
- 參考論文：Koestenberger et al. Neonatology 2011;100:85–92. DOI:10.1159/000322006；Koestenberger et al. J Am Soc Echocardiogr 2009;22:715–719. DOI:10.1016/j.echo.2009.03.026。
- 本工具用於臨床決策輔助，TAPSE 非右心室射出分率的直接替代值。


## cTAPSE 研究參考值
- Results 和 Bedside 同時列出：出生後前 3 天極低出生體重兒 cTAPSE 25 ± 4%（先前提供之書籍摘要，原始研究尚待核實）。
- 出生後第 14 天無 PDA 早產兒 cTAPSE 38.0 ± 5.5%（Toyoshima et al., Pediatric Research 2024, Table 3）。
- 依 PNA 顯示研究時間點的適用性提示，但不因此直接認定個別病人符合研究收案條件。
- 不計算 cTAPSE Z-score，不將上述 SD 值作為正常／異常或治療門檻；TAPSE 2011/2009 的 Z-score 計算維持不變。


## 本次版面調整
- Right Ventricular Function 輸入區塊移至輸入分頁最後，置於「清除所有輸入」按鈕之前。
- Results 的右心室區塊只列 TAPSE、cTAPSE、TAPSE Z-score 三項，保留原有參考資訊。
- Bedside 的 Koestenberger 2011 參考說明改為三行淺灰色小字，與數值分開顯示。
- 所有臨床計算式、Report 與測量圖保持不變。


## Results 排序調整
Results 分頁依序顯示 Hemodynamic Results、IOWA Score、Right Ventricular Function｜TAPSE（最下方），未修改計算邏輯。


## 本次更新
- 新增「TAPSE（三尖瓣環收縮期位移）測量教學」圖片，並連結到 TAPSE 與 RV Length 欄位旁的 ⓘ 按鈕。
- 教學圖庫新增 TAPSE 教學圖，圖庫順序為 Workflow、TAPSE、其他測量教學圖。
- 已將 PDA / LPA 教學圖（measurement_guides/05_pda_lpa.png）替換為最新版本。
