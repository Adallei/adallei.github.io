---
title: Markdown Syntax Guide
toc: false
prev: docs/_index
excludeSearch: true
---

## Basic grammar
### Headings

```
### Heading III
#### Heading IV
##### Heading V
###### Heading VI
```
### Heading III
#### Heading IV
##### Heading V
###### Heading VI

### Line breaks
* Add \<br> at the end of a line to make a line break

```
First line<br>
Second line<br>
Third line<br>
```

First line<br>
Second line<br>
Third line<br>

### Emphasis
* Add two * or  _ before and after the statement to boldface

```
**Hello World**
__Hello World__
```
**Hello World**<br>
__Hello World__

* Adding a * or _ before or after a statement makes the text italicized

```
*Hello World*
_Hello World_
```
*Hello World*<br>
_Hello World_

### Lists
*  Preceding a statement with a number and . spaces to create an ordered list<br>
An unordered list can be created by prefixing the statement with - or + or * and a space

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

### Quotes
*  The display can be quoted by prefixing the statement with a > and a space<br>
Nested paragraphs can be displayed by prefixing them with two > and a space<br>
References can also be used with other syntax

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

### Code
* Add ` or ``` before or after the statement to display the code

```
`Hello World`
```Hello World```
```

`Hello World`<br>
```Hello World```

### Links
*  Place the link text in [] and the link in () to create a text link<br>
The linking syntax can also be used with other syntaxes

```
[github](https://github.com)
[**github**](https://github.com)
```

[github](https://github.com)<br>
[**github**](https://github.com)

### Image
*  Add ! before [] to the link syntax and fill in the () with the image link or directory. and fill in the () with the link or directory of the image to add the image.<br>
An optional image title text can be added after the link or directory

```
![My Avatar](https://github.com/adallei.png)
![My Avatar](https://github.com/adallei.png "Avatar")
```

![My Avatar](https://github.com/adallei.png)
![My Avatar](https://github.com/adallei.png "Avatar")

These are the basic uses of Markdown, covering most usage scenarios.<br>
If you want to know more about MarkDown syntax see[*Markdown Guide*](https://www.markdownguide.org/)