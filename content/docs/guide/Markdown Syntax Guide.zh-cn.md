---
title: Markdown 语法指南
toc: false
prev: docs/_index
excludeSearch: true
---

## 基础语法

### 标题

```
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题
```
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题

### 换行
* 在一行的末尾添加 \<br> 即可进行换行

```
第一行<br>
第二行<br>
第三行<br>
```

第一行<br>
第二行<br>
第三行<br>

### 强调
* 在语句前后各加上两个 * 或 _ 即可加粗字体

```
**Hello World**
__Hello World__
```
**Hello World**<br>
__Hello World__

* 在语句前后加上一个 * 或 _ 即可使文本斜体显示

```
*Hello World*
_Hello World_
```
*Hello World*<br>
_Hello World_

### 列表
* 在语句前加上数字和 . 空格即可创建有序列表<br>
在语句前加上 - 或 + 或 * 和空格即可创建无序列表

```
1. One
2. Two
3. Three
- One
+ Two
* Three
```
1. One
2. Two
3. Three
- One
+ Two
* Three

### 引用
* 在语句前加上一个 > 和空格即可引用显示<br>
在要嵌套的段落前加上两个 > 和空格可以嵌套显示<br>
引用也可以搭配其他语法使用

```
> Hello World
> Hello
>> world
> **Hello** *World*
```

> Hello World<br>
> Hello<br>
>> world<br>
> **Hello** *World*<br>

### 代码
* 在语句前后加上 ` 或 ``` 即可代码显示

```
`Hello World`
```Hello World```
```

`Hello World`<br>
```Hello World```

### 链接
* 把链接文本放在 [] 内，链接放在 () 内即可创建文本链接<br>
链接语法也可以搭配其他语法使用

```
[github](https://github.com)
[**github**](https://github.com)
```

[github](https://github.com)<br>
[**github**](https://github.com)

### 图片
* 在链接语法的基础上在 [] 前加上 ! 并在 () 中填写图片链接或目录即可添加图片<br>
链接或目录后可以增加一个可选的图片标题文本

```
![My Avatar](https://github.com/adallei.png)
![My Avatar](https://github.com/adallei.png "Avatar")
```

![My Avatar](https://github.com/adallei.png)
![My Avatar](https://github.com/adallei.png "Avatar")

以上就是Markdown的基础用法，涵盖了大部分使用场景。<br>
如果想要了解更多MarkDown语法请参阅[*Markdown官方教程*](https://markdown.com.cn/)