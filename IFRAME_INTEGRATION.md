# iframe 串接注意事項與案例

本文件提供網站廠商嵌入跨館 AI 導覽員的串接說明。**網站 iframe 以文字版 Web 為主要串接方式，並且必須開放相機與麥克風權限。**一般版、APP、Kiosk 與 LINE 導流網址一併列供其他情境使用。以下均為 Test 測試網址，正式環境網址請以服務提供方交付資訊為準。

## 串接資訊

| 使用情境 | 文字版 Test 網址（網站首選） | 一般版 Test 網址 |
| --- | --- | --- |
| Web | `https://moeai-test.omniguider.com/home/chat/nmns/web` | `https://moeai-test.omniguider.com/home/nmns/web` |
| APP | `https://moeai-test.omniguider.com/home/chat/nmns/app` | `https://moeai-test.omniguider.com/home/nmns/app` |
| Kiosk | `https://moeai-test.omniguider.com/home/chat/nmns/kiosk` | `https://moeai-test.omniguider.com/home/nmns/kiosk` |

網站 iframe 請使用 **文字版 Web** 路徑 `/home/chat/nmns/web`；APP 與 Kiosk 使用各自的平台路徑。以下 iframe 程式碼均以文字版 Web 網址示範。

### 館別代碼

上述網址中的 `nmns` 是**館別代碼範例**。各館串接時，須將它替換成服務提供方分配的館別代碼；同一館的 Web、APP、Kiosk、一般版及文字版網址都使用該館代碼。請勿將 `nmns` 當作所有館別共用的固定字串，也不要自行猜測代碼。

| 版本 | 網址格式（將 `{館別代碼}` 換成實際代碼） |
| --- | --- |
| 網站文字版 Web（主要串接） | `https://moeai-test.omniguider.com/home/chat/{館別代碼}/web` |
| 網站一般版 Web | `https://moeai-test.omniguider.com/home/{館別代碼}/web` |

若要指定語系，在平台路徑最後加上 `/zh-TW`、`/en`、`/ja` 或 `/ko`。下方含 `nmns` 的網址均為同一館別的 Test 範例；交付其他館別時，請同步替換所有範例中的代碼。

## 串接前確認

1. **嵌入與來源**：確認測試、正式環境各自的 iframe URL，並請服務方允許父頁來源嵌入。若子頁回應 `Content-Security-Policy: frame-ancestors` 或 `X-Frame-Options` 封鎖嵌入，前端加上 iframe 標籤也無法解決。若父頁使用 CSP，還須在父頁的 `frame-src` 允許子頁來源。
2. **相機與麥克風（必要）**：網站 iframe **必須**加上 `allow="camera; microphone"`，兩項權限都不可省略；父頁與子頁均須以 HTTPS 提供服務，本機開發可使用瀏覽器認可的 `localhost` 安全環境。若父頁有 `Permissions-Policy` 回應標頭，必須確認相機與麥克風都允許子頁來源。網站也應向使用者說明並引導其在瀏覽器授權；`allow` 只是允許服務提出請求，不能代替使用者同意。
3. **子頁功能**：由子頁在需要時呼叫 `navigator.mediaDevices.getUserMedia()`，處理拒絕、沒有裝置、裝置占用等情況，並在不用時停止媒體軌道。父頁無法透過跨來源 DOM 操作代替子頁完成這些步驟。
4. **登入與儲存**：若子頁依賴 Cookie、登入狀態或本機儲存，在 Safari、Firefox、無痕模式及封鎖第三方 Cookie 的環境實測。`SameSite=None; Secure` 是跨站 Cookie 的必要設定，但瀏覽器仍可能阻擋第三方 Cookie。
5. **畫面與導覽**：提供清楚的 `title`、足夠的手機高度與可捲動區域；確認服務內的彈窗、返回、外開連結與鍵盤操作。`iframe` 的 `load` 事件不代表子頁功能、權限或登入流程已成功。
6. **其他容器**：若父頁還會被放進另一層 iframe、App WebView 或館內觸控設備，須在最外層容器一起驗證權限政策與裝置權限。

### 權限政策範例（由父頁伺服器設定）

若部署環境已設定限制性 `Permissions-Policy`，必須讓服務來源同時取得相機與麥克風的請求資格。可由網站伺服器設定，例如：

```http
Permissions-Policy: camera=(self "https://moeai-test.omniguider.com"), microphone=(self "https://moeai-test.omniguider.com")
```

此標頭由網站伺服器送出。正式環境應換成正式服務來源；iframe 的 `allow` 和上層政策都要允許，瀏覽器才可能顯示授權提示。若 iframe 轉址至另一個來源，也要確認轉址後來源在政策與 `allow` 的允許範圍內。

## i18n 注意事項

- **父子頁各自管理語系**：網站的 `<html lang="zh-Hant">` 不會自動切換跨來源 iframe 的語系。若網站要指定導覽員語系，請使用下方的**網址路徑語系代碼**；`iframe title` 也應隨網站語系翻譯。
- **語系位置**：在平台路徑最後加上 `/語系代碼`。網站文字版 Web 英文為 `/home/chat/nmns/web/en`；一般版 Web 英文則為 `/home/nmns/web/en`。本服務說明沒有提供 `?lang=` 查詢參數或 `postMessage` 語系切換協定，請勿以其取代路徑語系。
- **未指定語系**：使用者曾選過語系時，沿用上次選擇；首次進入使用繁體中文。若網站需要固定語系，請在網址加入代碼，不要依賴預設值。
- **語系代碼**：繁體中文 `zh-TW`、英文 `en`、日文 `ja`、韓文 `ko`。網站內部若使用 `zh-Hant` 等其他代碼，組合網址前須轉成服務接受的代碼。
- **切換與測試**：網站切換語系後可更新 iframe 網址，但重載可能影響目前對話或導覽狀態。請測試各語系的介面文字、權限說明、錯誤訊息、語音功能和版面；如需不重載的切換方式，另與服務方確認。

