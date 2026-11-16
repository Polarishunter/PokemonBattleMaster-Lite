# Pokémon Battle Master · Lite（靜態體驗版）

此為依據使用者提供的「寶可夢對戰大師_正式版.rar」資料庫與「phase1-20261020-g-mechanics.rar」公開資源製作的**獨立靜態展示版**，並非原本的 Next.js + ASP.NET Core V2 完整版本。

## 主要功能

- 寶可夢圖鑑：共 1,458 筆繁體中文型態記錄，支援中文／英文／編號、屬性與型態篩選，檢視種族值、特性。
- 招式圖鑑：937 筆招式（含資料狀態為 NotApplicable 的歷史招式），提供類別、威力、命中、PP 與效果說明。
- 道具圖鑑：488 筆道具，提供繁體中文／英文名稱、ID 與類別搜尋；封存資料未包含完整效果，故不顯示推測效果。
- 六人隊伍編輯：自由配置隊伍、特性、道具、性格及最多四個招式；瀏覽器 LocalStorage 儲存與 JSON 匯入／匯出。
- 屬性分析：使用資料庫中「第六世代以後」18×18 屬性相剋表，估算招式屬性對單／雙屬性防守的倍率，以及隊伍弱點。

## 重要限制

- 資料為**封存快照**，不是即時同步的新遊戲更新；不等於原版所有 CurrentSnapshot API 結果或實時賽事統計。
- **不提供**完整傷害計算、戰鬥模擬、配招及道具合法性驗證、雲端儲存、登入或後端資料同步。
- 圖鑑圖片選用公開託管的 PokeAPI Sprites 官方插畫 URL 供線上預覽；圖片權利屬原權利人。網路離線或來源失效時會顯示替代圖形；特殊型態不冒充普通型態插畫。
- 使用者封存檔中的完整 SQLite 資料庫、logs、私密設定、Windows 執行檔和 caches **沒有**加入此網站。
- 這是非官方、非商業的粉絲展示用途。請注意 Pokémon 相關商標及圖片的權利歸屬，且公開再散布封存資料前仍應確認原來源授權。

## 本機執行

1. 在此資料夾開啟終端機。
2. 輸入 `python -m http.server 8000`。
3. 前往 `http://localhost:8000/`。

網站只有 `index.html`、`style.css`、`app.js`、`data/catalog.json`、`assets/logo.png`，可直接部署到 GitHub Pages 的 `main` 分支根目錄，或任何可提供靜態檔案的託管服務；不需要 Node.js、.NET 或 Python 在正式伺服器上持續執行。

## 來源

- 資料：使用者提供的正式版 SQLite 資料庫，精選 `CurrentSnapshots`、`Moves`、`Items`、`Natures`、`Types` 及 `TypeEffectiveness` 欄位。
- Logo：使用者提供的 G 版 `web/public/battle-master-icon-small.png`。
- 網頁風格：參考使用者 GitHub 的 Pokémon Battle Master V2 前端深灰及紅色主題，重新以原生 HTML/CSS/JS 製作。

## AGENTS.md 與可重複擴充實例

專案的開發規範詳見 [AGENTS.md](AGENTS.md)，包括網站目的、深灰紅色設計、SPA hash 路由、資料欄位、命名方式、AI 新增功能的步驟與驗收標準。

本次實際要求 AI 依規範增加「道具圖鑑」視圖（`#items`），重用既有 `data/catalog.json` 內的 `items[]` 和表格樣式，完成搜尋、分類、清除條件及分頁。只修改 `index.html` 的主選單、`app.js` 的視圖與導覽、`README.md` 的說明，**沒有重新設計網站，也沒有新增後端或變更資料格式**。

- GitHub Repository：<https://github.com/Polarishunter/PokemonBattleMaster-Lite>
- 公開網站：<https://polarishunter.github.io/PokemonBattleMaster-Lite/>
- 道具圖鑑：<https://polarishunter.github.io/PokemonBattleMaster-Lite/#items>