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
  <div class="card-body"> <!-- 加入一個上下左右 padding -->
      <h4 class="card-title"></h4> <!-- 調整間距 -->
      <h6 class="card-subtitle"></h6> <!-- 調整間距 -->
      <p class="card-text"></p> <!-- 最後一個會有縮小下距 -->
      <a href="#" class="card-link"></a>
  </div>
</div>
```

### 結構 2

```html
<div class="card">
  <div class="card-header"></div> <!-- 上灰底，切上方圓角 -->
  <div class="card-body">
    <div class="card-title"></div>
    <div class="catd-text"></div>
    <a href="#" class="card-link"></a>
  </div>
  <div class="card-footer"></div> <!-- 下灰底，切下方圓角 -->
</div>
```

### 結構 3

卡片式導覽元件。參考[範例](http://bootstrap.hexschool.com/docs/4.0/components/card/#navigation)

```html
<div class="card">
  <div class="card-header">
    <ul class="nav nav-tabs card-header-tabs">
      <li class="nav-item">
        <a href="#" class="nav-link"></a>
      </li>
      <li class="nav-item">
        <a href="#" class="nav-link"></a>
      </li>
    </ul>
  </div>
  <div class="card-body"></div>
</div>
```

### 結構 4

導覽元件，片狀的。參考[範例](http://bootstrap.hexschool.com/docs/4.0/components/card/#navigation)

```html
<div class="card">
  <div class="card-header">
    <ul class="nav nav-pills card-header-pills">
      <li class="nav-item">
        <a href="#" class="nav-link"></a>
      </li>
      <li class="nav-item">
        <a href="#" class="nav-link"></a>
      </li>
    </ul>
  </div>
  <div class="card-body"></div>
</div>
```

### 結構 5

文字覆蓋在圖片上面 (要注意顏色搭配，預設白色文字作搭配)

```html
<div class="card">
  <img src="" alt="" class="card-img">
  <div class="card-img-overlay">
    <h4 class="card-title"></h4>
    <p class="card-text"></p>
    <p class="card-text"></p>
  </div>
</div>
```

### 結構 6

卡片群組 1

```html
<div class="card-group">
  <div class="card"></div>
  <div class="card"></div>
  <div class="card"></div>
</div>
```

### 結構 7

卡片群組 2，與 1 的差別就是 2 有加上 gutter

```html
<div class="card-deck">
  <div class="card"></div>
  <div class="card"></div>
  <div class="card"></div>
</div>
```

### 結構 8

卡片欄，可容納 card 數量非常多。是瀑布流的排版方式，由上而下由左至右的新 CSS
排法。顯示可直接看[官網範例](https://getbootstrap.com/docs/4.0/components/card/#card-columns)

```html
<div class="card-columns">
  <div class="card"></div>
  <div class="card"></div>
  <div class="card"></div>
</div>
```

## Carousel

輪播插件，結構：

```html
<div id="carouselExampleIndicators" class="carousel slide" data-ride="carousel">
  <ol class="carousel-indicators">
    <li data-target="#carouselExampleIndicators" data-slide-to="0" class="active"></li>
    <li data-target="#carouselExampleIndicators" data-slide-to="1"></li>
    <li data-target="#carouselExampleIndicators" data-slide-to="2"></li>
  </ol>
  <div class="carousel-inner">
    <div class="carousel-item active">
      <img class="d-block w-100" src="..." alt="First slide">
    </div>
    <div class="carousel-item">
      <img class="d-block w-100" src="..." alt="Second slide">
    </div>
    <div class="carousel-item">
      <img class="d-block w-100" src="..." alt="Third slide">
    </div>
  </div>
  <a class="carousel-control-prev" href="#carouselExampleIndicators" role="button" data-slide="prev">
    <span class="carousel-control-prev-icon" aria-hidden="true"></span>
    <span class="sr-only">Previous</span>
  </a>
  <a class="carousel-control-next" href="#carouselExampleIndicators" role="button" data-slide="next">
    <span class="carousel-control-next-icon" aria-hidden="true"></span>
    <span class="sr-only">Next</span>
  </a>
