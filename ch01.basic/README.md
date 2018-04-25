# Bootstrap 4 重點精華

## 特點

- 元件化
- 標準網頁格線
- 標準化語意
- 前後端開發整合容易
- 780 萬個網頁使用

## v4 與 v3 的差異

- Less to Sass
- IE 8、IE 9 掰
- float to flexbox
- 增加中斷點：575px
- px to rem
- font-size: 14px to 16px
- 大方色彩
- 充滿生命力按鈕
- 靈活變化
- 移除、新增與整合元件
- 重新設計的文件

## Content

### Reboot

重新規範化元素風格

- windows 英文字體為黑體字，中文字體卻為明體字
  - 因為 bs 4 將字體部分以系統預設為主，但 windows、android
    則沒有預設這件事，所以 bs 4 以自載入字體的方式處理，英文字體為 Segoe UI，中文字體為新細明體
  - 建議 css 自專案加上 Microsoft JhengHei (微軟正黑體)，協調畫面才一致 (在
    "Segoe UI" 字體堆疊前面)
- box-sizing: border-box
  - 定義的寬度 = 實際呈現的寬度
- native font stack

    ```scss
    $font-family-sans-serif:
      // Safari for OS X and iOS (San Francisco)
      -apple-system,
      // Chrome < 56 for OS X (San Francisco)
      BlinkMacSystemFont,
      // Windows
      "Segoe UI",
      // Android
      "Roboto",
      // Basic web fallback
      "Helvetica Neue", Arial, sans-serif,
      // Emoji fonts
      "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol" !default;
    ```

### Typography

> Typography
> 字義：版面元素的安排，衡量版面上各個元素之間合宜的距離、視覺份量，以及相對的位置。

- 含語意的標籤
- 不含語意，但具有樣式的 class
- Display headings：如果你覺得 h1 標題不夠大的話
- list-unstyled、list-inlune
- text-truncate：把多餘的字裁切掉變點點點

### image

- 響應式：
  - .img-fluid (width: 100%; height: auto;)
- 縮圖：
  - .img-thumbnail
  - .rounded
- 對齊：
  - float (float-left、float-right，要注意父層 clearfix)
  - .mx-auto + .d-block 置中
  - 父層 .text-center 置中

### figures

圖片可增加描述

```html
<figure class="figure">
  <img src="..." class="figure-img img-fluid rounded" alt="A generic square placeholder image with rounded corners in a figure.">
  <figcaption class="figure-caption">A caption for the above image.</figcaption>
</figure>
```

可使用 text utilities 來對齊圖形的標題

### table

bs 4 建議是完整結構

```html
<table class="table table-responsive">
  <thead>
    <tr>
      <th scope="col">#</th>
      <th scope="col">First</th>
      <th scope="col">Last</th>
      <th scope="col">Handle</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">1</th>
      <td>Mark</td>
      <td>Otto</td>
      <td>@mdo</td>
    </tr>
    <tr>
      <th scope="row">2</th>
      <td>Jacob</td>
      <td>Thornton</td>
      <td>@fat</td>
    </tr>
    <tr>
      <th scope="row">3</th>
      <td>Larry</td>
      <td>the Bird</td>
      <td>@twitter</td>
    </tr>
  </tbody>
</table>
```

- .table-{color} or .thread-{color} 來增加背景顏色
- .table-striped 添加斑馬紋
  - (有添加 color 樣式會隨 color 做背景顏色的深淺區分)
- .table-bordered 在表格和儲存格的四邊添加邊框
  - (有添加 color 樣式會隨 color 做邊框顏色的調整)
- .table-hover 啟用 hover 狀態
  - (有添加 color 樣式會隨 color 做 hover 顏色的調整)
- .table-sm 可將儲存格 padding 縮減一半
- .table-responsive 可始終呈現水平滾動
- .table-responsive{-sm|-md|-lg|-xl} 創建響應式表格的最大斷點

## Layout

### Grid

- 讓畫面有設計感、有規則、有規律，會讓我們覺得比較整齊
- 12 欄是較多數字的公倍數
  - total width：960px (外圍 gutter 是內圍的一半)
  - Number of Columns：12
  - gutter width: 20px
  - column width：60px
