# CSS Guide

---

CSS编码风格指南。

---

## 文档目录

1. [命名规范](#1-命名规范)
2. [代码风格](#2-代码风格)
3. [通用](#3-通用)
4. [值与单位](#4-值与单位)
5. [文本排版](#5-文本排版)
6. [变换与动画](#6-变换与动画)
7. [媒体查询](#7-媒体查询)
8. [兼容性](#8-兼容性)
9. [代码注释](#9-代码注释)

## 1 命名规范

该命名规范主要解决以下问题：

* 从类名可以清晰区分出其功能作用，使页面结构清晰【命名空间、标识符】；
* 以组件、模块的思想去写一个区块的结构，强化结构的模块化【BEM模块思想】；
* 减少多人合作、项目耦合等情况下的命名冲突【命名空间】；

### 1.1 命名思想

项目如果没使用样式局部作用域框架（如vue），则使用BEM命名规则。

**【强制】** 区块、模块、组件等一个整个的结构遵循BEM命名思想；

当你能确定组件内最后一级的结构不会再发生变化时，最后一级可省略类名，使用两层嵌套；

* `.block` 代表了更高级别的抽象或组件；
* `.block__element` 代表`.block`的后代，用于形成一个完整的`.block`的整体；
* `.is-` | `.has-` | `.ext-` 代表`.block`的修饰符，**不使用双中划线`--`**。

相关链接：

* [BEM—源自Yandex的CSS 命名方法论](http://segmentfault.com/a/1190000000391762)
* [BEM官网](http://bem.info/)


### 1.2 多单词连接

**【强制】** 用中划线连接多个单词，例如：`news-list`；

### 1.3 命名空间

**【推荐】** 在合适的地方使用命名空间；

* **状态**：以`is`为命名空间，**表示动态的、具有交互性质的状态**，例如：`.is-open`、`.is-active`、`.is-selected` 等；
* **组件**：以`ui`或者`mod`为命名空间，**表示可复用、移植的组件模块**，例如：`.ui-slider`、`.mod-drop-menu`等；
* **扩展**：以`ext`为命名空间，**表示对组件基类的视觉形态的扩展**，例如：`.ext-cover`等；

### 1.4 区块命名

**【推荐】** 一般区块都可以划分为头部、身体和尾部，因此建议给你的区块分别以 `hd`、`bd`、`ft`来划分；

示例：

```css
.ui-card__hd {
    margin: 0;
}

.ui-card__bd {
    margin: 0;
}

.ui-card__ft {
    margin: 0;
}
```

#### 附：命名示例

<img src="https://cloud.githubusercontent.com/assets/1295348/7456687/0643f254-f2b9-11e4-9b14-f1b36257f9a3.jpg" alt="命名示例" width="600">


**[[⬆]](#)**


## 2 代码风格

### 2.1 缩进

**【强制】** 使用 **2** 个空格做为一个缩进层级，不允许使用 **4** 个空格 或 **tab** 字符；

示例：

```css
/* Not so great */
.selector {
  margin: 0;
}

/* Better */
.selector {
    margin: 0;
}
```

### 2.2 空格
**【强制】** 选择器 与 `{ `之间必须包含空格；

示例：

```css
/* Not so great */
.selector{
}

/* Better */
.selector {
}
```

**【强制】** `>`、`+`、`~` 选择器的两边各保留一个空格;

示例：

```css
/* Not so great */
main>nav {
    padding: 10px;
}
label+input {
    margin-left: 5px;
}
input:checked~button {
    background-color: #69C;
}

/* Better */
main > nav {
    padding: 10px;
}
label + input {
    margin-left: 5px;
}
input:checked ~ button {
    background-color: #69C;
}
```

**【强制】** 属性名 与之后的 `:` 之间不允许包含空格， `: `与 属性值 之间必须包含空格；

示例：

```css
/* Not so great */
margin :0;

/* Better */
margin: 0;
```

**【强制】** 列表型属性值 书写在单行时，`, `后必须跟一个空格；

示例：

```css
/* Not so great */
font-family: Arial,sans-serif;
box-shadow: 0 0 2px rgba(0,128,0,.3);

/* Better */
font-family: Arial, sans-serif;
box-shadow: 0 0 2px rgba(0, 128, 0, .3);
```

### 2.3 选择器
**【强制】** 当一个 rule 包含多个 selector 时，每个选择器声明必须独占一行；

示例：

```css
/* Not so great */
.post, .page, .comment {
    line-height: 1.5;
}

/* Better */
.post,
.page,
.comment {
    line-height: 1.5;
}
```

### 2.4 属性
**【强制】** 属性定义必须另起一行；

示例：

```css
/* Not so great */
.selector { margin: 0; padding: 0;}

/* Better */
.selector {
    margin: 0;
    padding: 0;
}
```

**【强制】** 属性定义后必须以分号结尾；

示例：

```css
/* Not so great */
.selector {
    margin: 0
}

/* Better */
.selector {
    margin: 0;
}
```


**[[⬆]](#)**



## 3. 通用

### 3.1 选择器

**【强制】** 如无必要，不得为`id`、`class`选择器添加 *类型选择器* 进行限定；

在性能和维护性上，都有一定的影响。

示例：

```css
/* Not so great */
dialog#error,
p.danger-message {
    font-color: #c00;
}

/* Better */
#error,
.danger-message {
    font-color: #c00;
}
```

**【建议】** 选择器的嵌套层级应该不大于 **3** 级，位置靠后的限定条件应可能精确；

在性能和维护性上，都有一定的影响。

示例：

```css
/* Not so great */
.comment ul li a span {}
#top-hero .hero-avatar li.avatar .pic em {}

/* Better */
.comment .date {}
#top-hero .pic em {}
```

### 3.2 属性

### 3.2.1 属性书写顺序

**【建议】** 同一 rule set 下的属性在书写时，应按功能进行分组，并以 Formatting Model > Box Model > Typographic > Visual 的顺序书写，以提高代码的可读性。

1. Positioning Model 布局方式、位置；相关属性包括：`position / top / right / bottom / left / z-index  / display / float / ...`
2. Box model 盒模型；相关属性包括：`width / height / padding / margin / border / overflow /  ...`
3. Typographic 文本排版；相关属性包括：`font / line-height / text-align / word-wrap / ...`
4. Visual 视觉外观；相关属性包括：`color / background / list-style / transform / animation / transition  / ...`
5. 如果包含 content 属性，应放在最前面；

Positioning 处在第一位，因为他可以使一个元素脱离正常文本流，并且覆盖盒模型相关的样式。盒模型紧跟其后，因为他决定了一个组件的大小和位置。其他属性只在组件 内部 起作用或者不会对前面两种情况的结果产生影响，所以他们排在后面。

详情资料 [Twitter的strictPropertyOrder](https://github.com/twitter/recess/blob/master/lib/lint/strict-property-order.js#L36)


### 3.2.2 属性引号

**【强制】** 属性选择器中的值必须用双引号包围。不允许使用单引号，不允许不使用引号。

示例：

```css
/* Not so great */
article[character='juliet'] {
    voice-family: "Vivien Leigh", victoria, female
}

/* Better */
article[character="juliet"] {
    voice-family: "Vivien Leigh", victoria, female
}
```

### 3.2.3 属性简写

简写形式可以在一定程度上压缩样式，但并不意味着你可以对所有可以简写的属性声明都使用简写。过度使用简写形式的属性声明会导致代码混乱，会对属性值带来不必要的覆盖从而引起意外的副作用，并且不能充分利用CSS的继承。常见的滥用简写属性声明的情况如下：

* `padding`
* `margin`
* `font`
* `background`
* `border`
* `border-radius`

如果你只需定义其中的一两个属性，而不是全部，尽量分开来写：
```css
/* Better */
.selector {
    margin-bottom: 10px;
    background-color: red;
    background-image: url(image.jpg);
    border-top-left-radius: 3px;
    border-top-right-radius: 3px;
}

/* Not so great */
.selector {
    margin: 0 0 10px;
    background: red;
    background: url(image.jpg);
    border-radius: 3px 3px 0 0;
}
```


**[[⬆]](#)**



## 4 值与单位

### 4.1 文本

**【强制】** 文本内容必须用双引号包围，不允许使用单引号；

文本类型的内容可能在选择器、属性值等内容中。

示例：

```css
/* Not so great */
html[lang|=zh] q:before {
    font-family: 'Microsoft YaHei', sans-serif;
    content: '“';
}

/* Better */
html[lang|="zh"] q:after {
    font-family: "Microsoft YaHei", sans-serif;
    content: "“";
}
```

### 4.2 数值

**【强制】** 当数值为 **0 - 1** 之间的小数时，省略整数部分的 **0**；

示例：

```css
/* Not so great */
.selector {
    opacity: 0.8;
}

/* Better */
.selector {
    opacity: .8;
}
```

### 4.3 长度

**【强制】** 长度为 **0** 时须省略单位 (也只有长度单位可省)；

示例：

```css
/* Not so great */
.selector {
    margin: 0px 10px;
}

/* Better */
.selector {
    margin: 0 10px;
}
```

### 4.4 url()

**【强制】** url() 函数中的路径不加引号；

示例：

```css
/* Not so great */
.selector {
    background: url("bg.png");
}

/* Better */
.selector {
    background: url(bg.png);
}
```

### 4.5 颜色

**【强制】** RGB颜色值必须使用十六进制记号形式 `#rrggbb`，不允许使用 `rgb()`，带有alpha的颜色信息可以使用 `rgba()`；颜色值不允许使用命名色值；

示例：

```css
/* Not so great */
.selector {
    box-shadow: 0 0 2px rgba(0,128,0,.3);
    border-color: rgb(0, 128, 0);
    color: gray;
}

/* Better */
.selector {
    box-shadow: 0 0 2px rgba(0, 128, 0, .3);
    border-color: #008000;
    color: #999;
}
```

**【建议】** 颜色值中的英文字符采用小写，至少要保证同一项目内一致；

示例：

```css
/* Not so great */
.selector {
    color: #0073AA;
}

/* Better */
.selector {
    color: #0073aa;
}
```

### 4.6 2D位置

**【强制】** 必须同时给出水平和垂直方向的位置；

2D 位置初始值为 0% 0%，但在只有一个方向的值时，另一个方向的值会被解析为 center。为避免理解上的困扰，应同时给出两个方向的值。 [background-position属性值的定义](http://www.w3.org/TR/CSS21/colors.html#propdef-background-position)

示例：

```css
/* Not so great */
.selector {
    background-position: top; /* 50% 0% */
}

/* Better */
.selector {
    background-position: center top; /* 50% 0% */
}
```


**[[⬆]](#)**



## 5. 文本排版

### 5.1 字体族

**【强制】** `font-family` 属性中的字体族名称应使用字体的**英文** Family Name，其中如有空格，须放置在引号中；

常见的字体族名称如下：

| 字体 | 操作系统 | Family Name |
|:----|:------|:----|
|宋体 (中易宋体) |  Windows | SimSun |
|黑体 (中易黑体) |  Windows | SimHei |
|微软雅黑       |  Windows | Microsoft YaHei |
|微软正黑 | Windows | Microsoft JhengHei |
|华文黑体 | Mac/iOS | STHeiti |
|冬青黑体 | Mac/iOS | Hiragino Sans GB |
|文泉驿正黑 | Linux | WenQuanYi Zen Hei |
|文泉驿微米黑 | Linux | WenQuanYi Micro Hei |

**【强制】** `font-family` 应当遵循以下顺序：

1. 西文字体在前，中文字体在后；
2. 效果佳 (质量高/更能满足需求) 的字体在前，效果一般的字体在后的顺序编写；
3. 最后必须指定一个通用字体族( serif / sans-serif )；

详细说明可参考 [如何保证网页的字体在各平台都尽量显示为最高质量的黑体？](http://www.zhihu.com/question/19911793/answer/13329819)

**【强制】** `font-family` 不区分大小写，但在同一个项目中，同样的 Family Name 大小写必须统一；

示例：

```css
/* Not so great */
body {
    font-family: arial, sans-serif;
}

h1 {
    font-family: Arial, "Microsoft YaHei", sans-serif;
}

/* Better */
body {
    font-family: Arial, sans-serif;
}

h1 {
    font-family: Arial, "Microsoft YaHei", sans-serif;
}
```

### 5.2 字重

**【强制】** `font-weight` 属性必须使用数值方式描述；

CSS 的字重分 100 – 900 共九档，但目前受字体本身质量和浏览器的限制，实际上支持 400 和 700 两档，分别等价于关键词 normal 和 bold。

浏览器本身使用一系列[启发式规则](http://www.w3.org/TR/CSS21/fonts.html#propdef-font-weight)来进行匹配，在 &gt;700 时一般匹配字体的 Regular 字重，&gt;=700 时匹配 Bold 字重。

但已有浏览器开始支持 =600 时匹配 Semibold 字重 ([见此表](http://justineo.github.io/slideshows/font/#/3/15))，故使用数值描述增加了灵活性，也更简短。

示例：

```css
/* Not so great */
.selector {
    font-weight: bold;
}

/* Better */
.selector {
    font-weight: 700;
}
```


**[[⬆]](#)**


## 6 变换与动画

**【强制】** 使用 `transition` 定义属性时应遵循以下顺序：

1. `[ transition-property ]`：检索或设置对象中的参与过渡的属性；
2. `[ transition-duration ]`：检索或设置对象过渡的持续时间；
3. `[ transition-timing-function ]`：检索或设置对象中过渡的动画类型；
4. `[ transition-delay ]`：检索或设置对象延迟过渡的时间；

`transition：[ transition-property ] || [ transition-duration ] || [ transition-timing-function ] || [ transition-delay ]`

如果顺序错乱，在某些安卓浏览器上会让动画失效。

示例：

```css
/* Not so great */
.selector {
    transition: color .2s 0 ease-in;
}

/* Better */
.selector {
    transition: color .2s ease-in 0;
}
```

**【建议】** 尽可能在浏览器能高效实现的属性上添加过渡和动画：

在可能的情况下应选择这样四种变换：

* `transform: translate(npx, npx);`
* `transform: scale(n);`
* `transform: rotate(ndeg);`
* `opacity: 0..1;`

详见 [High Performance Animations](http://www.html5rocks.com/en/tutorials/speed/high-performance-animations/)


**[[⬆]](#)**


## 7 媒体查询

**【强制】** `Media Query` 不得单独编排，必须与相关的规则一起定义；

不要将他们一起放到一个独立的样式文件中，或者丢在文档的最底部，这样做只会让大家以后更容易忘记他们。

示例：

```css
/* Not so great */
/* header styles */
/* main styles */
/* footer styles */

@media (...) {
    /* header styles */
    /* main styles */
    /* footer styles */
}

/* Better */
/* header styles */
@media (...) {
    /* header styles */
}

/* main styles */
@media (...) {
    /* main styles */
}

/* footer styles */
@media (...) {
    /* footer styles */
}
```

## 8 兼容性

### 8.1 属性前缀

**【强制】** 带私有前缀的属性由长到短排列，按冒号位置对齐；

标准属性放在最后，按冒号对齐方便阅读与编辑。

示例：

```css
/* Not so great */
.selector {
    transition: color .2s ease-in 0;
    -webkit-transition: color .2s ease-in 0;
    -moz-transition: color .2s ease-in 0;
}

/* Better */
.selector {
    -webkit-transition: color .2s ease-in 0;
       -moz-transition: color .2s ease-in 0;
            transition: color .2s ease-in 0;
}
```

### 8.2 hack

**【建议】** 如果有其他解决方案，请不要使用hack；


**[[⬆]](#)**


## 9 代码注释

代码是由人编写并维护的。请确保你的代码能够自描述、注释良好并且易于他人理解。好的代码注释能够传达上下文关系和代码目的。不要简单地重申组件或 class 名称。

### 9.1 单行注释

**【强制】** 星号与内容之间必须保留一个空格；

示例：

```css
/* 新闻中心表格隔行变色 */
```

### 9.2 多行注释

**【强制】** 星号要一列对齐，星号与内容之间必须保留一个空格；

示例：

```css
/**
 * Sometimes you need to include optional context for the entire component. Do that up here if it's important enough.
 */
```
 
### 9.3 文件注释

**【强制】** 文件顶部必须包含文件注释，用 `@file` 标识文件说明。星号要一列对齐，星号与内容之间必须保留一个空格，标识符冒号与内容之间必须保留一个空格；

```css
/**
 * @file: 文件概要描述
 * @author: author-name(mail-name@domain.com)
 *          author-name2(mail-name2@domain.com)
 * @update: 2015-04-29 00:02:45
 */
```
* `@update`为可选项，建议每次改动都更新一下；
* 当该业务项目主要由固定的一个或多个人负责时，需要添加`@author`标识，一方面是尊重劳动成果，另一方面方便在需要时快速定位责任人；


**[[⬆]](#)**


参考资料： 

1. [bootcss编码规范](http://codeguide.bootcss.com/)
2. [豆瓣CSS Code Guideline](https://github.com/kejun/CSS-Code-Guideline)
2. [spec css style guide](https://github.com/ecomfe/spec/blob/master/css-style-guide.md)