</div>
```

這樣會是三個在輪播，有往前往後箭頭，下方還有底線的指標 (這兩個要記得需要外層
.carousel 的元素 #id 做 data-target、href 屬性搭配)

包含字幕的話加上 .carousel-caption 在 .carousel-item

```html
<div class="carousel-item">
  <img src="..." alt="...">
  <div class="carousel-caption d-none d-md-block">
    <h5>...</h5>
    <p>...</p>
  </div>
</div>
```

在實際案例中，會運用到輪播事件來做計數器的運算 (or 為效能提升而做的分頁機制)

```javascript
$('#myCarousel').on('slide.bs.carousel', function () {
  // do something…
})
```

所有輪播事件都在輪播本身 (即 `<div class="carousel">`) 下被觸發

有輪播立即觸發與輪播完成切換觸發的兩種事件：

- slide.bs.carousel
- slid.bs.carousel

## Collapse

折疊 JavaScript 套件，有三個狀態 (用 JavaScript 作切換)：

- .collapse：隱藏套件
- .callapsing：套用轉換中的動態效果
- .callapse.show：顯示內容

連結要使用 href 屬性指定 .collapse 元素的 id，按鈕則是 data-target 屬性。而
data-toggle="callapse" 則都需要設置

```html
<p>
  <a class="btn btn-primary" data-toggle="collapse" href="#collapseExample" role="button" aria-expanded="false" aria-controls="collapseExample">
    Link with href
  </a>
  <button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#collapseExample" aria-expanded="false" aria-controls="collapseExample">
    Button with data-target
  </button>
</p>
<div class="collapse" id="collapseExample">
  <div class="card card-body">
    Anim pariatur cliche reprehenderit, enim eiusmod high life accusamus terry richardson ad squid. Nihil anim keffiyeh helvetica, craft beer labore wes anderson cred nesciunt sapiente ea proident.
  </div>
</div>
```

data-target 也可指定 .collapse 元素的 class，就可一次折疊多個 (看第三個 button)

```html
<p>
  <a class="btn btn-primary" data-toggle="collapse" href="#multiCollapseExample1" role="button" aria-expanded="false" aria-controls="multiCollapseExample1">Toggle first element</a>
  <button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#multiCollapseExample2" aria-expanded="false" aria-controls="multiCollapseExample2">Toggle second element</button>
  <button class="btn btn-primary" type="button" data-toggle="collapse" data-target=".multi-collapse" aria-expanded="false" aria-controls="multiCollapseExample1 multiCollapseExample2">Toggle both elements</button>
</p>
<div class="row">
  <div class="col">
    <div class="collapse multi-collapse" id="multiCollapseExample1">
      <div class="card card-body">
        Anim pariatur cliche reprehenderit, enim eiusmod high life accusamus terry richardson ad squid. Nihil anim keffiyeh helvetica, craft beer labore wes anderson cred nesciunt sapiente ea proident.
      </div>
    </div>
  </div>
  <div class="col">
    <div class="collapse multi-collapse" id="multiCollapseExample2">
      <div class="card card-body">
        Anim pariatur cliche reprehenderit, enim eiusmod high life accusamus terry richardson ad squid. Nihil anim keffiyeh helvetica, craft beer labore wes anderson cred nesciunt sapiente ea proident.
      </div>
    </div>
  </div>