- .container>.row>.col-xx>{content}
- .row：

    ```scss
    .row {
        display: flex;
        margin-left: -15px;
        margin-right: -15px;
    }
    ```

- 行動優先
  - 透過許多 media queries 設立中斷點，並製作具彈性的排版

      ```scss
      // Extra small devices (portrait phones, less than 576px)
      // No media query since this is the default in Bootstrap
       
      // Small devices (landscape phones, 576px and up)
      @media (min-width: 576px) { ... }
       
      // Medium devices (tablets, 768px and up)
      @media (min-width: 768px) { ... }
       
      // Large devices (desktops, 992px and up)
      @media (min-width: 992px) { ... }
       
      // Extra large devices (large desktops, 1200px and up)
      @media (min-width: 1200px) { ... }
      ```

  - xs (預設斷點) -> sm -> md -> lg
    - xs：<= 575px
    - sm：576px ~ 767px
    - md：768px ~ 991px
    - lg：992px ~ 1199px
    - xl：>= 1200px
  - .col-* (xs 省略) -> .col-sm-* -> .col-md-* -> .col-lg-* -> .col-xl-*
  - 舉例：

      ```html
      <div class="row">
        <div class="col-sm-4 side-bar">
        </div>
        <div class="col-sm-8 content">
        </div>
      </div>
      ```

    畫面寬度小於 575px 將會調整為 12 滿版寬 (單欄)，若設置 md 則為小於 768px
    調整為單欄，所以會是組合式，就有多裝置自適應效果

### Flex

可以寫成

```html
<div class="row">
  <div class="col"></div>
  <div class="col"></div>
  <div class="col"></div>
</div>
```

自動幫你分配比例為三等寬

```scss
.col {
  flex-basis: 0;
  flex-grow: 1;
  max-width: 100%;
}
```

- 傳統 float 如同水一樣可左右流動，但這概念已無法應付現在多元的排版方式，如：置中、垂直、等距等等
- flex 解決了這樣問題，並且具更優於 float 的彈性
- 詳細 flex 可參考我另一篇 blog：[CSS3 Flexbox 重點精華](https://eden-liu.com/frontend/css3-flexbox-key-points/)

#### .container

- 用來定義最外層的容器
- 種類：
  - 滿版寬 (.container-fluid)
    - 不需要嚴謹定義最大寬度
    - width: auto;
  - 階段固定寬 (.container)
    - 階段美感要求、需最大寬度限制
    - 低於 575px：width: auto;
    - 大於 575px：width: 540px;
    - 大於 768px：width: 720px;
    - 大於 992px：width: 960px;
    - 大於 1200px：width: 1140px;
- 使用到 grid system 一定要用 .container 作為最外層包裝，會補回 gutter on
  outside (margin-x: -15px)

## Utilities

### Flex

官方文件：[https://getbootstrap.com/docs/4.0/utilities/flex/](https://getbootstrap.com/docs/4.0/utilities/flex/)

- 外層要有 flex 屬性
- direction 是排序方法
- justify-content 主軸線對齊
- align-item 交錯軸對齊
- align-self 自己這個元件的交錯軸對齊

bs 就是作成了 class，並加上響應式項目 (組合技)：屬性名-尺寸-屬性值

其他特別 (少用) 屬性：

- flex-wrap
  - 物件超出範圍的時候，要不要做換行
  - row 預設會加上 wrap，會強制換行
  - flex-wrap 換行、flex-nowrap 不換行
- align-content
  - 在 wrap (換行) 屬性下才能使用
  - 全體元件對齊屬性 (不是僅針對換行的元件)
- order
  - 排列順序
  - .order-1、.order-2，數值小的會往前排列
  - 行動跟 PC 有不同排序的時候

### Spacing


官方文件：[https://getbootstrap.com/docs/4.0/utilities/spacing/](https://getbootstrap.com/docs/4.0/utilities/spacing/)

- 讓元件有善加上 margin 與 padding 的屬性
- 屬性-方向-尺寸 (組合技)：
  - {property}{sides}-{size} for xs
  - {property}{sides}-{breakpoint}-{size} for sm, md, lg and xl
  - sides 沒填就是 5 個方向都填
  - size: 0 ~ 5，$spacer * (0|.25|.5|1|1.5|3)
  - .m(l|r|t|b|x|y)-auto 可運用在 flex (很常用到)