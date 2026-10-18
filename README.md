# 店家小相簿

用照片和 hashtag 整理去過、想去的咖啡廳、早午餐、酒吧。純前端、無帳號,資料只存在使用者自己的瀏覽器(IndexedDB)。手機與電腦都能用,可「加到主畫面」當成 App,第一次開啟後支援離線。

## 功能
- 瀑布流照片牆,點照片才顯示店家詳細資訊
- 標籤(hashtag)篩選,可選聯集(OR)或交集(AND)
- 排序:去的時間、價位、評價、去的次數、加入時間、店名
- 「去過」與「想去」兩種狀態
- 備份與還原(複製 / 貼上 JSON)

## 資料結構
以店名為 key,每間店:

```
{ name, photos: [dataURL], visits: ["YYYY-MM-DD"], price: 0-4, rating: 0-5,
  tags: [], status: "visited" | "wish", notes, created }
```

## 檔案
| 檔案 | 用途 |
|---|---|
| `index.html` | 整個 App(HTML + CSS + JS 都在裡面) |
| `sw.js` | 離線快取。更新 App 後請把裡面的 `VERSION` 加一,使用者才會拿到新版 |
| `manifest.webmanifest` | 「加到主畫面」設定 |
| `icons/` | App 圖示 |

## 部署到 GitHub Pages
1. 把這些檔案放在 repo 根目錄(`index.html` 要在最外層)。
2. Repo 的 Settings → Pages → Source 選 `Deploy from a branch`,Branch 選 `main`、資料夾 `/ (root)`。
3. 約一分鐘後網址是 `https://<你的帳號>.github.io/<repo 名稱>/`。

## 使用提醒
- 資料綁定「網址 + 瀏覽器」。手機和電腦各自獨立,換網址或清除網站資料會消失,請定期用「備份」功能保存。
- iPhone:Safari → 分享 → 加入主畫面。Android:Chrome → 選單 → 安裝應用程式。

## 本機預覽
```
python3 -m http.server 8000
```
然後開 http://localhost:8000