</div>
```

可搭配卡片元件，展開預設折疊行為以創建摺疊功能 (口風琴折疊)
。[官網範例](https://getbootstrap.com/docs/4.0/components/collapse/#accordion-example)

```html
<div id="accordion" role="tablist">
  <div class="card">
    <div class="card-header" role="tab" id="headingOne">
      <h5 class="mb-0">
        <a data-toggle="collapse" href="#collapseOne" role="button" aria-expanded="true" aria-controls="collapseOne">
          Collapsible Group Item #1
        </a>
      </h5>
    </div>
    
    <div id="collapseOne" class="collapse show" role="tabpanel" aria-labelledby="headingOne" data-parent="#accordion">
      <div class="card-body">
        Anim pariatur cliche reprehenderit, enim eiusmod high life accusamus terry richardson ad squid. 3 wolf moon officia aute, non cupidatat skateboard dolor brunch. Food truck quinoa nesciunt laborum eiusmod. Brunch 3 wolf moon tempor, sunt aliqua put a bird on it squid single-origin coffee nulla assumenda shoreditch et. Nihil anim keffiyeh helvetica, craft beer labore wes anderson cred nesciunt sapiente ea proident. Ad vegan excepteur butcher vice lomo. Leggings occaecat craft beer farm-to-table, raw denim aesthetic synth nesciunt you probably haven't heard of them accusamus labore sustainable VHS.
      </div>
    </div>
  </div>
  <div class="card">
    <div class="card-header" role="tab" id="headingTwo">
      <h5 class="mb-0">
        <a class="collapsed" data-toggle="collapse" href="#collapseTwo" role="button" aria-expanded="false" aria-controls="collapseTwo">
          Collapsible Group Item #2
        </a>
      </h5>
    </div>
    <div id="collapseTwo" class="collapse" role="tabpanel" aria-labelledby="headingTwo" data-parent="#accordion">
      <div class="card-body">
        Anim pariatur cliche reprehenderit, enim eiusmod high life accusamus terry richardson ad squid. 3 wolf moon officia aute, non cupidatat skateboard dolor brunch. Food truck quinoa nesciunt laborum eiusmod. Brunch 3 wolf moon tempor, sunt aliqua put a bird on it squid single-origin coffee nulla assumenda shoreditch et. Nihil anim keffiyeh helvetica, craft beer labore wes anderson cred nesciunt sapiente ea proident. Ad vegan excepteur butcher vice lomo. Leggings occaecat craft beer farm-to-table, raw denim aesthetic synth nesciunt you probably haven't heard of them accusamus labore sustainable VHS.
      </div>
    </div>
  </div>
  <div class="card">
    <div class="card-header" role="tab" id="headingThree">
      <h5 class="mb-0">
        <a class="collapsed" data-toggle="collapse" href="#collapseThree" role="button" aria-expanded="false" aria-controls="collapseThree">
          Collapsible Group Item #3
        </a>
      </h5>
    </div>
    <div id="collapseThree" class="collapse" role="tabpanel" aria-labelledby="headingThree" data-parent="#accordion">
      <div class="card-body">
        Anim pariatur cliche reprehenderit, enim eiusmod high life accusamus terry richardson ad squid. 3 wolf moon officia aute, non cupidatat skateboard dolor brunch. Food truck quinoa nesciunt laborum eiusmod. Brunch 3 wolf moon tempor, sunt aliqua put a bird on it squid single-origin coffee nulla assumenda shoreditch et. Nihil anim keffiyeh helvetica, craft beer labore wes anderson cred nesciunt sapiente ea proident. Ad vegan excepteur butcher vice lomo. Leggings occaecat craft beer farm-to-table, raw denim aesthetic synth nesciunt you probably haven't heard of them accusamus labore sustainable VHS.
      </div>
    </div>
  </div>
</div>
```

## Dropdowns

下拉選單的 JavaScript 套件，按鈕觸發隱藏選單

- 可在 .dropdown 元素加上 .dropup 使其向上展開選單，空間不夠會自動切換向上或向下

### 結構 1

```html
<div class="dropdown"> <!-- 定位使用 -->
  <button class="dropdown-toggle" data-toggle="dropdown">Action</button>
  <div class="dropdown-menu">
    <h6 class="dropdown-header">Dropdown header</h6>
    <a href="#" class="dropdown-item"></a>
    <a href="#" class="dropdown-item"></a>
    <a href="#" class="dropdown-item"></a>
    <div class="dropdown-divider"></div> <!-- 分隔線 -->
    <a href="#" class="dropdown-item"></a>
  </div>
