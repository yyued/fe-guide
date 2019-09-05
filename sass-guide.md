# SASS Guide

---

SASS规范指南，SASS 代码的基本规范和原则与 [CSS 编码规范](https://github.com/duowan/fe-guide/blob/master/css-guide.md) 保持一致。

---

## 文档目录

1. [编码](#1-编码)
2. [代码组织](#2-代码组织)
3. [`@import` 语句](#3-import-语句)
4. [变量](#4-变量)
5. [继承](#5-继承)
6. [BEM命名](#6-BEM命名)

## 1 编码

**【强制】** 使用UTF-8编码，每个SASS文件的第一行必须是定义编码的 `@charset "UTF-8";`；

如果没定义编码，很有可能会出现跨平台兼容问题。


## 2 代码组织

**【强制】** 代码必须按如下形式按顺序组织：

1. 全局的变量声明 || `@import`；
2. 样式声明；

示例：

```css
$base-font-size          : 12px !default; // 字号
$base-font-family        : "Hiragino Sans GB", "Microsoft Yahei", "WenQuanYi Micro Hei", sans-serif !default; // 字体族

@import "base/config";
@import "biz/page";

body {
    background: #fff;
}
```

## 3 `@import` 语句

**【强制】** 同一个SASS文件中的所有的 `@import`必须放在同一块，不允许分开：

**【建议】** 使用双引号引入SASS文件，至少同一项目要保持一致：

## 4 变量

**【强制】** 变量命名必须采用 @foo-bar 形式，不允许使用 @fooBar 形式；

示例：

```css
/* Not so great */
$cardColor: #fff;

/* Better */
$card-color: #fff;
```

## 5 继承

**【强制】** 使用继承时，如果在声明块内书写 `@extend` 语句，必须写在开头；

示例：

```css
/* Not so great */
.selector {
    color: #fff;
    @extend sameStyle;
}

/* Better */
.selector {
    @extend sameStyle;
    color: #fff;
}
```

## 6 BEM命名

**【强制】** SASS内使用BEM命名时，请勿使用缩写与嵌套；

SASS BEM使用缩写会不利于名称搜索、排查定位；另外，BEM本来就是为了解决嵌套问题，因此没必要多此一举。

示例：

```css
/* Not so great */
.aside {
    color: #fff;
    &__item {
        width: 100px;
    }
}

/* Better */
.aside {
    color: #fff;
}
.aside__item {
    width: 100px;
}
```
