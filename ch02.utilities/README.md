# Bootstrap 4 Utilities 重點精華

Bootstrap Utilities 據多項通用類別供使用，搭配 Components
做組合技延伸更多不同效果。這裡建議跟著官網閱讀，會更得心應手喔！

官方文件：[https://getbootstrap.com/docs/4.0/utilities/](https://getbootstrap.com/docs/4.0/utilities/)

## Borders

- .border (預設淺灰)、.border-0、.border-{sides}-0
- color：.border + .border-{colors}
- border-radius：.rounded、.rounded-{side}、rounded-circle、.rounded-0

## Clearfix

清除浮動，.float-left、.float-right 的父層元素用，使其空間正常

## Close Icon

用在 alert 與 modals 的 components 上，是一個整段 `<button>` 程式碼

特別要加上 aria-label 元素屬性給看不見的人用

```html
<button type="button" class="close" aria-label="Close">
  <span aria-hidden="true">&times;</span>
</button>
```

## Colors

- primary
- secondary
- success
- danger
- warning
- info
- light
- dark

分為兩個部分

- 文字
  - text-{colors}
  - 單純文字
  - 連結
    - 滑鼠滑入會比較深一點
- 背景
  - bg-{colors}
  - 文字記得要搭配不同色彩

## Display

就是 display 屬性，套用時要注意標籤，可搭配不同斷點

- .d-{value} for xs
- .d-{breakpoint}-{value} for sm, md, lg and xl

## Embed

響應式的 iframe 功能，官方範例是 youtube 影片，它會保留 iframe 的比例 (21by9、16by9、4by3、1by1)

- iframe parent class：.embed-responsive + .embed-responsive-{比例}
- iframe class：.embed-responsive-item

## Flex

- Direction - 排列方向
  - .flex-row
  - .flex-row-reverse
  - .flex-column
  - .flex-column-reverse
- Justify content - 主軸元件排列
  - .justify-content-{start|end|center|between|around}
- Align items - 交錯軸元件排列
  - .align-items-{start|end|center|baseline|stretch}
- Align self - 交錯軸單一元件的排列 (所以 align-item 要加 s 的關係)
  - .align-self-{start|end|center|baseline|stretch}
- Auto margins
  - 用在 flex 內元件
  - 讓相鄰的 flex 內元件把空間推移開來
- Wrap - 物件超過寬度是否換行
  - .flex-wrap
  - .flex-nowrap
  - .flex-wrap-reverse
- Order - 排序
  - 1 ~ 12：order-{number}
- Align content - 有出現換行的時候所有元件排列
  - .align-content-{start|end|center|baseline|stretch}

## Float

- .float-left
- .float-right
- .float-none：清除它原本的浮動 (有 .float-left 與 .float-right 的元素上)
- 有包含斷點：.float-{sm|md|lg|xl}-{left|right|none}
- 記得外層要加入 clearfix 清除浮動

## Image replacement

.text-hide

隱藏文字的功能，用在背景圖有意義的時候，為了讓搜尋引擎做搜尋，但是這個文字是不需要顯示，僅為了
SEO 而存在，就可用 .text-hide 使其文字隱藏，通常運用在 Logo。

```html
<h1 class="text-hide">Custom heading</h1>
```

or Sass mixin

```scss
// Usage as a mixin
.heading {
  @include text-hide;
}
```

要使用 background-image 取代文字內容

```html
<h1 class="text-hide" style="background-image: url('/assets/brand/bootstrap-solid.svg'); width: 50px; height: 50px;">Bootstrap</h1>
```

## Position

- .fixed-top：移動到畫面頂端
- .fixed-bottom：移動到畫面底部
- .sticky-top：貼齊於頂端，將一個元素置於可視區的頂部，從邊緣到邊緣，但僅在你滾動視窗經過它之後。但他沒支援所有瀏覽器，IE
  11 與 Edge，會把 sticky 當成 relative 來使用

## Screenreaders

螢幕閱讀器 用戶使用

透過 .sr-only 將一個元素對所有設備隱藏 除了螢幕閱讀器。將 .sr-only 與
.sr-only-focusable 結合，以便在其被 focused 時再次顯示該元素 (例如透過鍵盤使用)

```html
<a class="sr-only sr-only-focusable" href="#content">Skip to main content</a>
```

也可用做 Sass mixins

```scss
// Usage as a mixin
.skip-navigation {
  @include sr-only;
  @include sr-only-focusable;
}
```

## Sizing

提供不同的寬與高的尺寸，寬 w，高則為 h，有 25、50、75 與 100% 四種數值

- .w-{25|50|75|100}
- .h-{25|50|75|100}
- .mw-100：max-width: 100%
- .mh-100：max-height: 100%

## Spacing

- 讓元件友善加上 margin 與 padding 的屬性
- 屬性-方向-尺寸 (組合技)：
  - {property}{sides}-{size} for xs
  - {property}{sides}-{breakpoint}-{size} for sm, md, lg and xl
  - sides 沒填就是 4 個方向都填
  - size：0 ~ 5，$spacer * {0|.25|.5|1|1.5|3}
    - $spacer 就是 1rem，16px
  - .m*-auto 可運用在 flex (很常用到)

## Text

- .text-justify：使其文字對齊
  - [文字對齊官網範例](http://bootstrap.hexschool.com/docs/4.0/utilities/text/#text-alignment)
- .text-left
- .text-center
- .text-right
- .text-{sm|md|lg|xl}-{left|center|right} 有包含不同的中斷點
- .text-nowrap：使文字不會換行
- .text-truncate：超過空間文字用...替代，不過內容要設定寬度才會有效
- .text-lowercase
- .text-uppercase
- .text-capitalize：字母首字改大寫
- .text-weight-bold
- .text-weight-normal
- .text-italic：改成斜體字

## vertical-align

不同的垂直對齊方法，很容易用在表格上

- .align-baseline：對齊文字基準線
- .align-top
- .align-middle
- .align-bottom
- .align-text-top：圖片套用，其他文字會對其頂部
- .align-text-bottom：圖片套用，其他文字會對齊底部

## Visibility

會讓物件消失，但空間保留

- .visible
- .invisible