</div>
```

### 結構 2

```html
<div class="btn-group">
  <button>Action</button>
  <button class="dropdown-toggle dropdown-toggle-split" data-toggle="dropdown"></button>
  <div class="dropdown-menu">
    <h6 class="dropdown-header">Dropdown header</h6>
    <a href="#" class="dropdown-item">item1</a>
    <a href="#" class="dropdown-item">item2</a>
    <a href="#" class="dropdown-item">item3</a>
    <div class="dropdown-divider"></div>
    <a href="#" class="dropdown-item"></a>item4</div>
</div>
```

這樣箭頭會比較有協調與平均，寬度不會太寬

### 結構 3

可客製化內容，沒要求你一定要用選單。畫面詳見[官網](http://bootstrap.hexschool.com/docs/4.0/components/dropdowns/#menu-forms)

```html
<div class="dropdown-menu">
  <form class="px-4 py-3">
    <div class="form-group">
      <label for="exampleDropdownFormEmail1">Email address</label>
      <input type="email" class="form-control" id="exampleDropdownFormEmail1" placeholder="email@example.com">
    </div>
    <div class="form-group">
      <label for="exampleDropdownFormPassword1">Password</label>
      <input type="password" class="form-control" id="exampleDropdownFormPassword1" placeholder="Password">
    </div>
    <div class="form-check">
      <input type="checkbox" class="form-check-input" id="dropdownCheck">
      <label class="form-check-label" for="dropdownCheck">
        Remember me
      </label>
    </div>
    <button type="submit" class="btn btn-primary">Sign in</button>
  </form>
  <div class="dropdown-divider"></div>
  <a class="dropdown-item" href="#">New around here? Sign up</a>
  <a class="dropdown-item" href="#">Forgot password?</a>
</div>
```

## Form

- class 應該要套在哪一個標籤上
- HTML5 表單觀念

### 基本結構

```html
<form>
  <div class="form-group"> <!-- 包 input，調整間距 -->
    <label for="exampleInputEmail1">Email address</label>
    <input type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" placeholder="Enter email">
    <small id="emailHelp" class="form-text text-muted">We'll never share your email with anyone else.</small> <!-- 調整間距 -->
  </div>
  <div class="form-group">
    <label for="exampleInputPassword1">Password</label>
    <input type="password" class="form-control" id="exampleInputPassword1" placeholder="Password">
  </div>
  <div class="form-group">
    <label for="exampleSelect1">Select</label>
    <select name="exampleSelect1" id="exampleSelect1" class="form-control" multiple>
      <option value="1">1</option>
      <option value="2">2</option>
      <option value="3">3</option>
      <option value="4">4</option>
      <option value="5">5</option>
    </select>
  </div>
  <div class="form-group">
    <label for="exampleTextarea1">Textarea</label>
    <textarea class="form-control" id="exampleTextarea1"></textarea>
  </div>
  <div class="form-check"> <!-- 要 disabled 建議也加 class="disabled" 在這裡，就可文字也呈現灰色 -->
    <input type="checkbox" class="form-check-input" id="exampleCheck1">
    <label class="form-check-label" for="exampleCheck1">Check me out</label>
  </div>
  <button type="submit" class="btn btn-primary">Submit</button>
