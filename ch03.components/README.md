# Bootstrap 4 Components 重點精華

Components，是 Bootstrap
為何受歡迎的主要原因，它提供大量現成的組件供開發者使用，輕鬆組合與變化。加上
Bootstrap 結構化非常落實，進行客製化的調整也非常簡單。

這裏同 utilities 的篇幅一樣，透過 [Bootstrap 官網](https://getbootstrap.com/docs/4.0/components/) 做對照能事半功倍！！

在官網文件閱讀部分，不脫離下列這幾個項目：

- 基本元件範例
- 元件樣式變化
  - 元件變化
  - Grid 或 Utilities 等混合使用
  - 網頁親和性
- 元件與 JavaScript
- 編譯說明
  - $ 開頭的程式碼

## Alerts

訊息回饋用

- .alert 僅包含簡單的間距，可搭配 .alert-{color} 做不同背景色彩
- 內層有連結標籤 `<a>` 可掛上 .alert-link 類別，該連結顏色會是加深外層顏色的背景色彩，會比較協調
- 可增加額外的 HTML 元素

    ```html
    <div class="alert alert-success" role="alert">
      <h4 class="alert-heading">Well done!</h4>
      <p>Aww yeah, you successfully read this important alert message. This example text is going to run a bit longer so that you can see how spacing within an alert works with this kind of content.</p>
      <hr>
      <p class="mb-0">Whenever you need to, be sure to use margin utilities to keep things nice and tidy.</p>
    </div>
    ```

    效果可參見 [Alert 官網](http://bootstrap.hexschool.com/docs/4.0/components/alerts/#additional-content)

- plugin
  - 加上 `data-dismiss="alert"` 屬性可以移除 alert，是一次性的行為

## Badge

一行文字的額外訊息提供，可作連結、按鈕的計數器或 Tag 等

- .badge 僅提供 padding 與字體變白色，需搭配 .badge-{color} 做不同背景色彩
- 會自動符合各種尺寸 (em 單位繼承父元素尺寸)
- .badge-pill 可使標籤更圓潤
- 套用在 `<a>` 連結元素，提供 hover 和 focus 狀態 (背景變深)

## Breadcrumb

讓用戶了解目前在網頁的位置，也會提升 SEO，它是運用 `::before` 和 content 處理的

可用兩種結構：

```html
<ol class="breadcrumb">
  <li class="breadcrumb-item"><a href="#">Home</a></li>
  <li class="breadcrumb-item active"><a href="#">Library</a></li>
</ol>
```

```html
<nav class="breadcrumb">
  <a href="#" class="breadcrumb-item">Home</a>
  <a href="#" class="breadcrumb-item active">Library</a>
</nav>
```

網頁親和性：

- `aria-label="breadcrumb"` 來描述 `nav` 元素的導航說明
- `aria-current="page"` 到此群組的最後一個項目，表示這是當前頁面

## Buttons

bootstrap 使用最頻繁的元件

- .btn 僅是結構，可搭配 .btn-{color} 做不同主題色彩
- 加入 disable，會呈現半透明狀態
  - button 元素是加入 disabled 屬性
  - a 元素是加入 .disabled class
    - 看起來不能點其實還是可以點，所以建議還是用 button
- .btn-link，保有 button 結構，但是呈現是連結樣式
- 可套用在
  a、button、`input[type="button"]`、`input[type="submit"]`、`input[type="reset"]`
  元素，input 一定要前述那三個，樣式才會正確
- .btn-outline-{color}，屬於外框按鈕，hover 會變實心
- 加入 .active，啟用狀態，會直接按下去的樣式
- 有不同尺寸，加上 .btn-sm or .btn-lg
- 加入 .btn-block 變成塊狀屬性，填滿整個空間，並且兩個時上下相鄰會有間距
- plugin
  - 加上 data-toggle="button" 切換按鈕狀態，詳見[官網](http://bootstrap.hexschool.com/docs/4.0/components/buttons/#toggle-states)
  - 群組式 (checkbox or radio，下方以 checkbox 為例)

      ```html
      <div class="btn-group">
        <label for="" class="btn btn-secondary active">
          <input type="checkbox" autocomplete="off" checked>
        </label>
        <label for="" class="btn btn-secondary">
          <input type="checkbox" autocomplete="off">
        </label>
        <label for="" class="btn btn-secondary">
          <input type="checkbox" autocomplete="off">
        </label>
      </div>
      ```

      input 會被隱藏

## Button group

外層加上 .btn-group 的 class，裡面的 .btn 就可以被群組化了 (v4 採用 flex)

- 結構

    ```html
    <div class="btn-group" role="group" aria-label="Basic example">
      <button type="button" class="btn btn-secondary">Left</button>
      <button type="button" class="btn btn-secondary">Middle</button>
      <button type="button" class="btn btn-secondary">Right</button>
    </div>
    ```

- .btn-toolbar 可將整組的按鈕加入到按鈕工具列，實現再度群組化

    ```html
    <div class="btn-toolbar" role="toolbar" aria-label="Toolbar with button groups">
      <div class="btn-group mr-2" role="group" aria-label="First group">
        <button type="button" class="btn btn-secondary">1</button>
        <button type="button" class="btn btn-secondary">2</button>
        <button type="button" class="btn btn-secondary">3</button>
        <button type="button" class="btn btn-secondary">4</button>
      </div>
      <div class="btn-group mr-2" role="group" aria-label="Second group">
        <button type="button" class="btn btn-secondary">5</button>
        <button type="button" class="btn btn-secondary">6</button>
        <button type="button" class="btn btn-secondary">7</button>
      </div>
      <div class="btn-group" role="group" aria-label="Third group">
        <button type="button" class="btn btn-secondary">8</button>
      </div>
    </div>
    ```

    - 多群組的外層掛上該 class
    - 可加上 .justify-content-between 等的類別實現 flex 排版

- 也有 .input-group 將按鈕與輸入元素作群組
- 有不同尺寸的大小控制 (不是調整按鈕)
  - .btn-group-lg
  - .btn-group
  - .btn-group-sm
- .btn-group-vertical 可使其垂直排列
- plugin
  - 可再作到巢狀。官網是與下拉式選單群組使用，詳見[官網](https://getbootstrap.com/docs/4.0/components/button-group/#nesting)

## Card

非常大的元件，將 v3 以前比較少用的元件整合到這裡

- .card 可隨著外層 grid 調整它的大小，是有符合響應式的
- .card 加入 .text-{left|center|right} 調整內層的文字對齊
- .card 加入 utilities 改變不同色彩
  - 背景：.bg-{color}
  - 外框：.border-{color}
- 可透過 .bg-transparent 移除背景色

### 結構 1

```html
<div class="card"> <!-- 加入一個細細的 border 與白色的底 -->
  <img src="" alt="" class="card-img-top"> <!-- or .card-img-bottom，會符合響應式 -->
</div>
```
