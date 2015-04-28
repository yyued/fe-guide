# Directory Guide

---

静态资源目录规范指南。

---

**【强制】** 所有资源类型必须按以下目录放置；

* **doc** 与 **swf** 不会默认生成；
* 当该项目为中大型项目或长期维护项目时，请手动添加**doc**目录，并且填写相关文档；
* 当该项目有需要flash文件时，请手动添加**swf**目录放置flash文件；


```html
src/                                # static resource directory
|
|-- css/                            # all generated CSS
|   |-- global.sss                  # the global stylesheet
|   ...
|
|-- doc/                            # the project documents
|   |-- css.md                      # stylesheet document
|   |-- sass.md                     # SASS document
|   |-- html.md                     # html document
|   |-- js.md                       # javascript document
|   |-- README.md                   # general documentation
|   ...
|
|-- img/                            # all images
|   |-- bg-body.jpg                 # body background
|   ...
|
|-- js/                             # all javascript files
|   |-- main.js                     # general documentation
|   |-- vendor                      # third-party plugins
|       |-- modernizr-2.8.3.min.js
|       |-- ...
|   ...
|
|-- sass/                           # all SASS files
|   |-- global.scss                 # the global SASS
|   |-- _slice.scss                 # automatic img to css
|   |-- base                        # the base SASS
|       |-- _base.scss
|       |-- _mixins.scss
|       |-- _normalize.scss
|   |-- lego                        # the LEGO UI SASS
|       |-- _config.scss
|       |-- _ui-box.scss
|       |-- _ui-tab.scss
|       |-- ...
|   |-- biz1                        # the business SASS
|       |-- ...
|   |-- biz2                        # the business SASS
|       |-- ...
|
|-- swf/                            # the flash files
|   |-- logo-duowan.swf
|   |-- ...
|
|-- tpl/                            # the templates
|   |-- ...
|
`-- index.html                      # the html file
```