</form>
```

上述範例檔僅 checkbox 元素是使用 .form-check

- 可用 .form-control-{sm||lg}，來做不同的表單控制項的尺寸
- 只能讀不能修改，加 readonly 在 input 的屬性上
- checkbox、radio 想要水平排列，可在 .form-check 元素加 .form-check-inline
- 有運用 grid，可用 .form-row 取代 .row，gutter 會拉小

    ```html
    <div class="form-row">
      <div class="form-group col-md-6"></div>
      <div class="form-group col-md-6"></div>
    </div>
    ```

- 有運用 grid，可用 .col-form-label 使其排版正確 (以下範例 label 字會置中)

    ```html
    <form>
      <div class="form-group row">
        <label for="inputEmail3" class="col-sm-2 col-form-label">Email</label>
        <div class="col-sm-10">
          <input type="email" class="form-control" id="inputEmail3" placeholder="Email">
        </div>
      </div>
      <div class="form-group row">
        <label for="inputPassword3" class="col-sm-2 col-form-label">Password</label>
        <div class="col-sm-10">
          <input type="password" class="form-control" id="inputPassword3" placeholder="Password">
        </div>
      </div>
      <fieldset class="form-group">
        <div class="row">
          <legend class="col-form-label col-sm-2 pt-0">Radios</legend>
          <div class="col-sm-10">
            <div class="form-check">
              <input class="form-check-input" type="radio" name="gridRadios" id="gridRadios1" value="option1" checked>
              <label class="form-check-label" for="gridRadios1">
                First radio
              </label>
            </div>
            <div class="form-check">
              <input class="form-check-input" type="radio" name="gridRadios" id="gridRadios2" value="option2">
              <label class="form-check-label" for="gridRadios2">
                Second radio
              </label>
            </div>
            <div class="form-check disabled">
              <input class="form-check-input" type="radio" name="gridRadios" id="gridRadios3" value="option3" disabled>
              <label class="form-check-label" for="gridRadios3">
                Third disabled radio
              </label>
            </div>
          </div>
        </div>
      </fieldset>
      <div class="form-group row">
        <div class="col-sm-2">Checkbox</div>
        <div class="col-sm-10">
          <div class="form-check">
            <input class="form-check-input" type="checkbox" id="gridCheck1">
            <label class="form-check-label" for="gridCheck1">
              Example checkbox
            </label>
          </div>
        </div>
      </div>
      <div class="form-group row">
        <div class="col-sm-10">
          <button type="submit" class="btn btn-primary">Sign in</button>
        </div>
      </div>
    </form>
    ```

- 可在 form 元素套上 .form-inline 成為行內表單，變成水平一排
  - 將標籤轉為 flex 屬性，裡面的屬性必要時用 utilities 的 spacing 做調整

  ```html
  <form class="form-inline">
    <label class="sr-only" for="inlineFormInputName2">Name</label>
    <input type="text" class="form-control mb-2 mr-sm-2" id="inlineFormInputName2" placeholder="Jane Doe">
  
    <label class="sr-only" for="inlineFormInputGroupUsername2">Username</label>
    <div class="input-group mb-2 mr-sm-2">
      <div class="input-group-prepend">
        <div class="input-group-text">@</div>
      </div>
      <input type="text" class="form-control" id="inlineFormInputGroupUsername2" placeholder="Username">
    </div>
  
    <div class="form-check mb-2 mr-sm-2">
      <input class="form-check-input" type="checkbox" id="inlineFormCheck">
      <label class="form-check-label" for="inlineFormCheck">
        Remember me
      </label>
    </div>
  
    <button type="submit" class="btn btn-primary mb-2">Submit</button>
  </form>
  ```

- disabled 屬性可加表單元素或外層做整個 disable
- 自訂樣式

    ```html
    <div class="custom-control custom-checkbox">
      <input type="checkbox" class="custom-control-input" id="customCheck1">
      <label class="custom-control-label" for="customCheck1">Check this custom checkbox</label>
    </div>
    
    <div class="custom-control custom-radio">
      <input type="radio" id="customRadio1" name="customRadio" class="custom-control-input">
      <label class="custom-control-label" for="customRadio1">Toggle this custom radio</label>
    </div>
    <div class="custom-control custom-radio">
      <input type="radio" id="customRadio2" name="customRadio" class="custom-control-input">
      <label class="custom-control-label" for="customRadio2">Or toggle this other custom radio</label>
    </div>
    ```

### 表單驗證

- 分 server 驗證與 client 驗證
- client 使用偽元素 :invalid 與 :valid 來做驗證樣式，分別是紅色與綠色
- server 則使用 class 手動加入 .is-invalid 與 .is-valid 來替換上面那兩個偽元素
- .invalid-feedback 用來做錯誤回饋用的區塊 class
- form 要配 id 以及加上 novalidate 的屬性，代表該表單未驗證，這樣未驗證
  .invalid-feedback 的區塊內文字不會顯示
- 要驗證的元素一定要加 required 屬性，否則驗證失敗樣式結果是呈現綠色的
- 啟用瀏覽器驗證用 bootstrap [官網的範例](https://getbootstrap.com/docs/4.0/components/forms/#validation)就可以使用了

```html
<form id="needs-validation" novalidate>
  <div class="form-row">
    <div class="col-md-4 mb-3">
      <label for="validationCustom01">First name</label>
      <input type="text" class="form-control" id="validationCustom01" placeholder="First name" value="Mark" required>
    </div>
    <div class="col-md-4 mb-3">
      <label for="validationCustom02">Last name</label>
      <input type="text" class="form-control" id="validationCustom02" placeholder="Last name" value="Otto" required>
    </div>
    <div class="col-md-4 mb-3">
      <label for="validationCustomUsername">Username</label>
      <div class="input-group">
        <div class="input-group-prepend">
          <span class="input-group-text" id="inputGroupPrepend">@</span>
        </div>
        <input type="text" class="form-control" id="validationCustomUsername" placeholder="Username" aria-describedby="inputGroupPrepend" required>
        <div class="invalid-feedback">
          Please choose a username.
        </div>
      </div>
    </div>
  </div>
  <div class="form-row">
    <div class="col-md-6 mb-3">
      <label for="validationCustom03">City</label>
      <input type="text" class="form-control" id="validationCustom03" placeholder="City" required>
      <div class="invalid-feedback">
        Please provide a valid city.
      </div>
    </div>
    <div class="col-md-3 mb-3">
      <label for="validationCustom04">State</label>
      <input type="text" class="form-control" id="validationCustom04" placeholder="State" required>
      <div class="invalid-feedback">
        Please provide a valid state.
      </div>
    </div>
    <div class="col-md-3 mb-3">
      <label for="validationCustom05">Zip</label>
      <input type="text" class="form-control" id="validationCustom05" placeholder="Zip" required>
      <div class="invalid-feedback">
        Please provide a valid zip.
      </div>
    </div>
  </div>
  <button class="btn btn-primary" type="submit">Submit form</button>
