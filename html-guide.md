# HTML Guide

---

HTML规范指南。

---

## 文档目录

1. [代码风格](#1-代码风格)
2. [属性](#2-属性)
3. [标签](#3-标签)
4. [head设定](#4-head设定)
5. [图片](#5-图片)
6. [表单](#6-表单)
7. [注释](#7-注释)


## 1 代码风格

### 1.1 缩进
**【强制】**使用 *2* 个空格作为一个缩进层级，不允许使用 *4* 个空格或 *tab* 字符；


## 2 属性

### 2.1 属性引号

**【强制】**对于属性的定义使用双引号，不允许使用单引号，不允许不使用引号；

示例：

```html
<!-- Not so great -->
<img class='avatar' src="./img/avatar.png" alt='avatar'>

<!-- Better -->
<img class="avatar" src="./img/avatar.png" alt="avatar">
```

### 2.2 属性大小写

**【强制】**属性名应该小写，不允许大写或大小写混合；

示例：

```html
<!-- Not so great -->
<table cellSpacing="0">...</table>

<!-- Better -->
<table cellspacing="0">...</table>
```

### 2.3 属性布尔值

**【建议】**布尔类型的属性，建议不添加属性值，至少同一项目要保持一致；

示例：

```html
<input type="text" disabled>
<input type="checkbox" checked>
```

### 2.4 属性声明顺序

**【建议】**HTML 属性建议尽量按照以下给出的顺序依次排列，确保代码的易读性。

* `class`
* `id`, `name`
* `data-*`
* `src`, `for`, `type`, `href`
* `title`, `alt`
* `aria-*`, `role`

class 用于标识高度可复用组件，因此应该排在首位。id 用于标识具体组件，应当谨慎使用（例如，页面内的书签），建议预留更多的id命名给技术，因此排在第二位。

```html
<a class="..." id="..." data-modal="toggle" href="#">Example link</a>

<input class="form-control" type="text">

<img src="..." alt="...">
```

### 2.5 自定义属性

**【建议】**使用自定义属性作为JS的hook，建议以`data-`为前缀；

示例：

```html
<input data-role="getPic" type="button">
```

### 2.6 链接属性

**【强制】**禁止 `a` 标签的 `href` 取值为空或不写 `href` 属性，重构时默认可用 `#` 代替；

如果不需要使用链接功能，请不要使用不带 `href` 的 `a` 标签，既不符合标签的语义，也可能会产生未知的兼容性问题；

示例：

```html
<!-- Not so great -->
<a href="" title="title">欢聚时代</a>
<a class="xxx">欢聚时代</a>

<!-- Better -->
<a href="#" title="title">欢聚时代</a>
```


**[[⬆]](#)**


## 3 标签

### 3.1 标签大小写

**【强制】**标签名应该小写，不允许大写或大小写混合；

示例：

```html
<!-- Not so great -->
<DIV clsss="xxx">...</DIV>

<!-- Better -->
<div clsss="xxx">...</div>
```

### 3.2 标签自闭合

**【建议】**对于无需自闭合的标签，建议不自闭合，至少同一项目要保持一致；

常见无需自闭合标签有`input`、`img`、`br`、`hr`等

示例：

```html
<input type="checkbox" value="1">
```

### 3.3 标签嵌套

**【强制】**标签使用必须符合标签嵌套规则；

例如：内联元素不能嵌套块元素，`<p>`元素和`<h1~6>`元素不能嵌套块元素等，详见 [Allowed nesting of elements in HTML 4 Strict (and XHTML 1.0 Strict) ](http://www.cs.tut.fi/~jkorpela/html/strict.html) 与 [HTML5 Content models](http://www.w3.org/TR/2011/WD-html5-20110525/content-models.html);

**【建议】**实用为王，尽量遵循 HTML 标准和语义，但是不要以牺牲实用性为代价。任何时候都要尽量使用最少的标签并保持最小的复杂度。

```html
<!-- Not so great -->
<span class="avatar">
  <img src="...">
</span>

<!-- Better -->
<img class="avatar" src="...">
```

### 3.4 避免过时标签

**【强制】**不允许使用过时的旧标签，请使用新标签或者CSS代替：

<ul>
    <li><del><code>acronym</code></del> → <ins><code>abbr</code></ins></li>
    <li><del><code>applet</code></del> → <ins><code>object</code></ins></li>
    <li><del><code>b</code></del> → <ins><code>strong</code></ins></li>
    <li><del><code>dir</code></del> → <ins><code>ul</code></ins></li>
    <li><del><code>strike</code></del> → <ins><code>del</code></ins></li>
    <li><del><code>basefont</code></del></li>
    <li><del><code>big</code></del></li>
    <li><del><code>center</code></del></li>
    <li><del><code>font</code></del></li>
    <li><del><code>isindex</code></del></li>
    <li><del><code>tt</code></del></li>
    <li><del><code>u</code></del></li>
</ul>

请参详：http://www.w3schools.com/tags/


**[[⬆]](#)**


## 4 head设定

### 4.1 doctype

**【强制】**doctype使用 HTML5 的 doctype 来启用标准模式。

其中 `doctype` 建议使用大写的 DOCTYPE； [关于doctype该使用大写还是小写的讨论](http://stackoverflow.com/questions/7020961/uppercase-or-lowercase-doctype)

示例：

```html
<!DOCTYPE html>
```

### 4.2 页面编码

**【强制】**页面必须明确指定字符编码，让浏览器快速确定适合网页内容的渲染方式。指定字符编码的 meta 必须是 head 的第一个直接子元素。建议使用无 BOM 的 UTF-8 编码；

示例：

```html
<meta charset="UTF-8">
```

### 4.3 兼容模式

**【建议】**PC端启用 IE Edge 模式，并针对360浏览器启用webkit渲染模式；

示例：

```html
<meta http-equiv="X-UA-Compatible" content="IE=edge">
<meta name="renderer" content="webkit">
```

### 4.4 引入CSS

**【强制】**引入 CSS 时必须指明 rel="stylesheet"；

建议在 head 中引入页面需要的所有 CSS 资源，因为在页面渲染的过程中，新的CSS可能导致元素的样式重新计算和绘制，页面闪烁；

示例：

```html
<link rel="stylesheet" src="global.css">
```

### 4.5 引入JavaScript

**【建议】**JavaScript应当放在页面尾部；出于性能方面的考虑，如非必要，请遵守此条建议；

示例：

```html
<body>
    <!-- a lot of elements -->
    <script src="main.js"></script>
</body>
```

### 4.6 favicon

**【强制】**保证 `favicon` 可访问；

在未指定 favicon 时，大多数浏览器会请求 Web Server 根目录下的 favicon.ico 。为了保证favicon可访问，避免404，必须遵循以下两种方法之一：

1. 在 Web Server 根目录放置 favicon.ico 文件;
2. 使用 link 指定 favicon;

示例：

```html
<link type="image/x-icon" rel="shortcut icon" href="path/to/favicon.ico">
```

#### 附：工作流中默认的PC端head设定

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="renderer" content="webkit">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <meta name="Keywords" content="多玩游戏">
    <meta name="description" content="多玩游戏">
    <!-- a lot of elements -->
</head>
<body>
    <!-- a lot of elements -->
</body>
</html>
```

#### 附：工作流中默认的移动端head设定

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=0, minimum-scale=1.0, maximum-scale=1.0">
    <meta name="format-detection" content="telephone=no,address=no,email=no">
    <meta name="apple-itunes-app" content="app-id=myAppStoreID, affiliate-data=myAffiliateData, app-argument=myURL">
    <meta name="keywords" content="多玩游戏">
    <meta name="description" content="多玩游戏">
    <!-- a lot of elements -->
</head>
<body>
    <!-- a lot of elements -->
</body>
</html>
```
注意：当该项目有相关的app在app store中，设置meta`apple-itunes-app`，如上面最后一条，并填上对应的`app-id`。详细请看：[Promoting Apps with Smart App Banners](https://developer.apple.com/library/ios/documentation/AppleApplications/Reference/SafariWebContent/PromotingAppswithAppBanners/PromotingAppswithAppBanners.html)

更详细的meta属性设置可以参详：https://github.com/hzlzh/cool-head


**[[⬆]](#)**


## 5 图片

**【强制】**禁止 `img` 的 `src` 取值为空；延迟加载的图片也要增加默认的 `src`；

`src` 取值为空，会导致部分浏览器重新加载一次当前页面，参考 [Yahoo performance rules](https://developer.yahoo.com/performance/rules.html#emptysrc)

**【建议】**为重要图片添加 `alt` 属性；

可以提高图片加载失败时的用户体验。

**【建议】**添加 `width` 和 `height` 属性，以避免页面抖动；

**【建议】**有下载需求或者预期会灵活变动的图片采用 `img` 标签实现，无下载需求的图片采用 CSS 背景图实现；

* 用户头像、用户产生的图片等有潜在下载需求的图片，以 img 形式实现，能方便用户下载；
* 无下载需求的图片，比如：icon、背景、代码使用的图片等，尽可能采用 css 背景图实现。


**[[⬆]](#)**


## 6 表单

**【强制】**有文本标题的控件必须使用 `label` 标签将其与其标题相关联；

有两种方式：

1. 将控件置于 label 内;
2. label 的 for 属性指向控件的 id。

推荐使用第一种，减少不必要的 id。如果 DOM 结构不允许直接嵌套，则应使用第二种。

示例：

```html
<label><input name="confirm" type="checkbox" value="on"> 我已确认上述条款</label>

<label for="username">用户名：</label> <input id="username" name="username" type="checkbox">
```

**【建议】**尽量不要使用按钮类元素的 name 属性；

由于浏览器兼容性问题，使用按钮的 name 属性会带来许多难以发现的问题。具体情况可参考 [此文](http://w3help.org/zh-cn/causes/CM2001)；

**【建议】**在针对移动设备开发的页面时，根据内容类型指定输入框的 `type` 属性；

根据内容类型指定输入框类型，能获得能友好的输入体验。

示例：

```html
<input type="number" value="1">
```

**[[⬆]](#)**


## 7 注释

**【建议】**对**超过10行**的页面模块进行注释, 以降低开发人员的嵌套成本和后期的维护成本。建议使用结尾注释方式，例如：

当模块代码量较少时，可以省略 `start`。

```html
<!-- 文章内容 start -->
<section id="post">
   do some things...
</section>
<!-- 文章内容 end -->
```

或者标注模块的class或者id：
```html
<!-- #post start -->
<section id="post">
    do some things...
</section>
<!-- #post end -->
```

**[[⬆]](#)**


参考资料： 

1. [bootcss编码规范](http://codeguide.bootcss.com/)
2. [Google HTML编码规范](http://google-styleguide.googlecode.com/svn/trunk/htmlcssguide.xml)
3. [spec HTML编码规范](https://github.com/ecomfe/spec/blob/master/css-style-guide.md)
