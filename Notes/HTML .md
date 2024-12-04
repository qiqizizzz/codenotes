# 0、资料

[前端原生Html免费模板网站总结(带网址)](https://blog.csdn.net/m0_49714202/article/details/125457301)

[HTML教程](https://www.runoob.com/html/html-tutorial.html)

[HTML 参考手册- (HTML5 标准)](https://www.runoob.com/tags/html-reference.html)

 [CSS教程](https://www.runoob.com/css/css-tutorial.html)

[CSS 参考手册](https://www.runoob.com/cssref/css-reference.html)

[Web docs](https://developer.mozilla.org/en-US/)

[CSS动画库_github](https://animate.style/)

# 一、基础

## 1.网页

HTML:超文本标记语言，用来制作网页的一门语言。

网页是图片、链接、文字、声音、视频等元素组成，其实就是一个html文件(后缀名为html)。

## 2.Web标准

主要包括结构、表现和行为三个方面。

| 标准 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| 结构 | 结构用于对网页元素进行整理和分类，现阶段主要学的是HTML。     |
| 表现 | 表现用于设置网页元素的版式、颜色、大小等外观样式，主要指的是CSS |
| 行为 | 行为是指网页模型的定义及**交互**的编写，现阶段主要学的是JavaScript |

## 3.基础语法

### 3.1 HTML 标题

HTML 标题（Heading）是通过`<h1> `- `<h6> `标签来定义的。

```html
<h1>这是一个标题</h1>
<h2>这是一个标题</h2>
<h3>这是一个标题</h3>
```

 `<br>`元素可用于分割内容。区分一下： `<br>`, `<br/> `以及 `<br />`（带有空格）
`<br>` 是 HTML 写法。是 XHTML1.1 的写法, 也是 XML 写法。`<br/>` 是 XHTML 为兼容 HTML 的写法,也是 XML 写法。HTML5 因为兼容 XHTML，所以三种写法都可以使用。
早期发布的 HTML 规范当中，`<br>` 与` <img>` 等元素是不用封闭自身的，但是这种元素造成了 HTML 规范的不严谨，于是在之后发布的 XHTML 语言中，参考了更为严谨的 XML 规范，在这些不用自身封闭的元素后加 `/`来表示自行封闭，在逻辑上来讲等同于`<br>`....`</br>`（但是没有 `</br>` 这种写法），这样一来保证了较少的代码量，二来保证了规范的严谨



可以将注释插入 HTML 代码中，这样可以提高其可读性，使代码更易被人理解。浏览器会忽略注释，也不会显示它们。

注释写法如下:

```html
<!-- 这是一个注释 -->
```

**注释:** 开始括号之后（左边的括号）需要紧跟一个叹号 **!** (英文标点符号)，结束括号之前（右边的括号）不需要，合理地使用注释可以对未来的代码编辑工作产生帮助。



> **标题大小与字体大小的关系:**

1到6号标题与1到6号字体逆序对应，比如1号字体对应6号标题，2号字体对应5号标题。

```html
<h1>这是1号标题</h1>
<font size="6">这是6号字体文本</font>

<h2>这是2号标题</h2>
<font size="5">这是5号字体文本</font>

<h3>这是3号标题</h3>
<font size="4">这是4号字体文本</font>

<h4>这是4号标题</h4>
<font size="3">这是3号字体文本</font>

<h5>这是5号标题</h5>
<font size="2">这是2号字体文本</font>

<h6>这是6号标题</h6>
<font size="1">这是1号字体文本</font>
```

### 3.2 HTML 段落

HTML 段落是通过标签 `<p>` 来定义的。

```html
<p>这是一个段落。</p>
<p>这是另外一个段落。</p>
```

**注意**：浏览器会自动地在段落的前后添加空行。（`</p>` 是块级元素）



### 3.3 HTML 链接

HTML 链接是通过标签 `<a>` 来定义的。

```html
<a href="https://www.runoob.com">这是一个链接</a>
```

- `<a>` 标签：定义了一个超链接（anchor）。它是 HTML 中用来创建可点击链接的主要标签。
- `href` 属性：指定目标 URL，当点击链接时，浏览器将导航到此 URL。



HTML使用标签 **`<a>`** 来设置超文本链接。

超链接可以是一个字，一个词，或者一组词，也可以是一幅图像，您可以点击这些内容来跳转到新的文档或者当前文档中的某个部分。

当您把鼠标指针移动到网页中的某个链接上时，箭头会变为一只小手。

在标签 `<a> `中使用了 **`href`** 属性来描述链接的地址。

默认情况下，链接将以以下形式出现在浏览器中：

- 一个未访问过的链接显示为蓝色字体并带有下划线。
- 访问过的链接显示为紫色并带有下划线。
- 点击链接时，链接显示为红色并带有下划线。

> 注意：如果为这些超链接设置了 CSS 样式，展示样式会根据 CSS 的设定而显示。



#### HTML 链接属性

href 属性描述了链接的目标。

**1、href：定义链接目标。**

这是超链接最重要的属性，用来指定链接的目的地，可以是另一个网页、文件、邮件、电话号码或 JavaScript。

```html
<a href="https://www.example.com">访问 Example</a>
```

**2、target：定义链接的打开方式。**

- `_blank`: 在新窗口或新标签页中打开链接。
- `_self`: 在当前窗口或标签页中打开链接（默认）。
- `_parent`: 在父框架中打开链接。
- `_top`: 在整个窗口中打开链接，取消任何框架。

```html
<a href="https://www.example.com" target="_blank" rel="noopener">新窗口打开 Example</a>
```

 `_self`的话是指在本身这个网页窗口来打开新的网页链接。
`_parent`主要是针对于框架网页中的跳转。
如果你一个页面由两三个框架组成，你要想整个页面跳转到其它网页链接，目标就需要用`_parent`了。如果不用这个，就只会使得那一小块框架区域里的网页跳转。 
而其它的地方则不变`_top`与`_self`差不很大。但是如果你用了`<!--#include file="..."-->`时，就会知道两者的差别了。因为如果你的超链接是做在 `<!--#include file="..."-->`上时。如果用`_self` 点击后的超链接就会在`<!--#include file="..."-->` 这个页面上打开，而页面其它部分不会改变。如果用_top 则会整个窗口一起跳转到新的链接网页。

**3、rel：定义链接与目标页面的关系。**

**nofollow**: 表示搜索引擎不应跟踪该链接，常用于外部链接。

**noopener** 和 **noreferrer**: 防止在新标签中打开链接时的安全问题，尤其是使用 **target="_blank"** 时。

- `noopener`: 防止新的浏览上下文（页面）访问`window.opener`属性和`open`方法。
- `noreferrer`: 不发送referer header（即不告诉目标网站你从哪里来的）。
- `noopener noreferrer`: 同时使用`noopener`和`noreferrer`。例子: `<a href="https://www.example.com" rel="noopener noreferrer">安全链接</a>`

> noopener noreferrer的意思是不会打开其他的网站，因为恶意病毒可能会修改你的浏览器空白页地址。

```html
<a href="https://www.example.com" target="_blank" rel="noopener noreferrer">安全链接</a>
```

**4、download：提示浏览器下载链接目标而不是导航到该目标。**

如果指定了文件名，浏览器会提示下载并保存为指定文件名。

例如：

```html
<a href="file.pdf" download="example.pdf">下载文件</a>
```

**5、title：定义链接的额外信息，当鼠标悬停在链接上时显示的工具提示。**

```html
<a href="https://www.example.com" title="访问 Example 网站">访问 Example</a>
```

**6、id：用于链接锚点，通常在同一页面中跳转到某个特定位置。**

```html
<!-- 链接到页面中的某个部分 -->
<a href="#section1">跳转到第1部分</a>
<div id="section1">这是第1部分</div>
```

**7、hreflang: 指定链接的目标URL的语言**

```html
<a href="https://www.example.com/es" hreflang="es">访问西班牙语网站</a>
```

**8、type: 指定链接资源的MIME类型**

```html
<a href="style.css" type="text/css">样式表</a>
```

**9、class: 用于指定元素的类名（CSS中定义）**

```html
<a href="https://www.example.com" class="external-link">外部链接</a>
```

**10、style: 直接在元素上定义CSS样式**

```html
<a href="https://www.example.com" style="color: red;">红色链接</a>
```

#### 空链接

以下是常见的几种设置空链接的方法，以及它们之间的区别：

| 方法                        | 作用                       | 是否会跳转 | 场景适用性                   |
| :-------------------------- | :------------------------- | :--------- | :--------------------------- |
| `href="#"`                  | 导航到页面顶部             | 是         | 占位符，捕获点击事件         |
| `href="javascript:void(0)"` | 阻止默认行为，不刷新页面   | 否         | 阻止跳转，配合 JS 使用       |
| `href=""`                   | 刷新当前页面               | 是         | 需要页面刷新时               |
| `href="about:blank"`        | 打开空白页面               | 是         | 新窗口打开空白页面           |
| `role="button"`             | 链接表现为按钮，无默认行为 | 否         | 配合 JS 实现按钮功能，无跳转 |



#### 关于创建电子邮件链接时如何发送邮件内容

在进行邮件内容发送时，需要使用关键字：**mailto**

示例如下：

```html
<a href="mailto:zhangrr601@163.com?subject=这是邮件的主题&body=这是邮件的内容" rel="nofollow">发送邮件</a>
```

这样会调启系统默认的邮件程序发送给 `zhangrr601@163.com`并且收件人那里已经填上了我邮箱的地址。

关于创建电子邮件链接时如何进行抄送，密送.

> **抄送：**
>
> 英文名称：Carbon Copy，又简称为 CC。在网络术语中，抄送就是将邮件同时发送给收信人以外的人，用户所写的邮件抄送一份给别人，对方可以看见该用户的 E-mail。同收件人地址栏一样，不可以超过 1024 个字符。一般来说，使用"抄送"服务时，多人抄送的电子邮件地址使用 **;** 分隔。



> **密件抄送：**
>
> 英文名称：Blind Carbon Copy ，又称“盲抄送”，和抄送的唯一区别就是它能够让各个收件人**无法查看**到这封邮件同时还发送给了哪些人。密件抄送是个很实用的功能，假如一次向成百上千位收件人发送邮件，最好采用密件抄送方式，这样一来可以保护各个收件人的地址不被其他人轻易获得，二来可以使收件人节省下收取大量抄送的 E-mail 地址的时间。

在进行抄送时，需要使用关键字：**cc**

在进行密送时，需要使用关键字：**bcc**

示例如下：

```html
<a href="mailto:zhangrr601@163.com?cc=someone@163.com&bcc=somebody@163.com" rel="nofollow">发送邮件</a>
```

参数说明：

| 参数                     | 描述             |
| :----------------------- | :--------------- |
| `mailto:*name@email.com` | 邮件接收地址     |
| `cc=*name@email.com`     | 抄送地址         |
| `bcc=*name@email.com`    | 密件抄送地址     |
| `subject=*subject text`  | 邮件主题         |
| `body=*body text`        | 邮件内容         |
| `?`                      | 第一个参数分隔符 |
| `&`                      | 其他参数分隔符   |

注：多个邮件地址用 **;** 隔开，空格用 **%20** 代替。



### 3.4 HTML 图像

HTML 图像是通过标签 `<img>` 来定义的.

```html
<img src="/images/logo.png" width="258" height="39" />
```

**注意**： 图像的名称和尺寸是以属性的形式提供的。



1、***.html** 文件跟 **1.png** 文件(c盘)在不同目录下：

```html
 <img src="file:///C:/Users/ASUS/Pictures/1.png" width="260" height="260"/>
```

2、***.html** 文件跟 **1.jpg** 图片在相同目录下：

```html
<img src="1.jpg" width="300" height="120"/>
```

3、***.html** 文件跟 **1.jpg** 图片在不同目录下：

```html
a、图片 1.jpg 在 image 文件夹中，1.html 跟 image 在同一目录下：
<img src="image/1.jpg/"width="300" height="120"/>
```

```html
b、图片 1.jpg 在 image 文件夹中，1.html 在 connage 文件夹中，image 跟 connage 在同一目录下：
<img src="../image/1.jpg/"width="300" height="120"/>
```

4、如果图片来源于网络，那么写绝对路径：

```html
<img src="http://static.runoob.com/images/runoob-logo.png" width="300" height="120"/>
```



**html 相对路径的写法：**

-  **./**：代表文件所在的目录（可以省略不写）如果写成image/background就相当于是在html文件下找image文件夹，当然是找不到的
-  **../**：代表文件所在的父级目录
-  **../../**：代表文件所在的父级目录的父级目录
-  **/**：代表文件所在的根目录

> 同一个目录：index2.html 或./index2.html；
> 在子目录：xxx/index2.html；
> 在孙子目录：xxx/xxx/index2.html；
> 在父目录：../index2.html；
> 在爷爷目录：../../index2.html；



## 4.基础概念

### 4.1 元素显示模式

在CSS中，html中的标签元素大体被分为三种不同的类型： 块状元素、内联元素(又叫行内元素)和内联块状(又叫行内块元素)元素。

常用的块状元素有：

 `<div>`、`<p>`、`<h1>`…`<h6>`、`<ol>`、`<ul>`、`<dl>`、`<table>`、`<address>`、`<blockquote>` 、`<form>`

**1.块级元素** 

在html中`<div>`、`<p>`、`<h1>`、`<form>`、`<ul>`和`<li>`就是块级元素。设置`display:block`就是将元素显示为块级元素。

如下代码就是将内联元素a转换为块状元素，从而使a元素具有块状元素特点。

```css
a{display:block;}
```

块级元素特点：

1、每个块级元素都从新的一行开始，并且其后的元素也另起一行。（真霸道，一个块级元素独占一行）;

2、元素的高度、宽度、行高以及顶和底边距都可设置。

3、元素宽度在不设置的情况下，是它本身父容器的100%（和父元素的宽度一致），除非设定一个宽度。

4、是一个盒子，里面可以放行内或者块级元素。

**2.内联元素--行内元素**

常用的内联元素有： 
`<a>`、`<span>`、`<br>`、`<i>`、`<em>`、`<strong>`、`<label>`、`<q>`、`<var>`、`<cite>`、`<code>`

 在html中，`<span>`、`<a>`、`<label>`、`<strong> `和`<em>`就是典型的内联元素（行内元素）（inline）元素。

当然块状元素也可以通过代码`display:inline`将元素设置为内联元素。如下代码就是将块状元素div转换为内联元素，从而使div 元素具有内联元素特点。

```html
 div{ display:inline; } 
...... 
 <div>我要变成内联元素</div> 
```

内联元素特点： 

1、相邻行内元素在一行上，一行可以显示多个。 

**2、元素的高度、宽度及顶部和底部边距不可设置；** 

3、元素的宽度就是它包含的文字或图片的宽度，不可改变。

4、行内元素只能容纳文本或其他行内元素。

**3.内联块状元素--行内块元素**

常用的内联块状元素有： `<img>`、`<input>`、`<td>`

内联块状元素（inline-block）就是同时具备内联元素、块状元素的特点，代码`display:inline-block`就是将元素设置为内联块状元素。

inline-block 元素特点： 

1、和其他元素都在一行上； 

2、元素的高度、宽度、行高以及顶和底边距都可设置。

| 元素模式   | 元素排列               | 设置样式               | 默认宽度         | 包含                     |
| ---------- | ---------------------- | ---------------------- | ---------------- | ------------------------ |
| 块级元素   | 一行只能放一个块级元素 | 可以设置宽度高度       | 容器的100%       | 容器级可以包含任何标签   |
| 行内元素   | 一行可以放多个行内元素 | 不可以直接设置宽度高度 | 它本身内容的宽度 | 容纳文本或则其他行内元素 |
| 行内块元素 | 一行放多个行内块元素   | 可以设置宽度和高度     | 它本身内容的宽度 |                          |

#### 元素显示模式的转换

**1.转换为块级元素**

```css
<style>
    a{
        display: block;   //核心语句
    }
</style>
```

**2.转换为行内元素**

```css
<style>
	div{
		display: inline;
		}
<style/>
```

**3.转换为行内块元素**

```css
<style>
	span{
		display:inline-block;
		}
<style/>
```



### 4.2 长度单位

长度单位包括包括：

- 相对单位

  `em`,`ex`,`ch`,`rem`,`vw`,`vh`,`vmax`,`vmin`

- 绝对单位

  `cm`,`mm`,`q`,`in`,`pt`,`pc`,`px`

### 4.3 CSS的三大特性

CSS 有三个非常重要的三个特性:层叠性、继承性、优先级。

**1.层叠性**

相同选择器给设置相同的样式，此时一个样式就会覆盖(层叠)另一个冲突的样式。层叠性主要解决样式冲突的问题。

层叠性原则：

- 样式冲突，遵循的原则是就近原则，哪个样式离结构近，就执行哪个样式。
- 样式不冲突，不会层叠

**2.继承性**

CSS中的继承: 子标签会继承父标签的某些样式，如文本颜色和字号。简单的理解就是:子承父业。恰当地使用继承可以简化代码，降低CSS样式的复杂性。

子元素可以继承父元素的样式(text-，font-，line-这些元素开头的可以继承，以及color属性)

**3.优先级**

| 选择器               | 选择器权重 |
| -------------------- | ---------- |
| 继承或者*            | 0,0,0,0    |
| 元素选择器           | 0,0,0,1    |
| 类选择器，伪类选择器 | 0,0,1,0    |
| ID选择器             | 0,1,0,0    |
| 行内样式 style=""    | 1,0,0,0    |
| !important 重要的    | ∞ 无穷大   |

优先级注意点:

1.权重是有4组数字组成,但是不会有进位。

2.可以理解为类选择器永远大于元素选择器,id选择器永远大于类选择器,以此类推。

3.等级判断从左向右，如果某一位数值相同，则判断下一位数值。

4.可以简单记忆法: 通配符和继承权重为0,标签选择器为1,类(伪类)选择器为10,id选择器 100,行内样式表为
1000,!important无穷大。

5.继承的权重是0，如果该元素没有直接选中，不管父元素权重多高，子元素得到的权重都是0。

# 二、HTML

## 0.HTML速查表

### HTML 基本文档

```html
<!DOCTYPE html>
<html>
<head>
<title>文档标题</title>
</head>
<body>
可见文本...
</body>
</html>
```

### 基本标签

```html
<h1>最大的标题</h1>
<h2> . . . </h2>
<h3> . . . </h3>
<h4> . . . </h4>
<h5> . . . </h5>
<h6>最小的标题</h6>
 
<p>这是一个段落。</p>
<br> （换行）
<hr> （水平线）
<!-- 这是注释 -->
```

### 文本格式化

```html
<b>粗体文本</b>
<code>计算机代码</code>
<em>强调文本</em>
<i>斜体文本</i>
<kbd>键盘输入</kbd> 
<pre>预格式化文本</pre>
<small>更小的文本</small>
<strong>重要的文本</strong>
 
<abbr> （缩写）
<address> （联系信息）
<bdo> （文字方向）
<blockquote> （从另一个源引用的部分）
<cite> （工作的名称）
<del> （删除的文本）
<ins> （插入的文本）
<sub> （下标文本）
<sup> （上标文本）
```

### 链接（Links）

```html
普通的链接：<a href="http://www.example.com/">链接文本</a>
图像链接： <a href="http://www.example.com/"><img src="URL" alt="替换文本"></a>
邮件链接： <a href="mailto:webmaster@example.com">发送e-mail</a>
书签：
<a id="tips">提示部分</a>
<a href="#tips">跳到提示部分</a>
```

### 图片（images）

```html
<img src="URL" alt="替换文本" height="42" width="42">
```

### 样式/区块

```html
<style type="text/css">
h1 {color:red;}
p {color:blue;}
</style>
<div>文档中的块级元素</div>
<span>文档中的内联元素</span>
```

### 无序列表

```html
<ul>
    <li>项目</li>
    <li>项目</li>
</ul>
```

### 有序列表

```html
<ol>
    <li>第一项</li>
    <li>第二项</li>
</ol>
```

### 定义列表

```html
<dl>
  <dt>项目 1</dt>
    <dd>描述项目 1</dd>
  <dt>项目 2</dt>
    <dd>描述项目 2</dd>
</dl>
```

### 表格（Tables）

```html
<table border="1">
  <tr>
    <th>表格标题</th>
    <th>表格标题</th>
  </tr>
  <tr>
    <td>表格数据</td>
    <td>表格数据</td>
  </tr>
</table>
```

### 框架（Iframe）

```html
<iframe src="demo_iframe.htm"></iframe>
```

### 表单（Forms）

```html
<form action="demo_form.php" method="post/get">
<input type="text" name="email" size="40" maxlength="50">
<input type="password">
<input type="checkbox" checked="checked">
<input type="radio" checked="checked">
<input type="submit" value="Send">
<input type="reset">
<input type="hidden">
<select>
<option>苹果</option>
<option selected="selected">香蕉</option>
<option>樱桃</option>
</select>
<textarea name="comment" rows="60" cols="20"></textarea>
 
</form>
```

### 实体（Entities）

```html
&lt; 等同于 <
&gt; 等同于 >
&#169; 等同于 ©
```



## 1.HTML 元素

| 开始标签 *               | 元素内容     | 结束标签 * |
| :----------------------- | :----------- | :--------- |
| `<p>`                    | 这是一个段落 | `</p>`     |
| `<a href="default.htm">` | 这是一个链接 | `</a>`     |
| `<br>`                   | 换行         |            |

*****开始标签常被称为**起始标签（opening tag）**，结束标签常称为**闭合标签（closing tag）**。

> HTML 元素语法

- HTML 元素以**开始标签**起始
- HTML 元素以**结束标签**终止
- **元素的内容**是开始标签与结束标签之间的内容
- 某些 HTML 元素具有**空内容（empty content）**
- 空元素**在开始标签中进行关闭**（以开始标签的结束而结束）
- 大多数 HTML 元素可拥有**属性**



**注意**：不要忘记结束标签,忘记使用结束标签会产生不可预料的结果或错误。

没有内容的 HTML 元素被称为空元素。空元素是在开始标签中关闭的。

**最好使用小写标签！**



## 2.HTML属性

属性是 HTML 元素提供的附加信息。

属性总是以 **name="value"** 的形式写在标签内，**name** 是属性的名称，**value** 是属性的值。

- HTML 元素可以设置**属性**
- 属性可以在元素中添加**附加信息**
- 属性一般描述于**开始标签**
- 属性总是以名称/值对的形式出现，**比如：name="value"**。



**实例：**

HTML 链接由 `<a>` 标签定义。链接的地址在 **href 属性**中指定：

```html
<a href="http://www.runoob.com">这是一个链接</a>
```

### HTML 属性常用引用属性值

属性值应该始终被包括在引号内。

双引号是最常用的，不过使用单引号也没有问题。

在某些个别的情况下，比如属性值本身就含有双引号，那么您必须使用单引号，例如：

```html
name='John "ShotGun" Nelson'
```



## 3.HTML文本格式化

HTML 使用标签 `<b>`("bold") 与 `<i>`("italic") 对输出的文本进行格式, 如：**粗体** or *斜体*

这些HTML标签被称为格式化标签（请查看完整标签参考手册）。

```html
通常标签 <strong> 替换加粗标签 <b> 来使用, <em> 替换 <i>标签使用。
然而，这些标签的含义是不同的：
<b> 与<i> 定义粗体或斜体文本。
<strong> 或者 <em>意味着你要呈现的文本是重要的，所以要突出显示。现今所有主要浏览器都能渲染各种效果的字体。不过，未来浏览器可能会支持更好的渲染效果。
```



## 4.HTML头部

**1. HTML` <head> `元素**

`<head> `元素包含了所有的头部标签元素。在 `<head>`元素中你可以插入脚本（scripts）, 样式文件（CSS），及各种meta信息。

可以添加在头部区域的元素标签为:` <title>`,` <style>`, `<meta>`, `<link>`, `<script>`, `<noscript>` 和 `<base>`。

**head 标签和 header 标签的不同**

head 标签用于定义文档头部，它是所有头部元素的容器。`<head>` 中的元素可以引用脚本、指示浏览器在哪里找到样式表、提供元信息等等。

如：

```html
<html>
  <head>
     <title>文档标题</title>
  </head>
</html>
```

header 标签用于定义文档的页眉（介绍信息）。

如：

```html
<html>
  <body>
    <header>
        <p>段落</p>
        <h1>一级标题</h1>
    </header>
  </body>
</html>
```

注意千万不要弄混。

**2. HTML `<title>` 元素**

`<title> `标签定义了不同文档的标题。

`<title> `在 HTML/XHTML 文档中是必需的。

`<title>` 元素:

- 定义了浏览器工具栏的标题
- 当网页添加到收藏夹时，显示在收藏夹中的标题
- 显示在搜索引擎结果页面的标题

**2. HTML `<base>` 元素**

`<base>` 标签描述了基本的链接地址/链接目标，该标签作为HTML文档中所有的链接标签的默认链接:

```html
<head> <base href="http://www.runoob.com/images/" target="_blank"> </head>
```

**3. HTML `<link>` 元素**

`<link>` 标签定义了文档与外部资源之间的关系。

`<link>` 标签通常用于链接到样式表:

```html
<head> <link rel="stylesheet" type="text/css" href="mystyle.css"> </head>
```

**4. HTML `<style>` 元素**

`<style>` 标签定义了HTML文档的样式文件引用地址.

在`<style>` 元素中你也可以直接添加样式来渲染 HTML 文档:

```html
<head>
<style type="text/css">
body {
    background-color:yellow;
}
p {
    color:blue
}
</style>
</head>
```

**5. HTML `<meta>` 元素**

meta标签描述了一些基本的元数据。

```html
<meta> 标签提供了元数据.元数据也不显示在页面上，但会被浏览器解析。
```

META 元素通常用于指定网页的描述，关键词，文件的最后修改时间，作者，和其他元数据。

元数据可以使用于浏览器（如何显示内容或重新加载页面），搜索引擎（关键词），或其他Web服务。

```html
<meta> 一般放置于 <head> 区域
```

**`<meta>` 标签- 使用实例**

为搜索引擎定义关键词:

```html
<meta name="keywords" content="HTML, CSS, XML, XHTML, JavaScript">
```

为网页定义描述内容:

```html
<meta name="description" content="免费 Web & 编程 教程">
```

定义网页作者:

```html
<meta name="author" content="Runoob">
```

每30秒钟刷新当前页面:

```html
<meta http-equiv="refresh" content="30">
```

**6. HTML `<script>` 元素**

`<script>`标签用于加载脚本文件，如： JavaScript。

## 5.HTML CSS

### 如何使用CSS

CSS 是在 HTML 4 开始使用的,是为了更好的渲染HTML元素而引入的.

CSS 可以通过以下方式添加到HTML中:

- 内联样式- 在HTML元素中使用"style" **属性**
- 内部样式表 -在HTML文档头部 `<head>` 区域使用`<style>` **元素** 来包含CSS
- 外部引用 - 使用外部 CSS **文件**

最好的方式是通过外部引用CSS文件.

### 内联样式

当特殊的样式需要应用到**个别元素**时，就可以使用内联样式。 使用内联样式的方法是在相关的标签中使用样式属性。样式属性可以包含任何 CSS 属性。以下实例显示出如何改变段落的颜色和左外边距。

```html
<p style="color:blue;margin-left:20px;">这是一个段落。</p>
```

> 1.HTML样式实例 - **背景颜色**

背景色属性（background-color）定义一个元素的背景颜色：

```html
<body style="background-color:yellow;">
<h2 style="background-color:red;">这是一个标题</h2> 
<p style="background-color:green;">这是一个段落。</p> </body>
```

> 2.HTML 样式实例 - **字体, 字体颜色 ，字体大小**

我们可以使用font-family（字体），color（颜色），和font-size（字体大小）属性来定义字体的样式:

```html
<h1 style="font-family:verdana;">一个标题</h1> <p style="font-family:arial;color:red;font-size:20px;">一个段落。</p>
```

> 3.HTML 样式实例 - **文本对齐方式**

使用 text-align（文字对齐）属性指定文本的水平与垂直对齐方式：

```html
<h1 style="text-align:center;">居中对齐的标题</h1> <p>这是一个段落。</p>
```

### CSS 引入外部标签`link`

第一种方式：使用最多，稳定

```html
<link rel="stylesheet" href="标签路径">
```

第二种方式：

```html
<style>
@import url("标签路径")
</style>
```

**扩展知识点:** link 和 import之间的区别?

**差别 1：**

本质的差别：**link** 属于 XHTML 标签，而 **@import** 完全是 CSS 提供的一种方式。

**差别 2：**

**加载顺序的差别：** 当一个页面被加载的时候（就是被浏览者浏览的时候) ，link 引用的 CSS 会同时被加载，而 **@import** 引用的 CSS 会等到页面全部被下载完再被加载。所以有时候浏览 **@import** 加载 CSS 的页面时开始会没有样式(就是闪烁)，网速慢的时候还挺明显。

**差别 3：**

**兼容性的差别:** **@import** 是 CSS2.1 提出的，所以老的浏览器不支持，**@import** 只有在 IE5 以上的才能识别，而 **link** 标签无此问题。

**差别 4：**

使用 dom(document object model文档对象模型 )控制样式时的差别：当使用 javascript 控制 dom 去改变样式的时候，只能使用 link 标签，因为**@import** 不是 dom 可以控制的。



## 6.HTML图像

**1. HTML 图像- 图像标签（ `<img>`）、`alt`属性和源属性（`Src`）**

在 HTML 中，图像由`<img>` 标签定义。

`<img>` 是空标签，意思是说，它只包含属性，并且没有闭合标签。

要在页面上显示图像，你需要使用源属性（src）。src 指 "source"。源属性的值是图像的 URL 地址。

**定义图像的语法是：**

```html
<img src="url" alt="some_text">
```

URL 指存储图像的位置。如果名为 "pulpit.jpg" 的图像位于 `www.runoob.com` 的 images 目录中，那么其 URL 为 `http://www.runoob.com/images/pulpit.jpg`。

alt 属性用来为图像定义一串预备的可替换的文本。

替换文本属性的值是用户定义的。

在浏览器无法载入图像时，替换文本属性告诉读者她们失去的信息。此时，浏览器将显示这个替代性的文本而不是图像。为页面上的图像都加上替换文本属性是个好习惯，这样有助于更好的显示信息，并且对于那些使用纯文本浏览器的人来说是非常有用的。

**2. HTML 图像- 设置图像的高度与宽度**

height（高度） 与 width（宽度）属性用于设置图像的高度与宽度。

属性值默认单位为像素:

```html
<img src="pulpit.jpg" alt="Pulpit rock" width="304" height="228">
```

**提示:** 指定图像的高度和宽度是一个很好的习惯。如果图像指定了高度宽度，页面加载时就会保留指定的尺寸。如果没有指定图片的大小，加载页面时有可能会破坏HTML页面的整体布局。

**3.HTML 图像-网站图标**

[如何在浏览器标题前端显示一张图片](https://blog.csdn.net/ggq53219/article/details/139016760?sharetype=blogdetail&shareId=139016760&sharerefer=APP&sharesource=2301_81250551&sharefrom=link)

使用 Favicon（网站图标）：Favicon 是一个小的图标，通常显示在浏览器标签页的左上角或地址栏旁边。你可以使用 .ico 或 .png 格式的图片作为 Favicon。在 HTML 中，你可以通过 `<link>` 标签的 rel="icon" 属性来引用它。

```html
<link rel="icon" href="image/cs.ico" type="image/x-icon">
```

或者，对于 PNG 格式：

```html
<link rel="icon" type="image/png" size="16x16" href="image/cs.png">
```

## 7.HTML表格

HTML 表格由 **`<table>`** 标签来定义。

HTML 表格是一种用于展示结构化数据的标记语言元素。

每个表格均有若干行（由 `<tr>` 标签定义），每行被分割为若干单元格（由 `<td>` 标签定义），表格可以包含标题行（**`<th>`**）用于定义列的标题。

- **tr**：tr 是 table row 的缩写，表示表格的一行。
- **td**：td 是 table data 的缩写，表示表格的数据单元格。
- **th**：th 是 table header的缩写，表示表格的表头单元格。

数据单元格可以包含文本、图片、列表、段落、表单、水平线、表格等等。

```html
<table>
  <thead>
    <tr>
      <th>列标题1</th>
      <th>列标题2</th>
      <th>列标题3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>行1，列1</td>
      <td>行1，列2</td>
      <td>行1，列3</td>
    </tr>
    <tr>
      <td>行2，列1</td>
      <td>行2，列2</td>
      <td>行2，列3</td>
    </tr>
  </tbody>
</table>
```

`<table>` 元素表示整个表格，它包含两个主要部分：`<thead>` 和 `<tbody>`。

- `<thead >` 用于定义表格的标题部分: 在 `<thead > `中，使用 `<th>` 元素定义列的标题，以上实例中列标题分别为"列标题1"，"列标题2"和"列标题3"。
- `<tbody >` 用于定义表格的主体部分: 在 `<tbody> `中，使用 `<tr>` 元素定义行，并在每行中使用 `<td>` 元素定义单元格数据，以上实例中有两行数据，每行包含三个单元格。

通过使用 `<th>` 元素定义列标题，可以使其在表格中以粗体显示，与普通单元格区分开来。

HTML 表格还可以具有其他部分，如 `<tfoot>` （表格页脚）和 `<caption>` （表格标题），`<tfoot> `可用于在表格的底部定义摘要、统计信息等内容。 `<caption>` 可用于为整个表格定义标题。

HTML 表格还支持合并单元格和跨行/跨列的操作，以及其他样式和属性的应用，以满足各种需求。

我们也可以使用 CSS 来进一步自定义表格的样式和外观。

### HTML 表格标签

| 标签         | 描述                 |
| :----------- | :------------------- |
| `<table>`    | 定义表格             |
| `<th>`       | 定义表格的表头       |
| `<tr>`       | 定义表格的行         |
| `<td>`       | 定义表格单元         |
| `<caption>`  | 定义表格标题         |
| `<colgroup>` | 定义表格列的组       |
| `<col>`      | 定义用于表格列的属性 |
| `<thead>`    | 定义表格的页眉       |
| `<tbody>>`   | 定义表格的主体       |
| `<tfoot>`    | 定义表格的页脚       |

## 8.HTML列表

HTML 支持有序、无序和定义列表:

### HTML无序列表

无序列表是一个项目的列表，此列项目使用粗体圆点（典型的小黑圆圈）进行标记。

无序列表使用 `<ul>`标签

```html
<ul>
<li>Coffee</li>
<li>Milk</li>
</ul>
```

浏览器显示如下：

- Coffee
- Milk

### HTML 有序列表

同样，有序列表也是一列项目，列表项目使用数字进行标记。 有序列表始于 `<ol>` 标签。每个列表项始于 `<li> `标签。

列表项使用数字来标记。

```html
<ol>
<li>Coffee</li>
<li>Milk</li>
</ol>
```

浏览器中显示如下：

1. Coffee
2. Milk

### HTML 自定义列表

自定义列表不仅仅是一列项目，而是项目及其注释的组合。

自定义列表以 `<dl> `标签开始。每个自定义列表项以 `<dt>` 开始。每个自定义列表项的定义以 `<dd>` 开始。

```html
<dl>
<dt>Coffee</dt>
<dd>- black hot drink</dd>
<dt>Milk</dt>
<dd>- white cold drink</dd>
</dl>
```

浏览器显示如下：

- Coffee

  - black hot drink

- Milk

  - white cold drink

> **注意事项 - 有用提示**

**提示:** 列表项内部可以使用段落、换行符、图片、链接以及其他列表等等。

## 9.HTML区块

### HTML `<div>` 和`<span>`

HTML 可以通过 `<div>` 和 `<span>`将元素组合起来。

###　HTML 区块元素

大多数 HTML 元素被定义为**块级元素**或**内联元素**。

块级元素在浏览器显示时，通常会以新行来开始（和结束）。

实例: `<h1>`, `<p>`, `<ul>`, `<table>`

### HTML 内联元素

内联元素在显示时通常不会以新行开始。

实例: `<b>`, `<td>`, `<a>`, `<img>`

### HTML`<div>` 元素

HTML `<div>`元素是块级元素，它可用于组合其他 HTML 元素的容器。

`<div>` 元素没有特定的含义。除此之外，由于它属于块级元素，浏览器会在其前后显示折行。

如果与 CSS 一同使用，`<div>` 元素可用于对大的内容块设置样式属性。

`<div>` 元素的另一个常见的用途是文档布局。它取代了使用表格定义布局的老式方法。使用 `<table>` 元素进行文档布局不是表格的正确用法。`<table>` 元素的作用是显示表格化的数据。

###　HTML`<span>` 元素

HTML `<span>` 元素是内联元素，可用作文本的容器。

`<span>` 元素也没有特定的含义。

当与 CSS 一同使用时，`<span>` 元素可用于为部分文本设置样式属性。

## 10.HTML布局

网页布局对改善网站的外观非常重要。

请慎重设计您的网页布局。

### 使用`<div>`元素

div 元素是用于分组 HTML 元素的块级元素。

下面的例子使用五个 div 元素来创建多列布局：

```html
<!DOCTYPE html>
<html>
<head> 
<meta charset="utf-8"> 
<title>菜鸟教程(runoob.com)</title> 
</head>
<body>
 
<div id="container" style="width:500px">
 
<div id="header" style="background-color:#FFA500;">
<h1 style="margin-bottom:0;">主要的网页标题</h1></div>
 
<div id="menu" style="background-color:#FFD700;height:200px;width:100px;float:left;">
<b>菜单</b><br>
HTML<br>
CSS<br>
JavaScript</div>
 
<div id="content" style="background-color:#EEEEEE;height:200px;width:400px;float:left;">
内容在这里</div>
 
<div id="footer" style="background-color:#FFA500;clear:both;text-align:center;">
版权 © runoob.com</div>
 
</div>
 
</body>
</html>
```

### 使用`<table>`元素

使用 HTML `<table>` 标签是创建布局的一种简单的方式。

大多数站点可以使用 `<div>` 或者 `<table>` 元素来创建多列。CSS 用于对元素进行定位，或者为页面创建背景以及色彩丰富的外观。

**即使可以使用 HTML 表格来创建漂亮的布局，但设计表格的目的是呈现表格化数据 - 表格不是布局工具！**

下面的例子使用三行两列的表格 - 第一和最后一行使用 colspan 属性来横跨两列：

```html
<!DOCTYPE html>
<html>
<head> 
<meta charset="utf-8"> 
<title>菜鸟教程(runoob.com)</title> 
</head>
<body>
 
<table width="500" border="0">
<tr>
<td colspan="2" style="background-color:#FFA500;">
<h1>主要的网页标题</h1>
</td>
</tr>
 
<tr>
<td style="background-color:#FFD700;width:100px;">
<b>菜单</b><br>
HTML<br>
CSS<br>
JavaScript
</td>
<td style="background-color:#eeeeee;height:200px;width:400px;">
内容在这里</td>
</tr>
 
<tr>
<td colspan="2" style="background-color:#FFA500;text-align:center;">
版权 © runoob.com</td>
</tr>
</table>
 
</body>
</html>
```

> HTML 布局 - 有用的提示

**Tip:** 使用 CSS 最大的好处是，如果把 CSS 代码存放到外部样式表中，那么站点会更易于维护。通过编辑单一的文件，就可以改变所有页面的布局。

**Tip:** 由于创建高级的布局非常耗时，使用模板是一个快速的选项。通过搜索引擎可以找到很多免费的网站模板（您可以使用这些预先构建好的网站布局，并优化它们）

## 11.HTML表单

HTML 表单用于收集用户的输入信息。

HTML 表单表示文档中的一个区域，此区域包含交互控件，将用户收集到的信息发送到 Web 服务器。

HTML 表单通常包含各种输入字段、复选框、单选按钮、下拉列表等元素。

以下是一个简单的HTML表单的例子：

- `<form>` 元素用于创建表单，`action` 属性定义了表单数据提交的目标 URL，`method` 属性定义了提交数据的 HTTP 方法（这里使用的是 "post"）。
- `<label>` 元素用于为表单元素添加标签，提高可访问性。
- `<input>` 元素是最常用的表单元素之一，它可以创建文本输入框、密码框、单选按钮、复选框等。`type` 属性定义了输入框的类型，`id` 属性用于关联 `<label>` 元素，`name` 属性用于标识表单字段。
- `<select>` 元素用于创建下拉列表，而 `<option>` 元素用于定义下拉列表中的选项。

```html
<form action="/" method="post">
    <!-- 文本输入框 -->
    <label for="name">用户名:</label>
    <input type="text" id="name" name="name" required>

    <br>

    <!-- 密码输入框 -->
    <label for="password">密码:</label>
    <input type="password" id="password" name="password" required>

    <br>

    <!-- 单选按钮 -->
    <label>性别:</label>
    <input type="radio" id="male" name="gender" value="male" checked>
    <label for="male">男</label>
    <input type="radio" id="female" name="gender" value="female">
    <label for="female">女</label>

    <br>

    <!-- 复选框 -->
    <input type="checkbox" id="subscribe" name="subscribe" checked>
    <label for="subscribe">订阅推送信息</label>

    <br>

    <!-- 下拉列表 -->
    <label for="country">国家:</label>
    <select id="country" name="country">
        <option value="cn">CN</option>
        <option value="usa">USA</option>
        <option value="uk">UK</option>
    </select>

    <br>

    <!-- 提交按钮 -->
    <input type="submit" value="提交">
</form>
```

表单是一个包含表单元素的区域。

表单元素是允许用户在表单中输入内容，比如：文本域（textarea）、下拉列表（select）、单选框（radio-buttons）、复选框（checkbox） 等等。

我们可以使用 `<form>`标签来创建表单:

```html
<form>
.
input 元素
.
</form>
```



### HTML 表单 - 输入元素

多数情况下被用到的表单标签是输入标签 `<input>`。

输入类型是由 **type** 属性定义。

接下来我们介绍几种常用的输入类型。

**1.文本域（Text Fields）**

文本域通过 **`<input type="text">`** 标签来设定，当用户要在表单中键入字母、数字等内容时，就会用到文本域。

```html
<form>
First name: <input type="text" name="firstname"><br>
Last name: <input type="text" name="lastname">
</form>
```

**注意**：表单本身并不可见。同时，在大多数浏览器中，文本域的默认宽度是20个字符。

**2.密码字段**

密码字段通过标签 **`<input type="password">`** 来定义:

```html
<form>
Password: <input type="password" name="pwd">
</form>
```

**注意**：密码字段字符不会明文显示，而是以星号 ***** 或圆点 **.** 替代。

**3.单选按钮（Radio Buttons）**

**`<input type="radio">`** 标签定义了表单的单选框选项:

```html
<form action="">
<input type="radio" name="sex" value="male">男<br>
<input type="radio" name="sex" value="female">女
</form>
```

**4.复选框（Checkboxes）**

**`<input type="checkbox">`** 定义了复选框。

复选框可以选取一个或多个选项：

```html
<form>
<input type="checkbox" name="vehicle[]" value="Bike">我喜欢自行车<br>
<input type="checkbox" name="vehicle[]" value="Car">我喜欢小汽车
</form>
```

**5.提交按钮(Submit)**

**`<input type="submit">`** 定义了提交按钮。

当用户单击确认按钮时，表单的内容会被传送到服务器。表单的动作属性 **action** 定义了服务端的文件名。

**action** 属性会对接收到的用户输入数据进行相关的处理:

```html
<form name="input" action="html_form_action.php" method="get">
Username: <input type="text" name="user">
<input type="submit" value="Submit">
</form>
```

假如您在上面的文本框内键入几个字母，然后点击确认按钮，那么输入数据会传送到 **html_form_action.php** 文件，该页面将显示出输入的结果。

以上实例中有一个 method 属性，它用于定义表单数据的提交方式，可以是以下值：

- **post**：指的是 HTTP POST 方法，表单数据会包含在表单体内然后发送给服务器，用于提交敏感数据，如用户名与密码等。
- **get**：默认值，指的是 HTTP GET 方法，表单数据会附加在 **action** 属性的 URL 中，并以 **?**作为分隔符，一般用于不敏感信息，如分页等。例如：`https://www.runoob.com/?page=1`，这里的 page=1 就是 get 方法提交的数据。

```html
<!-- 以下表单使用 GET 请求发送数据到当前的 URL，method 默认位 GET。 -->
<form>
  <label>Name:
    <input name="submitted-name" autocomplete="name">
  </label>
  <button>Save</button>
</form>

<!-- 以下表单使用 POST 请求发送数据到当前的 URL。 -->
<form method="post">
  <label>Name:
    <input name="submitted-name" autocomplete="name">
  </label>
  <button>Save</button>
</form>

<!-- 表单使用 fieldset, legend, 和 label 标签 -->
<form method="post">
  <fieldset>
    <legend>Title</legend>
    <label><input type="radio" name="radio"> Select me</label>
  </fieldset>
</form>
```

## 12.HTML 框架

通过使用框架，你可以在同一个浏览器窗口中显示不止一个页面。

**iframe语法:**

```html
<iframe src="URL"></iframe>
```

该URL指向不同的网页。

### iframe - 设置高度与宽度

height 和 width 属性用来定义iframe标签的高度与宽度。

属性默认以像素为单位, 但是你可以指定其按比例显示 (如："80%")。

```html
<iframe src="demo_iframe.htm" width="200" height="200"></iframe>
```

### iframe - 移除边框

frameborder 属性用于定义iframe表示是否显示边框。

设置属性值为 "0" 移除iframe的边框:

```html
<iframe src="demo_iframe.htm" frameborder="0"></iframe>
```

### iframe-显示目标链接页面

iframe 可以显示一个目标链接的页面

目标链接的属性必须使用 iframe 的属性，如下实例:

```html
<iframe src="demo_iframe.htm" name="iframe_a"></iframe>
<p><a href="https://www.runoob.com" target="iframe_a" rel="noopener">RUNOOB.COM</a></p>
```



> 出于有些网页不希望被嵌套, 响应头中有一选项:

```
X-Frame-Options
```

他有三个可配置值

```html
DENY：表示该网站页面不允许被嵌套，即便是在自己的域名的页面中也不能进行嵌套。
SAMEORIGIN：表示该页面可以在相同域名页面中被嵌套展示。
ALLOW-FROM uri：表示该页面可以在指定来源页面中进行嵌套展示。
```

## 13.HTML颜色

HTML 颜色由红色、绿色、蓝色混合而成。

HTML 颜色由一个十六进制符号来定义，这个符号由红色、绿色和蓝色的值组成（RGB）。

每种颜色的最小值是0（十六进制：#00）。最大值是255（十六进制：#FF）。

RGBA 的意思是（Red-Green-Blue-Alpha）它是在 RGB 上扩展包括了 **“alpha”** 通道，运行对颜色值设置透明度。

```css
div {

background:rgba(255,0,0,0.5);

}
```

相对于使用 rgb(255,255,0)，使用 rgba(255,255,0,0.5) 可以实现设置颜色透明度的功能，这里的 0.5 表示透明度，范围 0~1，0 表示全透明。

通常我们为了省略一个 0:

```css
div {
    background:rgba(255,0,0,.5);
}
```

实例：

```html
<p style="background-color:rgb(255,255,0)">
通过 rbg 值设置背景颜色
</p>
<p style="background-color:rgba(255,255,0,0.25)">
通过 rbg 值设置背景颜色
</p>
<p style="background-color:rgba(255,255,0,0.5)">
通过 rbg 值设置背景颜色
</p>
<p style="background-color:rgba(255,255,0,0.75)">
通过 rbg 值设置背景颜色
</p>
```

## 14.HTML脚本

### HTML `<script>` 标签

`<script>` 标签用于定义客户端脚本，比如 JavaScript。

`<script>` 元素既可包含脚本语句，也可通过 src 属性指向外部脚本文件。

JavaScript 最常用于图片操作、表单验证以及内容动态更新。

下面的脚本会向浏览器输出"Hello World!"：

```html
<script>
document.write("Hello World!");
</script>
```

### HTML`<noscript>` 标签

`<noscript> `标签提供无法使用脚本时的替代内容，比方在浏览器禁用脚本时，或浏览器不支持客户端脚本时。

`<noscript>`元素可包含普通 HTML 页面的 body 元素中能够找到的所有元素。

只有在浏览器不支持脚本或者禁用脚本时，才会显示 `<noscript>` 元素中的内容：

```html
<script>
document.write("Hello World!")
</script>
<noscript>抱歉，你的浏览器不支持 JavaScript!</noscript>
```

您只能在 HTML 输出流中使用 **document.write**。 如果您在文档已加载后使用它（比如在函数中），会覆盖整个文档。

## 15.HTML字符实体

HTML 中的预留字符必须被替换为字符实体。

一些在键盘上找不到的字符也可以使用字符实体来替换。

### HTML 实体

在 HTML 中，某些字符是预留的。

在 HTML 中不能使用小于号（<）和大于号（>），这是因为浏览器会误认为它们是标签。

如果希望正确地显示预留字符，我们必须在 HTML 源代码中使用字符实体（character entities）。 字符实体类似这样：

```html
&entity_name;

<!-- 或 -->

&#entity_number;
```

如需显示小于号，我们必须这样写：`&lt;` 或`&#60; `  或  `&#060`

**提示**： 使用实体名而不是数字的好处是，名称易于记忆。不过坏处是，浏览器也许并不支持所有实体名称（对实体数字的支持却很好）。

### 不间断空格

HTML 中的常用字符实体是不间断空格(&nbsp;)。

浏览器总是会截短 HTML 页面中的空格。如果您在文本中写 10 个空格，在显示该页面之前，浏览器会删除它们中的 9 个。如需在页面中增加空格的数量，可以用以下转义字符分隔字符

`&nbsp;` , `&ensp;` , `&emsp;` , `&thinsp;` , `&zwnj;` ,`&zwj;`

**1.`&nbsp;`**

`&nbsp;`的宽度，可运行于所有主流浏览器。其他几种空格（ `&ensp;` , `&emsp;` , `&thinsp;` , `&zwnj;` ,`&zwj;`）在不同浏览器中宽度各异。

`&nbsp;`  受font-size影响, 受letter-spacing和word-spacing影响;
另外5个,受font-size影响, 不受letter-spacing和word-spacing影响;

`&nbsp;` 不换行空格,默认四分之一em
全称No-Break Space，它是最常见和我们使用最多的空格，大多数的人可能只接触了&nbsp;，它是按下space键产生的空格。在HTML中，如果你用空格键产生此空格，空格是不会累加的（只算1个）。要使用html实体表示才可累加，该空格占据宽度受字体影响明显而强烈。
`&nbsp;`受css的word-spacing和letter-spacing控制, 其它不受;
`&nbsp;`等效Unicode的不间断空格: 十六进制写法`&#xA0;` , 十进制写法`&#160`;

**2.`&ensp;`**

`&ensp;` 半角空格,半个em
全称是En Space，en是字体排印学的计量单位，为em宽度的一半。根据定义，它等同于字体度的一半（如16px字体中就是8px）。名义上是小写字母n的宽度。
此空格传承空格家族一贯的特性：透明的，
此空格有个相当稳健的特性，就是其 占据的宽度正好是1/2个中文宽度，而且基本上不受字体影响。
受font-size影响, 不受letter-spacing和word-spacing影响;

**3.`&emsp;`**

`&emsp;` 全角空格,一个em
全称是Em Space，em是字体排印学的计量单位，相当于当前指定的点数。例如，1 em在16px的字体中就是16px。
此空格也传承空格家族一贯的特性：透明的，
此空格也有个相当稳健的特性，就是其 占据的宽度正好是1个中文宽度，而且基本上不受字体影响。
受font-size影响, 不受letter-spacing和word-spacing影响;

**4.`&thinsp;`** 

`&thinsp;` 窄空格符,瘦弱空格符,六分之一em
全称是Thin Space。瘦弱空格，就是该空格长得比较瘦弱，身体单薄，占据的宽度比较小。它是em之六分之一宽。
受font-size影响, 不受letter-spacing和word-spacing影响

**5.`&zwnj;`**‌

`&zwnj;`‌零宽不连字符
全称是Zero Width Non Joiner，是一个不打印字符，放在电子文本的两个字符之间，抑制本来会发生的连字，而是以这两个字符原本的字形来绘制。Unicode中的零宽不连字字符映射为“”（zero width non-joiner，U+200C），HTML字符值引用为： ‌
受font-size影响, 不受letter-spacing和word-spacing影响;

**6.`&zwj;`**

`&zwj;` 零宽连字符
全称是Zero Width Joiner，是一个不打印字符，放在某些需要复杂排版语言（如阿拉伯语、印地语）的两个字符之间，使得这两个本不会发生连字的字符产生了连字效果。零宽连字符的Unicode码位是U+200D 。
受font-size影响, 不受letter-spacing和word-spacing影响;




### 结合音标符

发音符号是加到字母上的一个"glyph(字形)"。

一些变音符号, 如 尖音符 ( ̀) 和 抑音符 ( ́) 。

变音符号可以出现字母的上面和下面，或者字母里面，或者两个字母间。

变音符号可以与字母、数字字符的组合来使用。

以下是一些实例:

| 音标符 | 字符 | Construct | 输出结果 |
| :----- | :--- | :-------- | :------- |
| ̀       | a    | `&#768`;  | à        |
| ́       | a    | `&#769`;  | á        |
| ̂       | a    | `&#770`;  | â        |
| ̃       | a    | `&#771`;  | ã        |
| ̀       | O    | `&#768`;  | Ò        |
| ́       | O    | `&#769`;  | Ó        |
| ̂       | O    | `&#770`;  | Ô        |
| ̃       | O    | `&#771`;  | Õ        |

### HTML字符实体

实体名称对大小写敏感！

[HTML ISO-8859-1 参考手册](https://www.runoob.com/tags/ref-entities.html)

## 16.HTML URL

URL 是一个网页地址。

URL可以由字母组成，如`runoob.com`，或互联网协议（IP）地址： `192.68.20.50`。大多数人进入网站使用网站域名来访问，因为名字比数字更容易记住。

### URL - 统一资源定位器

Web浏览器通过URL从Web服务器请求页面。

当您点击 HTML 页面中的某个链接时，对应的 `<a>` 标签指向万维网上的一个地址。

一个统一资源定位器(URL) 用于定位万维网上的文档。

一个网页地址实例: http://www.runoob.com/html/html-tutorial.html 语法规则:

```html
scheme://host.domain:port/path/filename
```

**说明:**

- scheme - 定义因特网服务的类型。最常见的类型是 http

- host - 定义域主机（http 的默认主机是 www）

- domain - 定义因特网域名，比如 runoob.com

- :port - 定义主机上的端口号（http 的默认端口号是 80）

- path - 定义服务器上的路径（如果省略，则文档必须位于网站的根目录中）。

- filename - 定义文档/资源的名称

### 常见的 URL Scheme

以下是一些URL scheme：

| Scheme | 访问               | 用于...                             |
| :----- | :----------------- | :---------------------------------- |
| http   | 超文本传输协议     | 以 http:// 开头的普通网页。不加密。 |
| https  | 安全超文本传输协议 | 安全网页，加密所有信息交换。        |
| ftp    | 文件传输协议       | 用于将文件下载或上传至网站。        |
| file   |                    | 您计算机上的文件。                  |

### URL 字符编码

URL 只能使用 [ASCII 字符集](https://www.runoob.com/tags/html-ascii.html).

来通过因特网进行发送。由于 URL 常常会包含 ASCII 集合之外的字符，URL 必须转换为有效的 ASCII 格式。

URL 编码使用 "%" 其后跟随两位的十六进制数来替换非 ASCII 字符。

URL 不能包含空格。URL 编码通常使用 + 来替换空格。

## 17.HTML 标签简写及全称

下表列出了 HTML 标签简写及全称：

| 标签        | 英文全称                  | 中文说明                       |
| :---------- | :------------------------ | :----------------------------- |
| a           | Anchor                    | 锚                             |
| abbr        | Abbreviation              | 缩写词                         |
| acronym     | Acronym                   | 取首字母的缩写词               |
| address     | Address                   | 地址                           |
| alt         | alter                     | 替用(一般是图片显示不出的提示) |
| b           | Bold                      | 粗体（文本）                   |
| bdo         | Bi-Directional Override   | 文本显示方向                   |
| big         | Big                       | 变大（文本）                   |
| blockquote  | Block Quotation           | 区块引用语                     |
| br          | Break                     | 换行                           |
| cell        | cell                      | 巢                             |
| cellpadding | cellpadding               | 巢补白                         |
| cellspacing | cellspacing               | 巢空间                         |
| center      | Centered                  | 7居中（文本）                  |
| cite        | Citation                  | 引用                           |
| code        | Code                      | 源代码（文本）                 |
| dd          | Definition Description    | 定义描述                       |
| del         | Deleted                   | 删除（的文本）                 |
| dfn         | Defines a Definition Term | 定义定义条目                   |
| div         | Division                  | 分隔                           |
| dl          | Definition List           | 定义列表                       |
| dt          | Definition Term           | 定义术语                       |
| em          | Emphasized                | 加重（文本）                   |
| font        | Font                      | 字体                           |
| h1~h6       | Header 1 to Header 6      | 标题1到标题6                   |
| hr          | Horizontal Rule           | 水平尺                         |
| href        | hypertext reference       | 超文本引用                     |
| i           | Italic                    | 斜体（文本）                   |
| iframe      | Inline frame              | 定义内联框架                   |
| ins         | Inserted                  | 插入（的文本）                 |
| kbd         | Keyboard                  | 键盘（文本）                   |
| li          | List Item                 | 列表项目                       |
| nl          | navigation lists          | 导航列表                       |
| ol          | Ordered List              | 排序列表                       |
| optgroup    | Option group              | 定义选项组                     |
| p           | Paragraph                 | 段落                           |
| pre         | Preformatted              | 预定义格式（文本 ）            |
| q           | Quotation                 | 引用语                         |
| rel         | Reload                    | 加载                           |
| s/ strike   | Strikethrough             | 删除线                         |
| samp        | Sample                    | 示例（文本                     |
| small       | Small                     | 变小（文本）                   |
| span        | Span                      | 范围                           |
| src         | Source                    | 源文件链接                     |
| strong      | Strong                    | 加重（文本）                   |
| sub         | Subscripted               | 下标（文本）                   |
| sup         | Superscripted             | 上标（文本）                   |
| td          | table data cell           | 表格中的一个单元格             |
| th          | table header cell         | 表格中的表头                   |
| tr          | table row                 | 表格中的一行                   |
| tt          | Teletype                  | 打印机（文本）                 |
| u           | Underlined                | 下划线（文本）                 |
| ul          | Unordered List            | 不排序列表                     |
| var         | Variable                  | 变量（文本）                   |







# 三、HTML5

## 1.HTML5 Canvas

[canvas参考手册](https://www.runoob.com/tags/ref-canvas.html)

`<canvas>` 标签定义图形，比如图表和其他图像，您必须使用脚本来绘制图形。

在画布上（Canvas）画一个红色矩形，渐变矩形，彩色矩形，和一些彩色的文字。

HTML5 `<canvas>` 元素用于图形的绘制，通过脚本 (通常是JavaScript)来完成.

`<canvas>` 标签只是图形容器，您必须使用脚本来绘制图形。

你可以通过多种方法使用 canvas 绘制路径,盒、圆、字符以及添加图像。

### 创建一个画布（Canvas）

一个画布在网页中是一个矩形框，通过 `<canvas>` 元素来绘制.

**注意:** 默认情况下 `<canvas>` 元素没有边框和内容。

`<canvas>`简单实例如下:

```html
<canvas id="myCanvas" width="200" height="100"></canvas>
```

**注意:** 标签通常需要指定一个id属性 (脚本中经常引用), width 和 height 属性定义的画布的大小.

**提示:**你可以在HTML页面中使用多个 `<canvas>` 元素.

使用 style 属性来添加边框:

```html
<canvas id="myCanvas" width="200" height="100"
style="border:1px solid #000000;">
</canvas>
```

### 使用 JavaScript 来绘制图像

canvas 元素本身是没有绘图能力的。所有的绘制工作必须在 JavaScript 内部完成：

```html
<script>
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
ctx.fillStyle="#FF0000";
ctx.fillRect(0,0,150,75);
</script>
```

**实例解析:**

首先，找到 `<canvas>` 元素:

```js
var c=document.getElementById("myCanvas");
```

然后，创建 context 对象：

```js
var ctx=c.getContext("2d");
```

getContext("2d") 对象是内建的 HTML5 对象，拥有多种绘制路径、矩形、圆形、字符以及添加图像的方法。

下面的两行代码绘制一个红色的矩形：

```js
ctx.fillStyle="#FF0000";
ctx.fillRect(0,0,150,75);
```

设置fillStyle属性可以是CSS颜色，渐变，或图案。fillStyle 默认设置是#000000（黑色）。

`fillRect(x,y,width,height)` 方法定义了矩形当前的填充方式。

**关于canvas坐标：**

> canvas 是一个二维网格。
>
> canvas 的左上角坐标为 (0,0)
>
> 上面的 fillRect 方法拥有参数 (0,0,150,75)。
>
> 意思是：在画布上绘制 150x75 的矩形，从左上角开始 (0,0)。

### Canvas - 路径

在Canvas上画线，我们将使用以下两种方法：

- moveTo(*x,y*) 定义线条开始坐标
- lineTo(*x,y*) 定义线条结束坐标

绘制线条我们必须使用到 "ink" 的方法，就像stroke().

**1.绘制线条:**

```js
//stroke() 方法
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
ctx.moveTo(0,0);
ctx.lineTo(200,100);
ctx.stroke();
```

**2.绘制圆形:**

```js
//arc(x,y,r,start,stop)
//实际上我们在绘制圆形时使用了 "ink" 的方法, 比如 stroke() 或者 fill().
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
ctx.beginPath();
ctx.arc(95,50,40,0,2*Math.PI);
ctx.stroke();
```

### Canvas - 文本

使用 canvas 绘制文本，重要的属性和方法如下：

- font - 定义字体
- fillText(*text,x,y*) - 在 canvas 上绘制实心的文本
- strokeText(*text,x,y*) - 在 canvas 上绘制空心的文本

**1.使用 fillText():**

```js
//使用 "Arial" 字体在画布上绘制一个高 30px 的文字（实心）：
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
ctx.font="30px Arial";
ctx.fillText("Hello World",10,50);
```

**2.使用 strokeText():**

```js
//使用 "Arial" 字体在画布上绘制一个高 30px 的文字（空心）：
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
ctx.font="30px Arial";
ctx.strokeText("Hello World",10,50);
```

### Canvas - 渐变

渐变可以填充在矩形, 圆形, 线条, 文本等等, 各种形状可以自己定义不同的颜色。

以下有两种不同的方式来设置Canvas渐变：

- createLinearGradient(*x,y,x1,y1*) - 创建线条渐变
- createRadialGradient(*x,y,r,x1,y1,r1*) - 创建一个径向/圆渐变

当我们使用渐变对象，必须使用两种或两种以上的停止颜色。

addColorStop()方法指定颜色停止，参数使用坐标来描述，可以是0至1.

使用渐变，设置fillStyle或strokeStyle的值为 渐变，然后绘制形状，如矩形，文本，或一条线。

**1.使用 createLinearGradient():**

```js
//创建一个线性渐变。使用渐变填充矩形:

var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
 
// 创建渐变
var grd=ctx.createLinearGradient(0,0,200,0);
grd.addColorStop(0,"red");
grd.addColorStop(1,"white");
 
// 填充渐变
ctx.fillStyle=grd;
ctx.fillRect(10,10,150,80);
```

**2.使用 createRadialGradient():**

```js
//创建一个径向/圆渐变。使用渐变填充矩形：
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
 
// 创建渐变
var grd=ctx.createRadialGradient(75,50,5,90,60,100);
grd.addColorStop(0,"red");
grd.addColorStop(1,"white");
 
// 填充渐变
ctx.fillStyle=grd;
ctx.fillRect(10,10,150,80);
```

### Canvas - 图像

把一幅图像放置到画布上, 使用以下方法:

- drawImage(*image,x,y*)

```js
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
var img=document.getElementById("scream");
ctx.drawImage(img,10,10);
//stream是图像名字
```

## 2.HTML5 SVG

SVG 定义为可缩放矢量图形。

HTML5 支持内联 SVG。

HTML **`<svg>`** 元素是 SVG 图形的容器。

SVG 有多种绘制路径、框、圆、文本和图形图像的方法。

# 四、项目

## 1.学成在线官网

```html
/* html */
<!DOCTYPE html>
<html>
  <head>
    <title>学成在线官网</title>
    <meta charset="utf-8"></meta>
    <link rel="stylesheet" href="xuechengzaixian.css">
  </head>
  <body>
  <!-- 头部区域-->
    <div class="header w">
      <!-- logo部分 -->
        <div class="logo">
          <img src="image_xuechengzaixian/logo.png" alt="">
        </div>
      <!-- 导航栏部分 -->
        <div class="nav">
          <ul>
            <li><a href="#">首页</a></li>
            <li><a href="#">课程</a></li>
            <li><a href="#">职业规划</a></li>
          </ul>
        </div>
      <!-- 搜索模块-->
        <div class="search">
          <input type="text" value="输入关键词">
          <button></button>
        </div>
      <!-- 用户模块-->
        <div class="user">
          <img src="image/mosi.PNG" alt="">
          qiqizizzz
        </div>
    </div>
  <!-- banner部分-->
   <div class="banner">
      <div class="w">
        <div class="subnav">
          <ul>
            <li><a href="#">前端开发<span>></span></a></li>
            <li><a href="#">后端开发<span>></span></a></li>
            <li><a href="#">移动开发<span>></span></a></li>
            <li><a href="#">人工智能<span>></span></a></li>
            <li><a href="#">商业预测<span>></span></a></li>
            <li><a href="#">云计算&大数据<span>></span></a></li>
            <li><a href="#">运维&测试<span>></span></a></li>
            <li><a href="#">UI设计<span>></span></a></li>
            <li><a href="#">产品<span>></span></a></li>
          </ul>
        </div>
        <div class="course">
          <h2>我的课程表</h2>
          <div class="bd">
            <ul>
              <li>
                <h4>继续学习 程序语言设计</h4>
                <p>正在学习--使用对象</p>
              </li>
              <li>
                <h4>继续学习 程序语言设计</h4>
                <p>正在学习--使用对象</p>
              </li>
              <li>
                <h4>继续学习 程序语言设计</h4>
                <p>正在学习--使用对象</p>
              </li>
            </ul>
            <a href="#" class="more">全部课程</a>
          </div>
        </div>
      </div>
   </div>
   <!-- 精品推荐模块-->
    <div class="goods w">
      <h3>精品推荐</h3>
      <ul>
        <li><a href="#">JQuery</a></li>
        <li><a href="#">Spark</a></li>
        <li><a href="#">MySQL</a></li>
        <li><a href="#">JavaWeb</a></li>
        <li><a href="#">HTML5</a></li>
      </ul>
      <a href="#" class="mod">修改兴趣</a>
    </div>
    <!-- box核心区域-->
    <div class="box w">
      <div class="box-hd">
        <h3>精品推荐</h3>
        <a href="#">查看全部</a>
      </div>
      <div class="box-bd">
        <ul>
          <li>
            <img src="image_xuechengzaixian/pic.png">
            <h4>Think PHP 5.0 博客系统实战项目演练</h4>
            <div class="info">
              <span>高级</span> * 123人在学习
            </div>
          </li>
          <li>
            <img src="image_xuechengzaixian/pic.png">
            <h4>Think PHP 5.0 博客系统实战项目演练</h4>
            <div class="info">
              <span>高级</span> * 123人在学习
            </div>
          </li>
          <li>
            <img src="image_xuechengzaixian/pic.png">
            <h4>Think PHP 5.0 博客系统实战项目演练</h4>
            <div class="info">
              <span>高级</span> * 123人在学习
            </div>
          </li>
          <li>
            <img src="image_xuechengzaixian/pic.png">
            <h4>Think PHP 5.0 博客系统实战项目演练</h4>
            <div class="info">
              <span>高级</span> * 123人在学习
            </div>
          </li>
          <li>
            <img src="image_xuechengzaixian/pic.png">
            <h4>Think PHP 5.0 博客系统实战项目演练</h4>
            <div class="info">
              <span>高级</span> * 123人在学习
            </div>
          </li>
          <li>
            <img src="image_xuechengzaixian/pic.png">
            <h4>Think PHP 5.0 博客系统实战项目演练</h4>
            <div class="info">
              <span>高级</span> * 123人在学习
            </div>
          </li>
          <li>
            <img src="image_xuechengzaixian/pic.png">
            <h4>Think PHP 5.0 博客系统实战项目演练</h4>
            <div class="info">
              <span>高级</span> * 123人在学习
            </div>
          </li>
          <li>
            <img src="image_xuechengzaixian/pic.png">
            <h4>Think PHP 5.0 博客系统实战项目演练</h4>
            <div class="info">
              <span>高级</span> * 123人在学习
            </div>
          </li>
          <li>
            <img src="image_xuechengzaixian/pic.png">
            <h4>Think PHP 5.0 博客系统实战项目演练</h4>
            <div class="info">
              <span>高级</span> * 123人在学习
            </div>
          </li>
          <li>
            <img src="image_xuechengzaixian/pic.png">
            <h4>Think PHP 5.0 博客系统实战项目演练</h4>
            <div class="info">
              <span>高级</span> * 123人在学习
            </div>
          </li>
        </ul>
      </div>
    </div>
     <!-- footer版块-->
    <div class="footer">
      <div class="w">
        <div class="copyright">
          <img src="image_xuechengzaixian/logo.png" alt="">
          <p>学成在线致力于普及中国最好的教育它与中国一流大学和机构合作提供在线课程。<br>
            © 2017年XTCG Inc.保留所有权利。-沪ICP备15025210号</p>
          <a href="#" class="app">下载APP</a>
        </div>
        <div class="links">
          <dl>
            <dt>关于学成网</dt>
              <dd><a href="#">关于</a></dd>
              <dd><a href="#">管理团队</a></dd>
              <dd><a href="#">工作机会</a></dd>
              <dd><a href="#">客户服务</a></dd>
              <dd><a href="#">帮助</a></dd>
          </dl>
          <dl>
            <dt>新手指南</dt>
              <dd><a href="#">如何注册</a></dd>
              <dd><a href="#">如何选课</a></dd>
              <dd><a href="#">如何拿到毕业证</a></dd>
              <dd><a href="#">学分是什么</a></dd>
              <dd><a href="#">考试未通过怎么办</a></dd>
          </dl>
          <dl>
            <dt>合作伙伴</dt>
              <dd><a href="#">合作机构</a></dd>
              <dd><a href="#">合作导师</a></dd>
          </dl>
        </div>
      </div>
    </div>
  </body>
</html>
```

```css
/* css */
*{
  padding: 0;  
  margin: 0;
}
.w{
  width: 1200px;
  height: 3000px;
  margin: auto;
}
body{
  background-color: #f3f5f7;
}
li{
  list-style: none;
}
a{
  text-decoration: none;
}
.clearfix:before,.clearfix:after{
	content:"";
	display:table;
}
.clearfix:after{
	clear:both;
}
.clearfix{
	zoom:1;
}
.header{
  height: 42px;
  margin: 30px auto; /*此区域会层叠w里面的margin*/
}
.logo{
  float: left;
  width: 198px;
  height: 42px;
}
.nav{
  float: left;
  margin-left: 60px;
}
.nav ul li{
  float: left;
  margin: 0 15px;
}
.nav ul li a{
  display: block;
  height: 42px;
  padding: 0 10px;
  line-height: 42px;
  font-size: 18px;
  color: #050505;
}
.nav ul li a:hover{
  border-bottom:2px solid #00a4ff ;
}
.search{
  float: left;
  width: 412px;
  height: 42px;
  margin-left: 70px;
}
.search input{
  float: left;
  width: 345px;
  height: 40px;
  border: 2px solid #00a4ff;
  border-right: 0;
  color: #bfbfbf;
  font-size: 14px;
  padding-left: 15px;
}
.search button{
  float: left;
  width: 50px;
  height: 44px;
  border: 0;
  background: url(image_xuechengzaixian/btn.png);
}
.user{
  float: right;
  height: 42px;
  margin-right: 30px;
  font-size: 14px;
  color: #666;
}
.user img{
  width: 20px;
  height: 20px;
}
.banner{
  height: 421px;
  background-color: rgb(28, 3, 108);
}
.banner .w{
  height: 421px;
  background:url(image_xuechengzaixian/banner2.png) no-repeat top center;
}
.subnav{
  float: left;
  width: 190px;
  height: 421px;
  background-color: rgba(0,0,0,0.3);
}
.subnav ul li{
  height: 45px;
  line-height: 45px;
  padding: 0 20px;
}
.subnav ul li a{
  font-size: 14px;
  color: #fff;
}
.subnav ul li a:hover{
  color:#00a4ff;
}
.subnav ul li a span{
  float: right;
}
.course{
  float: right;
  width: 230px;
  height: 300px;
  margin-top: 50px;
  background-color: white;
}
.course h2{
  height: 48px;
  background-color: #9bceea;
  text-align: center;
  line-height: 48px;
  font-size: 18px;
  color: #fff;
}
.bd{
  padding: 0 20px;
}
.bd ul li{
  padding: 14px 0;
  border-bottom: 1px solid #ccc;
}
.bd ul li h4{
  font-size: 16px;
  color:#4e4e4e
}
.bd ul li p{
  font-size: 12px;
  color: #a5a5a5;
}
.bd .more{
  display: block;
  height: 38px;
  border: 2px solid #00a4ff;
  text-align: center;
  line-height: 38px;
  color: #00a4ff;
  font-size: 16px;
}
.goods{
  height: 60px;
  line-height: 60px;
  background-color: #fff;
  margin-top:10px ;
  box-shadow: 0 2px 3px 3px rgba(0,0,0,0.1);
}
.goods h3{
  float: left;
  margin-left: 30px;
  font-size: 16px;
  color: #00a4ff;
}
.goods ul{
  float:left;
  margin-left: 30px;
}
.goods ul li{
  float: left;
}
.goods ul li a{
  padding: 0 30px;
  font-size: 16px;
  color: #050505;
  border-left: 1px solid #ccc;

}
.mod{
  float: right;
  margin-right: 30px;
  font-size: 14px;
  color: #00a4ff;
}
.box{
  margin-top: 30px;
}
.box-hd{
  height: 45px;
}
.box-hd h3{
  float: left;
  font-size: 20px;
  color: #494949;
}
.box-hd a{
  float: right;
  font-size: 12px;
  color: #a5a5a5;
  margin-top: 10px;
  margin-right: 30px;
}
.box-bd ul{
  width: 1225px;
}
/*增大ul的宽度防止孩子掉下来*/
.box-bd ul li{
  float: left;
  height: 270px;
  width: 228px;
  background-color: #fff;
  margin-right: 15px;
  margin-bottom: 15px;
}
.box-bd ul li img{
  width: 228px;
}
.box-bd ul li h4{
  margin: 20px 20px 20px 25px;
  font-size: 14px;
  font-weight: 400;
}
.box-bd .info{
  margin: 0 20px 0 25px;
  font-size: 12px;
  color: #999;
}
.box-bd .info span{
  color: #ff7c2d;
}
.footer{
  height: 415px;
  background-color: #fff;
}
.footer .w{
  padding-top: 35px;
}
.copyright{
  float: left;
}
.copyright p{
  margin:20px 0 15px 0 ;
  font-size: 12px;
  color: #666;
}
.copyright .app{
  display: block;
  width: 118px;
  height: 33px;
  text-align: center;
  line-height: 33px;
  color: #00a4ff;
  font-size: 16px;
  border: 2px solid #00a4ff;
}
.links{
  float: right;
}
.links dl{
  float: left;
  margin-left: 100px;
}
.links dl dt{
  font-size: 16px;
  color: #333;
  margin-bottom: 5px;
}
.links dl dd a{
  color: #333;
  font-size: 12px;
}
```