</form>
    
<script>
// Example starter JavaScript for disabling form submissions if there are invalid fields
(function() {
  'use strict';
    
  window.addEventListener('load', function() {
    var form = document.getElementById('needs-validation');
    form.addEventListener('submit', function(event) {
      if (form.checkValidity() === false) {
        event.preventDefault();
        event.stopPropagation();
      }
      form.classList.add('was-validated');
    }, false);
  }, false);
})();
</script>
```

## Input group

與 button group 很像，for input 標籤用，但多了一個 .input-group-prepend
class 可作為文字或輸入標籤用的組合項目。效果可看[官網](https://getbootstrap.com/docs/4.0/components/input-group/)

```html
<div class="input-group mb-3">
  <div class="input-group-prepend">
    <div class="input-group-text">
      <input type="checkbox" aria-label="Checkbox for following text input">
    </div>
  </div>
  <input type="text" class="form-control" aria-label="Text input with checkbox">
</div>
```

可在 .input-group 加上不同尺寸

- .input-group-sm
- .input-group-lg

可使用 dropdown

```html
<div class="input-group mb-3">
  <div class="input-group-prepend">
    <button class="btn btn-outline-secondary dropdown-toggle" type="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">Dropdown</button>
    <div class="dropdown-menu">
      <a class="dropdown-item" href="#">Action</a>
      <a class="dropdown-item" href="#">Another action</a>
      <a class="dropdown-item" href="#">Something else here</a>
      <div role="separator" class="dropdown-divider"></div>
      <a class="dropdown-item" href="#">Separated link</a>
    </div>
  </div>
  <input type="text" class="form-control" aria-label="Text input with dropdown button">
</div>
```

## Jumbotron

廣告大屏幕，大塊的關鍵行銷區域看板

```html
<div class="jumbotron">
  <h1 class="display-4">Hello, world!</h1>
  <p class="lead">This is a simple hero unit, a simple jumbotron-style component for calling extra attention to featured content or information.</p>
  <hr class="my-4">
  <p>It uses utility classes for typography and spacing to space content out within the larger container.</p>
  <p class="lead">
    <a class="btn btn-primary btn-lg" href="#" role="button">Learn more</a>
  </p>