### 指定語系網址範例

| 情境 | Test 網址 |
| --- | --- |
| 文字版 Web 英文 | `https://moeai-test.omniguider.com/home/chat/nmns/web/en` |
| 文字版 APP 日文 | `https://moeai-test.omniguider.com/home/chat/nmns/app/ja` |
| 文字版 Kiosk 韓文 | `https://moeai-test.omniguider.com/home/chat/nmns/kiosk/ko` |
| 一般版 Web 英文 | `https://moeai-test.omniguider.com/home/nmns/web/en` |
| 一般版 APP 日文 | `https://moeai-test.omniguider.com/home/nmns/app/ja` |
| 一般版 Kiosk 韓文 | `https://moeai-test.omniguider.com/home/nmns/kiosk/ko` |

## iframe 串接案例

### 案例一：網站嵌入文字版

將 iframe 放在需要顯示服務的頁面。`title` 請依服務用途及網站語系調整；寬高可依實際版型設定。

```html
<iframe
  src="https://moeai-test.omniguider.com/home/chat/nmns/web"
  title="跨館 AI 導覽員文字版"
  allow="camera; microphone"
  style="width: 100%; min-height: 600px; border: 0;"
></iframe>
```

網站串接時請保留範例中的 `allow="camera; microphone"`，不可省略任一項。實際啟用裝置仍須符合安全環境、上層權限政策、子頁程式及使用者授權。

### 案例二：依網站語系指定路徑

以網站目前的語系組合 iframe 網址。下例假設網站內部使用 `zh-Hant`，因此轉換成服務接受的 `zh-TW`；其他語系依實際網站需求擴充。

```html
<iframe id="guide-frame" title="跨館 AI 導覽員文字版" allow="camera; microphone"></iframe>

<script>
  const siteLocale = 'zh-Hant' // 改成網站目前的語系
  const localeMap = { 'zh-Hant': 'zh-TW', en: 'en', ja: 'ja', ko: 'ko' }
  const serviceLocale = localeMap[siteLocale] ?? 'zh-TW'
  const url = new URL(`https://moeai-test.omniguider.com/home/chat/nmns/web/${serviceLocale}`)
  document.querySelector('#guide-frame').src = url.href
</script>
```

若要沿用使用者上次選擇的語系，不要在網址加入語系代碼。一般版的 Web 基礎路徑是 `/home/nmns/web`。

### 案例三：LINE 導流時開啟外部瀏覽器

從 LINE 導流至服務網址時，在網址加入 `openExternalBrowser=1`。此參數可與路徑語系同時使用；加在語系路徑**之後**的查詢字串。以下是導流連結範例：

```html
<a href="https://moeai-test.omniguider.com/home/chat/nmns/web/en?openExternalBrowser=1">
  Open text version in English
</a>

<a href="https://moeai-test.omniguider.com/home/nmns/web?openExternalBrowser=1">
  開啟跨館 AI 導覽員一般版
</a>

<a href="https://moeai-test.omniguider.com/home/nmns/web/en?openExternalBrowser=1">
  Open standard version in English
</a>
```

`openExternalBrowser=1` 用於 LINE 導流連結；一般網站 iframe 串接使用前述文字版 Web 網址即可。

## 驗收清單

- [ ] 測試與正式 URL 可載入，瀏覽器 Console 沒有 `frame-ancestors`、`X-Frame-Options` 或 `frame-src` 阻擋訊息。
- [ ] 在正式 HTTPS 網址和目標瀏覽器／裝置上，分別測試相機、麥克風授權成功、拒絕及裝置不可用。
- [ ] **必要**：iframe 設有 `allow="camera; microphone"`，父頁 `Permissions-Policy` 未阻擋任一權限，並驗證子頁呼叫與授權提示；若有多層 iframe，逐層檢查。
- [ ] 驗證 iframe 與網站導覽、固定元件及其他嵌入內容不會互相遮擋，手機畫面可完整操作。
- [ ] 網站 iframe 使用文字版 Web 路徑 `/home/chat/nmns/web`；其他平台使用對應路徑，語系代碼加在路徑末端。
- [ ] 驗證未指定語系時的首次繁中與上次選擇行為；網站若需固定語系，使用明確代碼。
- [ ] LINE 導流連結加入 `openExternalBrowser=1`，並測試與語系路徑一起使用。
- [ ] 在第三方 Cookie 受限的瀏覽器中檢查登入與對話狀態。

## 參考文件

- [MDN：`getUserMedia()` 安全環境與 iframe 權限](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getUserMedia)
- [MDN：Permissions Policy 與 iframe `allow`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Permissions_Policy)
- [MDN：CSP `frame-src`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/frame-src) 與 [`frame-ancestors`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/frame-ancestors)
- [W3C：HTML 語言宣告](https://www.w3.org/International/questions/qa-html-language-declarations.en)
- [MDN：第三方 Cookie](https://developer.mozilla.org/en-US/docs/Web/Privacy/Guides/Third-party_cookies)
