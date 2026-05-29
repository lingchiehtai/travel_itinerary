# 行程表網頁 快速入門指南

## 📋 專案說明

這是一個互動式日本中部 7 天行程規劃網頁，使用 HTML + CSS + JavaScript 打造。

**特色功能：**
- ✅ 按鈕切換每日行程（D1～D7 + 行程摘要）
- ✅ 淡藍色漸層背景 + 浮動泡泡動畫效果
- ✅ 行程卡片響應式設計（手機、平板、電腦都適配）
- ✅ 粘性按鈕列（捲動時固定在上方）
- ✅ 微軟正黑體大標題 + 清晰行程內文

---

## 📁 檔案結構

```
japan-chubu-itinerary.html    ← 網頁主檔案（含 HTML + CSS + JS）
japan-itinerary-code-guide.md ← 程式碼詳細說明文件
README.md                      ← 本檔案
```

---

## 🚀 如何瀏覽網頁

### 1. 開啟網頁
直接用瀏覽器打開 `japan-chubu-itinerary.html` 即可，無需伺服器。

### 2. 瀏覽行程
- 點擊上方 **D1～D7** 按鈕切換各天行程
- 點擊 **摘要** 按鈕查看行程統計
- 按鈕可橫向滑動（超出螢幕寬度時）

### 3. 分享與下載
- 用瀏覽器「另存頁面」功能儲存為 HTML
- 或複製連結分享給他人

---

## 🎨 快速修改指南

所有可自訂的部分都在 `<style>` 區塊內（第 8–335 行）。

### 常見修改

#### 1. 改變行程內文字體大小
```css
.schedule li {
  font-size: 18px;  /* 改這個數字，目前 18px */
}
```
位置：程式碼第 213 行

#### 2. 改變標題與頂端距離
```css
.container {
  padding: 60px 4px 80px;  /* 改第一個 60px */
}
```
位置：程式碼第 42 行

#### 3. 改變頁面背景顏色
```css
body {
  background: linear-gradient(160deg, #a8d8f0 0%, #ceeafa 30%, #e0f4fd 60%, #b8e2f5 100%);
  /* 改這些十六進位顏色代碼（#開頭）*/
}
```
位置：程式碼第 23 行

#### 4. 改變卡片左右邊距
```css
.day-card {
  margin-left: 4px;   /* 改這個 */
  margin-right: 4px;  /* 或改這個 */
}
```
位置：程式碼第 115–116 行

#### 5. 隱藏裝飾線（標題上下方的金色線）
```css
.header::before { display: none; }  /* 隱藏上方線 */
.header::after { display: none; }   /* 隱藏下方線 */
```
位置：程式碼第 54–61 行

#### 6. 改變按鈕列與行程卡片距離
```css
.tab-bar {
  margin-bottom: 12px;  /* 改這個，目前 12px */
}
```
位置：程式碼第 267 行

#### 7. 改變泡泡動畫（增減泡泡數量）
```javascript
const bubbles = Array.from({ length: 28 }, () => createBubble(true));
                                      /* 改這個 28 */
```
位置：程式碼第 596 行

---

## 🎯 全局顏色變數

頁面所有顏色都由以下變數控制，改一次全頁生效：

```css
:root {
  --ink: #1a2a3a;      /* 主要文字顏色（深藍黑）*/
  --rust: #2e6fa3;     /* 強調色（交通、城市標籤）*/
  --moss: #3a8a7a;     /* 綠色（景點標籤）*/
  --mist: #5a87a8;     /* 次要文字（時間欄）*/
  --gold: #3a9fc8;     /* 主色（按鈕、卡片頂線）*/
  --line: #9ecde8;     /* 分隔線 */
}
```

位置：程式碼第 9–18 行

---

## 📱 響應式設計

網頁會自動適配不同螢幕尺寸：
- **手機**（< 600px）：單欄布局，按鈕列可橫向滑動
- **平板**（600–1024px）：寬度 780px，左右留白
- **電腦**（> 1024px）：同上，使用者體驗最佳

---

## ⌨️ 主要 HTML 結構

### 頁首
```html
<div class="header">
  <div class="title-jp">日本中部<br>悠閒自然路線</div>
  <div class="cities-strip">名古屋 · 飛驒高山 ...</div>
</div>
```

### 按鈕列
```html
<div class="tab-bar">
  <button class="tab-btn active" onclick="showDay(1)">D1</button>
  <button class="tab-btn" onclick="showDay(2)">D2</button>
  <!-- ... D3-D7 ... -->
  <button class="tab-btn tab-summary" onclick="showSummary()">摘要</button>
</div>
```

### 行程卡片（D1 為例）
```html
<div class="day-card" data-day="1">
  <div class="day-header">
    <span class="day-num">DAY 01</span>
    <span class="day-title">名古屋｜城下町漫步</span>
  </div>
  <ul class="schedule">
    <li><span class="time">09:00</span>
        <span class="activity">抵達名古屋</span></li>
  </ul>
  <div class="tip-box">提示文字</div>
</div>
```

---

## 🛠️ 進階修改

### 改變卡片內距
```css
.day-card {
  padding: 20px 24px 18px;
  /*       ↑上   ↑左右  ↑下 */
}
```

### 改變按鈕圓角程度
```css
.tab-btn {
  border-radius: 8px;  /* 越大越圓，8px = 扁扁的圓角 */
}
```

### 改變文字行高（行距）
```css
.schedule li {
  line-height: 1.7;  /* 改這個，越大行越寬 */
}
```

### 改變卡片陰影
```css
.day-card {
  box-shadow: 0 4px 18px rgba(60,140,200,0.1);
  /*          X  Y  模糊  顏色+透明度 */
}
```

---

## 🎬 JavaScript 功能

### 切換行程
```javascript
function showDay(n) {
  // 隱藏全部卡片，顯示第 n 天
}

function showSummary() {
  // 隱藏全部卡片，顯示摘要
}
```

### 泡泡動畫
- 28 顆泡泡在背景浮動
- 每顆泡泡有不同大小、速度、透明度
- 到達頂端會消失並重新生成


---

## ✨ 網頁使用技術


1. **CSS 漸層**：背景多點漸層
2. **CSS 動畫**：淡入、泡泡浮動
3. **CSS Grid / Flexbox**：行程排版
4. **JS 事件監聽**：按鈕點擊切換
5. **Canvas 繪圖**：泡泡效果
6. **響應式設計**：`clamp()` 函數
7. **毛玻璃效果**：`backdrop-filter: blur()`


---

**最後更新：2026年5月29日**