</div>
```

不要有圓角，則在 .jumbotron 元素加上 .jumbotron-fluid，寬度也會更為寬廣一點

## List group

列表清單群組

### 結構 1

```html
<ul class="list-group">
  <li class="list-group-item active"></li>
  <li class="list-group-item disabled"></li>
  <li class="list-group-item"></li>
  <li class="list-group-item"></li>
  <li class="list-group-item"></li>
</ul>
```

### 結構 2

結構 1 就不能夠點擊了，需要點擊可用下面結構，list-group-item-action 類別使其有
hover 效果

```html
<div class="list-group">
  <a href="#" class="list-group-item list-group-item-action active">
    <!-- 不僅純放文字，可放自訂內容結構 -->
  </a>
  <a href="#" class="list-group-item list-group-item-action disabled"></a>
  <a href="#" class="list-group-item list-group-item-action"></a>
  <a href="#" class="list-group-item list-group-item-action"></a>
  <a href="#" class="list-group-item list-group-item-action"></a>
</div>
```

.list-group-item 元素也可以是 `<button>`

在 .list-group-item 元素加入 .list-group-item-{color} 可替換不同色彩

### 結構 3

可製作成 tab 化的列表群組與內容

```html
<div class="row">
  <div class="col-4">
    <div class="list-group" id="list-tab" role="tablist">
      <a class="list-group-item list-group-item-action active" id="list-home-list" data-toggle="list" href="#list-home" role="tab" aria-controls="home">Home</a>
      <a class="list-group-item list-group-item-action" id="list-profile-list" data-toggle="list" href="#list-profile" role="tab" aria-controls="profile">Profile</a>
      <a class="list-group-item list-group-item-action" id="list-messages-list" data-toggle="list" href="#list-messages" role="tab" aria-controls="messages">Messages</a>
      <a class="list-group-item list-group-item-action" id="list-settings-list" data-toggle="list" href="#list-settings" role="tab" aria-controls="settings">Settings</a>
    </div>
  </div>
  <div class="col-8">
    <div class="tab-content" id="nav-tabContent">
      <div class="tab-pane fade show active" id="list-home" role="tabpanel" aria-labelledby="list-home-list">...</div>
      <div class="tab-pane fade" id="list-profile" role="tabpanel" aria-labelledby="list-profile-list">...</div>
      <div class="tab-pane fade" id="list-messages" role="tabpanel" aria-labelledby="list-messages-list">...</div>
      <div class="tab-pane fade" id="list-settings" role="tabpanel" aria-labelledby="list-settings-list">...</div>
    </div>
  </div>
</div>
```

tab-pane 是分頁的效果，裡面都有帶 id 與 .list-group-item 的 a 元素 href 屬性作切換對應

## Modal

互動視窗，是常用的元件 (要使用的話直接從官網複製結構再調整最輕鬆)。以下是基本結構：

```html
<!-- Button trigger modal -->
<button type="button" class="btn btn-primary" data-toggle="modal" data-target="#exampleModal">
  Launch demo modal
</button>

<!-- Modal -->
<div class="modal fade" id="exampleModal" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
  <div class="modal-dialog" role="document"> <!-- 可加入 .modal-sm or .modal-lg class 做尺寸的調整 -->
    <div class="modal-content"> <!-- 要使用從這裡以下去做修改就好，不要修改外部的 -->
      <div class="modal-header">
        <h5 class="modal-title" id="exampleModalLabel">Modal title</h5>
        <button type="button" class="close" data-dismiss="modal" aria-label="Close">
          <span aria-hidden="true">&times;</span>
        </button>
      </div>
      <div class="modal-body">
        ...
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
        <button type="button" class="btn btn-primary">Save changes</button>
      </div>
    </div>
  </div>
