# Directory Guide

---

目录与文件规范指南。

---

**【强制】** 所有的目录与文件命名使用中横线连接多个单词；

除了`README.md`和第三方的目录文件，一律禁止使用 `Pascal命名法`、`Camel命名法` 或 下划线连词。

## 工作流默认目录

```javascript
// good
src/
|
|-- img/
|   |-- bg-body.jpg
|   ...
|-- component/
|   |-- develop-film
|       |-- index.vue
|       |-- ...
|
`-- README.md

// bad
src/
|
|-- img/
|   |-- bgBody.jpg
|   ...
|-- component/
|   |-- develop_film
|       |-- index.vue
|       |-- ...
|
`-- README.md
```

