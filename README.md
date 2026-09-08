# 京都 7天6夜自由行

手機友善的京都行程手冊（靜態 PWA），方便旅途中快速查景點、交通、導航與分帳。

**線上版本：** [https://xinfu1993.github.io/kyoto-itinerary/](https://xinfu1993.github.io/kyoto-itinerary/)

## 行程概要

| 天數 | 日期 | 主題 |
|------|------|------|
| Day 1 | 12/20（日） | 抵京都・河原町首日 |
| Day 2 | 12/21（一） | 清水寺・祇園散步 |
| Day 3 | 12/22（二） | 金閣寺・北野今宮 |
| Day 4 | 12/23（三） | 任天堂博物館・宇治 |
| Day 5 | 12/24（四） | 伏見稻荷・二條城 |
| Day 6 | 12/25（五） | 嵐山竹林・聖誕夜 |
| Day 7 | 12/26（六） | 退房・返程關西機場 |

- **住宿：** 都城市酒店｜近鐵京都站  
- **出發／回程：** 關西國際機場（KIX）

## 功能

- **每日時間軸**：景點、建議時段、交通與備註
- **Google Maps 導航**：站與站之間的大眾運輸／步行連結
- **完成勾選**：進度存在瀏覽器（localStorage）
- **京都天氣**：依 Open-Meteo 顯示當日概況（需網路）
- **匯率換算**：日幣 JPY → 台幣 TWD（公開 API，非銀行牌價）
- **暗色模式**：可手動切換並記住偏好
- **Lightsplit 分帳**：一鍵開啟同行分帳連結
- **PWA 離線**：可加入主畫面；行程文字與總覽圖可離線開啟（天氣／匯率／地圖仍需網路）

## 加入主畫面（建議）

**iPhone（Safari）**

1. 用 Safari 開啟線上版本  
2. 分享 →「加入主畫面」

**Android（Chrome）**

1. 開啟線上版本  
2. 選單 →「安裝應用程式」或「加到主畫面」

## 專案結構

```
├── index.html              # 主頁（行程＋樣式＋互動）
├── overview.png            # 行程總覽圖
├── manifest.webmanifest    # PWA 設定
├── sw.js                   # Service Worker（離線快取／自動更新）
├── icon-192.png / icon-512.png
└── clear-cache.html        # 緊急清除快取（一般不需要）
```

純靜態站，無需建置工具或後端。

## 本機預覽

用任何靜態伺服器開啟根目錄即可，例如：

```bash
# Python
python -m http.server 8080

# Node (若已安裝 npx)
npx serve .
```

瀏覽器開啟 `http://localhost:8080`。

> 直接雙擊開啟 `index.html` 也可能可用，但部分功能（Service Worker、部分 API）在 `file://` 下可能受限，建議用本機伺服器。

## 部署（GitHub Pages）

此 repo 以 `main` 分支部署至 GitHub Pages。推送後約 1～2 分鐘會更新線上站。

Service Worker 採網路優先並會自動套用新版；若極少數情況仍看到舊畫面，可開一次 [`clear-cache.html`](https://xinfu1993.github.io/kyoto-itinerary/clear-cache.html) 再重整。

## 注意事項

- 匯率與天氣資料僅供參考，實際請以現場／官方資訊為準。  
- 營業時間、交通班次、票券預約可能變動，出發前請再確認。  
- 完成勾選與主題偏好存在本機瀏覽器，清除網站資料後會消失。

## License

個人旅遊行程手冊，僅供同行參考使用。