</div>
```

## Navs

導覽元件，結構可使用 `ul>li` or `nav>a`：

```html
<ul class="nav">
  <li class="nav-item">
    <a class="nav-link active" href="#">Active</a>
  </li>
  <li class="nav-item">
    <a class="nav-link" href="#">Link</a>
  </li>
  <li class="nav-item">
    <a class="nav-link" href="#">Link</a>
  </li>
  <li class="nav-item">
    <a class="nav-link disabled" href="#">Disabled</a>
  </li>
</ul> 
```

```html
<nav class="nav">
  <a class="nav-link active" href="#">Active</a>
  <a class="nav-link" href="#">Link</a>
  <a class="nav-link" href="#">Link</a>
  <a class="nav-link disabled" href="#">Disabled</a>
</nav>
```

可使用 flex 改變它的排版方式，e.g. .nav 加上 justify-content-end 等

.nav 元素可加上 .nav-tab 或 .nav-pills 改變樣式

JavaScript 可調整成頁籤切換功能 (也可換 pills 模式)：

```html
<ul class="nav nav-tabs" id="myTab" role="tablist">
  <li class="nav-item">
    <a class="nav-link active" id="home-tab" data-toggle="tab" href="#home" role="tab" aria-controls="home" aria-selected="true">Home</a>
  </li>
  <li class="nav-item">
    <a class="nav-link" id="profile-tab" data-toggle="tab" href="#profile" role="tab" aria-controls="profile" aria-selected="false">Profile</a>
  </li>
  <li class="nav-item">
    <a class="nav-link" id="contact-tab" data-toggle="tab" href="#contact" role="tab" aria-controls="contact" aria-selected="false">Contact</a>
  </li>
</ul>
<div class="tab-content" id="myTabContent">
  <div class="tab-pane fade show active" id="home" role="tabpanel" aria-labelledby="home-tab">...</div>
  <div class="tab-pane fade" id="profile" role="tabpanel" aria-labelledby="profile-tab">...</div>
  <div class="tab-pane fade" id="contact" role="tabpanel" aria-labelledby="contact-tab">...</div>
</div>
```

## Navbar

也是使用率非常高，一般是 .navbar 加上 .navbar-{color} 與 bg-{color} 做搭配，以下是基本結構：

```html
<nav class="navbar navbar-light bg-light">
  <a href="#" class="navbar-brand">Navbar</a>
</nav>
<nav class="navbar navbar-light bg-light">
  <span class="navbar-brand mb-0 h1">Navbar</span>
</nav>
```

.navbar 元素可加上 .navbar-expand-{sm|lg}，該指定尺寸以上會顯示出來，其他是隱藏

漢堡選單：

```html
<nav class="navbar navbar-expand-lg navbar-light bg-light">
  <a class="navbar-brand" href="#">Navbar</a>
  <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
    <span class="navbar-toggler-icon"></span>
  </button>
 
  <div class="collapse navbar-collapse" id="navbarSupportedContent">
    <ul class="navbar-nav mr-auto">
      <li class="nav-item active">
        <a class="nav-link" href="#">Home <span class="sr-only">(current)</span></a>
      </li>
      <li class="nav-item">
        <a class="nav-link" href="#">Link</a>
      </li>
      <li class="nav-item dropdown">
        <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
          Dropdown
        </a>
        <div class="dropdown-menu" aria-labelledby="navbarDropdown">
          <a class="dropdown-item" href="#">Action</a>
          <a class="dropdown-item" href="#">Another action</a>
          <div class="dropdown-divider"></div>
          <a class="dropdown-item" href="#">Something else here</a>
        </div>
      </li>
      <li class="nav-item">
        <a class="nav-link disabled" href="#">Disabled</a>
      </li>
    </ul>
    <form class="form-inline my-2 my-lg-0">
      <input class="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search">
      <button class="btn btn-outline-success my-2 my-sm-0" type="submit">Search</button>
    </form>
  </div>
</nav>
```

- 如果要加入表單記得加入 .form-inline
- 可用 fixed-top、fixed-bottom、sticky-top 做 navbar 不同定位


