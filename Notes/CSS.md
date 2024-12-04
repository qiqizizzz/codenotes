# 一、CSS

## 0.CSS属性书写顺序

建议遵循以下顺序:

1. 布局定位属性:display/position/float/clear /visibility/overflow(建议 display第一个写,毕竟关系到模式)
2. 自身属性 :width/height/margin/padding/border/background
3. 文本属性 : color / font / text-decoration/text-align/vertical-align/white- space / break-word
4. 其他属性 ( CSS3 ): content /cursor / border-radius/ box-shadow / text-shadow/ backaround:linear-gradient..

## 1.CSS 语法

### CSS实例

CSS声明总是以分号 **;** 结束，声明总以大括号 **{}** 括起来:

```css
p 
{
    color:red;
    text-align:center;
}
```

### CSS 注释

注释是用来解释你的代码，并且可以随意编辑它，浏览器会忽略它。

CSS注释以 **/*** 开始, 以 ***/** 结束, 实例如下:

```css
/*这是个注释*/
p
{
    text-align:center;
    /*这是另一个注释*/
    color:black;
    font-family:arial;
}
```

## 2.CSS id 和 class

如果你要在HTML元素中设置CSS样式，你需要在元素中设置"id" 和 "class"选择器。

### id 选择器

id 选择器可以为标有特定 id 的 HTML 元素指定特定的样式。

HTML元素以id属性来设置id选择器,CSS 中 id 选择器以 "#" 来定义。

以下的样式规则应用于元素属性 id="para1":

```css
#para1
{
    text-align:center;
    color:red;
}
```

> ID属性不要以数字开头，数字开头的ID在 Mozilla/Firefox 浏览器中不起作用。

### class 选择器

class 选择器用于描述一组元素的样式，class 选择器有别于id选择器，class可以在多个元素中使用。

class 选择器在 HTML 中以 class 属性表示, 在 CSS 中，类选择器以一个点 **`.`** 号显示：

在以下的例子中，所有拥有 center 类的 HTML 元素均为居中。

```css
.center {text-align:center;}
```

你也可以指定特定的 HTML 元素使用 class。

在以下实例中, 所有的 p 元素使用 class="center" 让该元素的文本居中:

```css
p.center {text-align:center;}
```

多个 class 选择器可以使用空格分开：

```css
.center { text-align:center; }
.color { color:#ff0000; }
<p class="center color">段落居中，颜色为红色。</p> 
```

## 3.CSS 创建

当读到一个样式表时，浏览器会根据它来格式化 HTML 文档。

**如何插入样式表**

插入样式表的方法有三种:

- 外部样式表(External style sheet)
- 内部样式表(Internal style sheet)
- 内联样式(Inline style)

### 外部样式表

当样式需要应用于很多页面时，外部样式表将是理想的选择。在使用外部样式表的情况下，你可以通过改变一个文件来改变整个站点的外观。每个页面使用 `<link>` 标签链接到样式表。 `<link> `标签在（文档的）头部：

```css
<head>
<link rel="stylesheet" type="text/css" href="mystyle.css">
</head>
```

浏览器会从文件 mystyle.css 中读到样式声明，并根据它来格式文档。

外部样式表可以在任何文本编辑器中进行编辑。文件不能包含任何的 html 标签。样式表应该以 .css 扩展名进行保存。下面是一个样式表文件的例子：

```css
hr {color:sienna;}
p {margin-left:20px;}
body {background-image:url("/images/back40.gif");}
```

> 不要在属性值与单位之间留有空格（如："margin-left: 20 px" ），正确的写法是 "margin-left: 20px" 。

### 内部样式表

当单个文档需要特殊的样式时，就应该使用内部样式表。你可以使用 `<style>` 标签在文档**头部**定义内部样式表，就像这样:

```css
<head>
<style>
hr {color:sienna;}
p {margin-left:20px;}
body {background-image:url("images/back40.gif");}
</style>
</head>
```

### 行内样式表

> 也叫做内联样式

由于要将表现和内容混杂在一起，内联样式会损失掉样式表的许多优势。请慎用这种方法，例如当样式仅需要在一个元素上应用一次时。

要使用内联样式，你需要在相关的标签内使用样式（style）属性。Style 属性可以包含任何 CSS 属性。本例展示如何改变段落的颜色和左外边距：

```css
<p style="color:sienna;margin-left:20px">这是一个段落。</p>
```

### 多重样式

如果某些属性在不同的样式表中被同样的选择器定义，那么属性值将从更具体的样式表中被继承过来。 

例如，外部样式表拥有针对 h3 选择器的三个属性：

```css
h3
{
    color:red;
    text-align:left;
    font-size:8pt;
}
```

而内部样式表拥有针对 h3 选择器的两个属性：

```css
h3
{
    text-align:right;
    font-size:20pt;
}
```

假如拥有内部样式表的这个页面同时与外部样式表链接，那么 h3 得到的样式是：

```css
color:red;
text-align:right;
font-size:20pt;
```

即颜色属性将被继承于外部样式表，而文字排列（text-alignment）和字体尺寸（font-size）会被内部样式表中的规则取代。

### 多重样式优先级

样式表允许以多种方式规定样式信息。样式可以规定在单个的 HTML 元素中，在 HTML 页的头元素中，或在一个外部的 CSS 文件中。甚至可以在同一个 HTML 文档内部引用多个外部样式表。

一般情况下，优先级如下：

**（内联样式）`Inline style` > （内部样式）`Internal style sheet` >（外部样式）`External style sheet` > 浏览器默认样式**

**注意**：如果外部样式放在内部样式的后面，则外部样式将覆盖内部样式。

[CSS 样式优先级](https://www.runoob.com/w3cnote/css-style-priority.html)



**多重样式优先级深入概念**

优先级是浏览器是通过判断哪些属性值与元素最相关以决定并应用到该元素上的。优先级仅由选择器组成的匹配规则决定的。

优先级就是分配给指定的CSS声明的一个权重，它由匹配的选择器中的每一种选择器类型的数值决定。

**1.优先级顺序**

下列是一份优先级逐级增加的选择器列表：

- 通用选择器（*）
- 元素(类型)选择器
- 类选择器
- 属性选择器
- 伪类
- ID 选择器
- 内联样式

**2.!important 规则例外**

当 !important 规则被应用在一个样式声明中时,该样式声明会覆盖CSS中任何其他的声明, 无论它处在声明列表中的哪里. 尽管如此, !important规则还是与优先级毫无关系.使用 !important 不是一个好习惯，因为它改变了你样式表本来的级联规则，从而使其难以调试。

一些经验法则：

- **Always** 要优化考虑使用样式规则的优先级来解决问题而不是 `!important`
- **Only** 只在需要覆盖全站或外部 css（例如引用的 ExtJs 或者 YUI ）的特定页面中使用 `!important`
- **Never** 永远不要在全站范围的 css 上使用` !important`
- **Never** 永远不要在你的插件中使用 `!important`

**3.CSS 优先级法则：**

-  A 选择器都有一个权值，权值越大越优先；
-  B 当权值相等时，后出现的样式表设置要优于先出现的样式表设置；
-  C 创作者的规则高于浏览者：即网页编写者设置的CSS 样式的优先权高于浏览器所设置的样式；
-  D 继承的CSS 样式不如后来指定的CSS 样式；
-  E 在同一组属性设置中标有“!important”规则的优先级最大；

![CSS优先级](C:\Users\wuqian\Desktop\附录文件和源代码\杂物\壁纸\QQ图片20241027131238.png)

## 4.CSS 背景

CSS 背景属性用于定义HTML元素的背景。

CSS 属性定义背景效果:

- background-color
- background-image
- background-repeat
- background-attachment
- background-position

### 背景颜色

**1.语法**

`background-color` 属性定义了元素的背景颜色.

页面的背景颜色使用在body的选择器中:

```css
body {background-color:#b0c4de;}
```

CSS中，颜色值通常以以下方式定义:

- 十六进制 - 如："#ff0000"
- RGB - 如："rgb(255,0,0)"
- 颜色名称 - 如："red"

特别的，`transparent`是背景颜色的初始值（透明）。

**实例：**

```css
/* 关键字值 */
background-color: red;
background-color: indigo;

/* 十六进制值 */
background-color: #bbff00; /* 完全不透明 */
background-color: #bf0; /* 完全不透明简写 */
background-color: #11ffee00; /* 完全透明 */
background-color: #1fe0; /* 完全透明简写 */
background-color: #11ffeeff; /* 完全不透明 */
background-color: #1fef; /* 完全不透明简写 */

/* RGB 值 */
background-color: rgb(255 255 128); /* 完全不透明 */
background-color: rgb(117 190 218 / 50%); /* 50% 透明 */

/* HSL 值 */
background-color: hsl(50 33% 25%); /* 完全不透明 */
background-color: hsl(50 33% 25% / 75%); /* 75% 不透明，25% 透明 */

/* 特殊关键字值 */
background-color: currentcolor;
background-color: transparent;

/* 全局值 */
background-color: inherit;
background-color: initial;
background-color: revert;
background-color: revert-layer;
background-color: unset;
```

**2.背景颜色-半透明(CSS3)**

CSS3为我们 提供了背景颜色半透明的效果。

```css
background:rgba(0,0,0,0.3);
```

- 最后一个参数是alpha透明度，取值范围在0~1之间
- 我们习惯把0.3的0省略掉，写为`background:rgba(0,0,0,.3);`

**注意**：背景半透明是指盒子背景半透明，盒子里面的内容不受影响。

### 背景图像

`background-image` 属性描述了元素的背景图像。实际开发常见于logo或者一些装饰性的小图片或者是超大的背景图片，优点是便于控制位置。

默认情况下，背景图像进行平铺重复显示，以覆盖整个元素实体.

页面背景图片设置实例:

```css
body {background-image:url('paper.gif');}
```

**1.背景图像 - 水平或垂直平铺**

默认情况下 **`background-image`** 属性会在页面的水平或者垂直方向平铺。

一些图像如果在水平方向与垂直方向平铺，这样看起来很不协调

如果图像只在水平方向平铺 (`repeat-x`), 页面背景会更好些:

```css
body
{
	background-image:url('gradient2.png');
	background-repeat:repeat-x;
}
```

**2.背景图像- 设置定位与不平铺**

让背景图像不影响文本的排版。

如果你不想让图像平铺，你可以使用 `background-repeat` 属性:

```css
body
{
	background-image:url('img_tree.png');
	background-repeat:no-repeat;      /*不平铺*/
}
```

我们还可以利用 `background-position` 属性改变图像在背景中的位置:

> **1.若参数是方位名词**

- 如果指定的两个值都是方位名词，则两个值前后顺序无关，比如 **`left top`**和**`top left`**效果一致。
- 如果只指定了一个方位名词，另一个词省略，则第二个值默认居中对齐。

> **2.若参数是精确单位**

- 如果参数值是精确坐标，那么第一个肯定是x坐标，第二个一定是y坐标。
- 如果只指定一个数值，那该数值一定是x坐标，另一个默认垂直居中。

> **3.若参数是混合单位**

- 如果指定的两个值是精确单位和方位名词混合使用，则第一个值是x坐标，第二个值是y坐标。

```css
body
{
	background-image:url('img_tree.png');
	background-repeat:no-repeat;
	background-position:right top;    /*若参数是方位名词*/
    background-position:10px 20px;    /*若参数是精确单位*/
    background-position:10px center;  /*若参数是混合单位*/
}
```

**3.背景图像固定(背景附着)**

`background-attachment`属性设置背景图像是否固定或者随着页面的其余部分滚动。

`background-attachment`后期可以制作视差滚动的效果。

```css
background-attchment:scroll | fixed
```

`scroll`：背景图像是随对象内容滚动

`fixed`：背景图像固定

### 简写属性

在以上实例中我们可以看到页面的背景颜色通过了很多的属性来控制。

为了简化这些属性的代码，我们可以将这些属性合并在同一个属性中.

背景颜色的简写属性为 "background":

```css
body {background:#ffffff url('img_tree.png') no-repeat right top;}
```

当使用简写属性时，属性值的顺序为:

- background-color
- background-image
- background-repeat
- background-attachment
- background-position

以上属性无需全部使用，你可以按照页面的实际需要使用.

### --CSS 背景属性

| Property              | 描述                                         |
| :-------------------- | :------------------------------------------- |
| background            | 简写属性，作用是将背景属性设置在一个声明中。 |
| background-attachment | 背景图像是否固定或者随着页面的其余部分滚动。 |
| background-color      | 设置元素的背景颜色。                         |
| background-image      | 把图像设置为背景。                           |
| background-position   | 设置背景图像的起始位置。                     |
| background-repeat     | 设置背景图像是否及如何重复。                 |

## 5.CSS 文本

### 文本颜色

颜色属性被用来设置文字的颜色。

颜色是通过CSS最经常的指定：

- 十六进制值 - 如: **＃FF0000**
- 一个RGB值 - 如: **RGB(255,0,0)**
- 颜色的名称 - 如: **red**

参阅 [CSS 颜色值](https://www.runoob.com/cssref/css-colors-legal.html) 查看完整的颜色值。

一个网页的背景颜色是指在主体内的选择：

```css
body {color:red;}
h1 {color:#00ff00;}
h2 {color:rgb(255,0,0);}
```

对于W3C标准的CSS：如果你定义了颜色属性，你还必须定义背景色属性。

### 文本的对齐方式

文本排列属性是用来设置文本的水平对齐方式。

文本可居中或对齐到左或右,两端对齐.

当text-align设置为"justify"，每一行被展开为宽度相等，左，右外边距是对齐（如杂志和报纸）。

```css
h1 {text-align:center;}
p.date {text-align:right;}
p.main {text-align:justify;}
```

### 文本修饰

text-decoration 属性用来设置或删除文本的装饰。

从设计的角度看 text-decoration属性主要是用来删除链接的下划线：

```css
a {text-decoration:none;}
```

也可以这样装饰文字：

```css
h1 {text-decoration:overline;}
h2 {text-decoration:line-through;}
h3 {text-decoration:underline;}
```

我们不建议强调指出不是链接的文本，因为这常常混淆用户。

### 文本转换

文本转换属性是用来指定在一个文本中的大写和小写字母。

可用于所有字句变成大写或小写字母，或每个单词的首字母大写。

```css
p.uppercase {text-transform:uppercase;}
p.lowercase {text-transform:lowercase;}
p.capitalize {text-transform:capitalize;}
```

### 文本缩进

文本缩进属性是用来指定文本的第一行的缩进。

```css
p {text-indent:50px;}
```

### 单行文本居中

```css
div{
	width:100px;
	height:40px;
	line-height:40px;
}
/* 只要 height=line-height就能实现文字居中 */
```

如果行高小于盒子高度，文字会偏上；

如果行高大于盒子高度，则文字偏下。

### --CSS 文本属性

| 属性                    | 描述                     |
| :---------------------- | :----------------------- |
| color                   | 设置文本颜色             |
| direction               | 设置文本方向             |
| letter-spacing          | 设置字符间距             |
| line-height(类似行间距) | 设置行高                 |
| text-align              | 对齐元素中的文本         |
| text-decoration         | 向文本添加修饰           |
| text-indent             | 缩进元素中文本的首行     |
| text-shadow             | 设置文本阴影             |
| text-transform          | 控制元素中的字母         |
| unicode-bidi            | 设置或返回文本是否被重写 |
| vertical-align          | 设置元素的垂直对齐       |
| white-space             | 设置元素中空白的处理方式 |
| word-spacing            | 设置字间距               |

## 6.CSS 字体

CSS字体属性定义字体，加粗，大小，文字样式。

### CSS字型

在CSS中，有两种类型的字体系列名称：

- **通用字体系列** - 拥有相似外观的字体系统组合（如 "Serif" 或 "Monospace"）
- **特定字体系列** - 一个特定的字体系列（如 "Times" 或 "Courier"）

| Generic family | 说明                                        |
| :------------- | :------------------------------------------ |
| Serif          | Serif字体中字符在行的末端拥有额外的装饰     |
| Sans-serif     | "Sans"是指无 - 这些字体在末端没有额外的装饰 |
| Monospace      | 所有的等宽字符具有相同的宽度                |

### 字体系列

font-family 属性设置文本的字体系列。

font-family 属性应该设置几个字体名称作为一种"后备"机制，如果浏览器不支持第一种字体，他将尝试下一种字体。

**注意**: 如果字体系列的名称超过一个字，它必须用引号，如Font Family："宋体"。

多个字体系列是用一个逗号分隔指明：

```css
p{font-family:"Times New Roman", Times, serif;}
```

### 字体样式

主要是用于指定斜体文字的字体样式属性。

这个属性有三个值：

- 正常 - 正常显示文本
- 斜体 - 以斜体字显示的文字
- 倾斜的文字 - 文字向一边倾斜（和斜体非常类似，但不太支持）

```css
p.normal {font-style:normal;}
p.italic {font-style:italic;}
p.oblique {font-style:oblique;}
```

### 字体大小

font-size 属性设置文本的大小。

能否管理文字的大小，在网页设计中是非常重要的。但是，你不能通过调整字体大小使段落看上去像标题，或者使标题看上去像段落。

请务必使用正确的HTML标签，就`<h1>` - `<h6>`表示标题和`<p>`表示段落：

字体大小的值可以是绝对或相对的大小。

绝对大小：

- 设置一个指定大小的文本
- 不允许用户在所有浏览器中改变文本大小
- 确定了输出的物理尺寸时绝对大小很有用

相对大小：

- 相对于周围的元素来设置大小
- 允许用户在浏览器中改变文字大小

**1.设置字体大小像素**

设置文字的大小与像素，让您完全控制文字大小：

```css
h1 {font-size:40px;}
h2 {font-size:30px;}
p {font-size:14px;}
```

**2.用em来设置字体大小**

为了避免Internet Explorer 中无法调整文本的问题，许多开发者使用 em 单位代替像素。

em的尺寸单位由W3C建议。

1em和当前字体大小相等。在浏览器中默认的文字大小是16px。

因此，1em的默认大小是16px。可以通过下面这个公式将像素转换为em：**px/16=em**

```css
h1 {font-size:2.5em;} /* 40px/16=2.5em */
h2 {font-size:1.875em;} /* 30px/16=1.875em */
p {font-size:0.875em;} /* 14px/16=0.875em */
```

在上面的例子，em的文字大小是与前面的例子中像素一样。不过，如果使用 em 单位，则可以在所有浏览器中调整文本大小。

不幸的是，仍然是IE浏览器的问题。调整文本的大小时，会比正常的尺寸更大或更小。

**3.使用百分比和EM组合**

在所有浏览器的解决方案中，设置 `<body>`元素的默认字体大小的是百分比：

```css
body {font-size:100%;}
h1 {font-size:2.5em;}
h2 {font-size:1.875em;}
p {font-size:0.875em;}
```

### 字体图标

[国外的字体图标网站](https://icomoon.io/)

字体图标使用场景:主要用于显示网页中通用、常用的一些小图标。

精灵图是有诸多优点的，但是缺点很明显。

1.图片文件还是比较大的。

2.图片本身放大和缩小会失真。

3.一旦图片制作完毕想要更换非常复杂

此时，有一种技术的出现很好的解决了以上问题，就是字体图标`iconfont`。

字体图标可以为前端工程师提供一种方便高效的图标使用方式，展示的是图标，本质属于字体。

#### **使用字体图标**

**1.在 CSS 样式中全局声明字体**

> 先把下载包里面的 **fonts** 文件夹放入页面根目录下

 简单理解把这些字体文件通过css引入到我们页面中。

一定注意字体文件路径的问题

```css
 @font-face {
   font-family: 'icomoon';
   src:  url('fonts/icomoon.eot?7kkyc2');
   src:  url('fonts/icomoon.eot?7kkyc2#iefix') format('embedded-opentype'),
     url('fonts/icomoon.ttf?7kkyc2') format('truetype'),
     url('fonts/icomoon.woff?7kkyc2') format('woff'),
     url('fonts/icomoon.svg?7kkyc2#icomoon') format('svg');
   font-weight: normal;
   font-style: normal;
 }
```

**2.给标签定义字体**

```css
span{
  font-family: 'icomoon';        /*必需的*/
  font-size: 40px;
  color:black;
 }
```

**3.复制某个字体图标的标签(官网查询)**

```css
<span></span>
```

> **字体图标的优点**

- 轻量级:一个图标字体要比一系列的图像要小。一旦字体加载了，图标就会马上渲染出来，减少了服务器请求
- 灵活性:本质其实是文字，可以很随意的改变颜色、产生阴影、透明效果、旋转等
- 兼容性:几乎支持所有的浏览器，请放心使用

注意:字体图标不能替代精灵技术，只是对工作中图标部分技术的提升和优化

总结:

1.如果遇到一些结构和样式比较简单的小图标，就用字体图标

2.如果遇到一些结构和样式复杂一点的小图片，就用精灵图,

> **字体文件格式**

不同浏览器所支持的字体格式是不一样的，字体图标之所以兼容，就是因为包含了主流浏览器支持的字体文件。

1).TureType( **.ttf** )格式.ttf字体是Windows和Mac的最常见的字体，支持这种字体的浏览器有IE9+、Firefox3.5+、Chrome4+、Safari3+、Opera10+、iOS Mobile、Safari4.2+；

2).Web Open Font Format( **.woff** )格式woff字体，支持这种字体的浏览器有IE9+、Firefox3.5+、Chrome6+、Safari3.6+、Opera11.1+；

3).Embedded Open Type( **.eot** )格式.eot字体是IE专用字体，支持这种字体的浏览器有IE4+；

4).SVG( .**svg** )格式.svg字体是基于SVG字体渲染的一种格式，支持这种字体的浏览器有Chrome4+、Safari3.1+、Opera10.0+、iOS Mobile Safari3.2+；

> **字体图标的追加**

如果工作中，原来的字体图标不够用了，我们需要添加新的字体图标到原来的字体文件中。

把压缩包里面的 **selection.json** 从新上传，然后选中自己想要新的图标，从新下载压缩包，并替换原来的文件即可。

### --CSS 字体属性

| Property     | 描述                                 |
| :----------- | :----------------------------------- |
| font         | 在一个声明中设置所有的字体属性       |
| font-family  | 指定文本的字体系列                   |
| font-size    | 指定文本的字体大小                   |
| font-style   | 指定文本的字体样式                   |
| font-variant | 以小型大写字体或者正常字体显示文本。 |
| font-weight  | 指定字体的粗细。                     |

## 7.CSS 链接

不同的链接可以有不同的样式。

### 链接样式

链接的样式，可以用任何CSS属性（如颜色，字体，背景等）。

特别的链接，可以有不同的样式，这取决于他们是什么状态。

这四个链接状态是：

- `a:link` - 正常，未访问过的链接
- `a:visited` - 用户已访问过的链接
- `a:hover` - 当用户鼠标放在链接上时
- `a:active` - 链接被点击的那一刻

```css
a:link {color:#000000;}      /* 未访问链接*/
a:visited {color:#00FF00;}  /* 已访问链接 */
a:hover {color:#FF00FF;}  /* 鼠标移动到链接上 */
a:active {color:#0000FF;}  /* 鼠标点击时 */
```

当设置为若干链路状态的样式，也有一些顺序规则：

- `a:hover` 必须跟在 `a:link` 和 `a:visited`后面
- `a:active` 必须跟在 `a:hover`后面

### 常见的链接样式

根据上述链接的颜色变化的例子，看它是在什么状态。

让我们通过一些其他常见的方式转到链接样式：

**1.文本修饰**

text-decoration 属性主要用于删除链接中的下划线：

```css
a:link {text-decoration:none;}
a:visited {text-decoration:none;}
a:hover {text-decoration:underline;}
a:active {text-decoration:underline;}
```

**2.背景颜色**

背景颜色属性指定链接背景色：

```css
a:link {background-color:#B2FF99;}
a:visited {background-color:#FFFF85;}
a:hover {background-color:#FF704D;}
a:active {background-color:#FF704D;}
```

## 8.CSS列表

CSS 列表属性作用如下：

- 设置不同的列表项标记为有序列表
- 设置不同的列表项标记为无序列表
- 设置列表项标记为图像

在 HTML中，有两种类型的列表：

- 无序列表 **`ul`** - 列表项标记用特殊图形（如小黑点、小方框等）
- 有序列表 **`ol`** - 列表项的标记有数字或字母

使用 CSS，可以列出进一步的样式，并可用图像作列表项标记。

### 列表项标记样式

**1.list-style-type属性指定列表项标记的类型是：**

```css
ul.a {list-style-type: circle;}
ul.b {list-style-type: square;}
 
ol.c {list-style-type: upper-roman;}
ol.d {list-style-type: lower-alpha;}
```

**2.列表项标记的图像**

要指定列表项标记的图像，使用列表样式图像属性：

```css
ul
{
    list-style-image: url('sqpurple.gif');
}
```

### 浏览器兼容性

同样在所有的浏览器，下面的例子会显示的图像标记：

```css
ul
{
    list-style-type: none;
    padding: 0px;
    margin: 0px;
}
ul li
{
    background-image: url(sqpurple.gif);
    background-repeat: no-repeat;
    background-position: 0px 5px; 
    padding-left: 14px; 
}
```

例子解释：

- ul:
  - 设置列表类型为没有列表项标记
  - 设置填充和边距 0px（浏览器兼容性）
- ul 中所有 li:
  - 设置图像的 URL，并设置它只显示一次（无重复）
  - 您需要的定位图像位置（左 0px 和上下 5px）
  - 用 padding-left 属性把文本置于列表中

### 简写属性

在单个属性中可以指定所有的列表属性。这就是所谓的简写属性。

为列表使用简写属性，列表样式属性设置如下：

```css
ul
{
    list-style: square url("sqpurple.gif");
}
```

可以按顺序设置如下属性：

- list-style-type
- list-style-position (有关说明，请参见下面的CSS属性表)
- list-style-image

如果上述值丢失一个，其余仍在指定的顺序，就没关系。

### 移除默认设置

list-style-type:none 属性可以用于移除小标记。默认情况下列表 `<ul>` 或 `<ol>` 还设置了内边距和外边距，可使用 `margin:0` 和 `padding:0` 来移除:

```css
ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
}
```

### --CSS 列表属性

| 属性                | 描述                                               |
| :------------------ | :------------------------------------------------- |
| list-style          | 简写属性。用于把所有用于列表的属性设置于一个声明中 |
| list-style-image    | 将图像设置为列表项标志。                           |
| list-style-position | 设置列表中列表项标志的位置。                       |
| list-style-type     | 设置列表项标志的类型。                             |

## 9.CSS 表格

### 表格边框

指定CSS表格边框，使用border属性。

下面的例子指定了一个表格的Th和TD元素的黑色边框：

```css
table, th, td
{
    border: 1px solid black;
}
```

请注意，在上面的例子中的表格有双边框。这是因为表和th/ td元素有独立的边界。

为了显示一个表的单个边框，使用 border-collapse属性。

### 折叠边框

border-collapse 属性设置表格的边框是否被折叠成一个单一的边框或隔开：

```css
table
{
    border-collapse:collapse;
}
table,th, td
{
    border: 1px solid black;
}
```

### 表格宽度和高度

width和height属性定义表格的宽度和高度。

下面的例子是设置100％的宽度，50像素的th元素的高度的表格：

```css
table 
{
    width:100%;
}
th
{
    height:50px;
}
```

### 表格文字对齐

表格中的文本对齐和垂直对齐属性。

text-align属性设置水平对齐方式，向左，右，或中心：

```css
td
{
    text-align:right;
}
```

垂直对齐属性设置垂直对齐，比如顶部，底部或中间：

```css
td
{
    height:50px;
    vertical-align:bottom;
}
```

### 表格填充

如需控制边框和表格内容之间的间距，应使用td和th元素的填充属性：

```css
td
{
    padding:15px;
}
```

### 表格颜色

下面的例子指定边框的颜色，和th元素的文本和背景颜色：

```css
table, td, th
{
    border:1px solid green;
}
th
{
    background-color:green;
    color:white;
}
```



## 10.CSS 盒子模型

所有HTML元素可以看作盒子，在CSS中，"box model"这一术语是用来设计和布局时使用。

CSS盒模型本质上是一个盒子，封装周围的HTML元素，它包括：边距，边框，填充，和实际内容。

盒模型允许我们在其它元素和周围元素边框之间的空间放置元素。

不同部分的说明：

- **Margin(外边距)** - 清除边框外的区域，外边距是透明的。
- **Border(边框)** - 围绕在内边距和内容外的边框。
- **Padding(内边距)** - 清除内容周围的区域，内边距是透明的。
- **Content(内容)** - 盒子的内容，显示文本和图像。

为了正确设置元素在所有浏览器中的宽度和高度，你需要知道的盒模型是如何工作的。

> 标准的盒模型

```css
.box {
  width: 350px;
  height: 150px;
  margin: 10px;
  padding: 25px;
  border: 5px solid black;
}
```

### 元素的宽度和高度

当您指定一个 CSS 元素的宽度和高度属性时，你只是设置内容区域的宽度和高度。要知道，完整大小的元素，你还必须添加内边距，边框和外边距。

下面的例子中的元素的总宽度为 450px：

```css
div {
    width: 300px;
    border: 25px solid green;
    padding: 25px;
    margin: 25px;
}
```

最终元素的总宽度计算公式是这样的：

总元素的宽度=宽度+左填充+右填充+左边框+右边框+左边距+右边距

元素的总高度最终计算公式是这样的：

总元素的高度=高度+顶部填充+底部填充+上边框+下边框+上边距+下边距

### 嵌套块元素垂直外边距的塌陷

对于两个嵌套关系(父子关系)的块元素，父元素有上外边距同时子元素也有上外边距，此时父元素会塌陷较大的外边距值。

解决方案：

- 可以为父元素定义上边框
- 可以为父元素定义上内边距
- 可以为父元素添加overflow:hidden

### 浏览器兼容性

一旦为页面设置了恰当的 DTD，大多数浏览器都会按照上面的图示来呈现内容。然而 IE 5 和 6 的呈现却是不正确的。根据 W3C 的规范，元素内容占据的空间是由 width 属性设置的，而内容周围的 padding 和 border 值是另外计算的。不幸的是，IE5.X 和 6 在怪异模式中使用自己的非标准模型。这些浏览器的 width 属性不是内容的宽度，而是内容、内边距和边框的宽度的总和。

虽然有方法解决这个问题。但是目前最好的解决方案是回避这个问题。也就是，不要给元素添加具有指定宽度的内边距，而是尝试将内边距或外边距添加到元素的父元素和子元素。

IE8 及更早IE版本不支持设置填充的宽度和边框的宽度属性。

解决IE8及更早版本不兼容问题可以在HTML页面声明 `<!DOCTYPE html>`即可。

## 11.CSS Border

CSS边框属性允许你指定一个元素边框的样式和颜色。

### 边框样式

边框样式属性指定要显示什么样的边界。

 **border-style**属性用来定义边框的样式

**border-style 值:**

- none: 默认无边框
- dotted: 定义一个点线边框
- dashed: 定义一个虚线边框
- solid: 定义实线边框
- double: 定义两个边框。 两个边框的宽度和 border-width 的值相同
- groove: 定义3D沟槽边框。效果取决于边框的颜色值
- ridge: 定义3D脊边框。效果取决于边框的颜色值
- inset:定义一个3D的嵌入边框。效果取决于边框的颜色值
- outset: 定义一个3D突出边框。 效果取决于边框的颜色值

### 边框宽度

您可以通过 `border-width` 属性为边框指定宽度。

为边框指定宽度有两种方法：可以指定长度值，比如 2px 或 0.1em(单位为 px, pt, cm, em 等)，或者使用 3 个关键字之一，它们分别是 thick 、medium（默认值） 和 thin。

**注意：**CSS 没有定义 3 个关键字的具体宽度，所以一个用户可能把 thick 、medium 和 thin 分别设置为等于 5px、3px 和 2px，而另一个用户则分别设置为 3px、2px 和 1px。

```css
p.one
{
    border-style:solid;
    border-width:5px;
}
p.two
{
    border-style:solid;
    border-width:medium;
}
```

### 边框颜色

border-color属性用于设置边框的颜色。可以设置的颜色：

- name - 指定颜色的名称，如 "red"
- RGB - 指定 RGB 值, 如 "rgb(255,0,0)"
- Hex - 指定16进制值, 如 "#ff0000"

您还可以设置边框的颜色为"transparent"。

**注意：** border-color单独使用是不起作用的，必须得先使用border-style来设置边框样式。

```css
p.one
{
    border-style:solid;
    border-color:red;
}
p.two
{
    border-style:solid;
    border-color:#98bf21;
}
```

### 边框-单独设置各边

在CSS中，可以指定不同的侧面不同的边框：

```css
p
{
    border-top-style:dotted;
    border-right-style:solid;
    border-bottom-style:dotted;
    border-left-style:solid;
}
```

border-style属性可以有1-4个值：

- border-style:dotted solid double dashed;
  - 上边框是 dotted
  - 右边框是 solid
  - 底边框是 double
  - 左边框是 dashed
- border-style:dotted solid double;
  - 上边框是 dotted
  - 左、右边框是 solid
  - 底边框是 double
- border-style:dotted solid;
  - 上、底边框是 dotted
  - 右、左边框是 solid
- border-style:dotted;
  - 四面边框是 dotted

上面的例子用了border-style。然而，它也可以和border-width 、 border-color一起使用。

### 简写属性

上面的例子用了很多属性来设置边框。

你也可以在一个属性中设置边框。

你可以在"border"属性中设置：

- border-width
- border-style (required)
- border-color

```css
border:5px solid red;
```

### --CSS 边框属性

| 属性                | 描述                                                         |
| :------------------ | :----------------------------------------------------------- |
| border              | 简写属性，用于把针对四个边的属性设置在一个声明。             |
| border-style        | 用于设置元素所有边框的样式，或者单独地为各边设置边框样式。   |
| border-width        | 简写属性，用于为元素的所有边框设置宽度，或者单独地为各边边框设置宽度。 |
| border-color        | 简写属性，设置元素的所有边框中可见部分的颜色，或为 4 个边分别设置颜色。 |
| border-bottom       | 简写属性，用于把下边框的所有属性设置到一个声明中。           |
| border-bottom-color | 设置元素的下边框的颜色。                                     |
| border-bottom-style | 设置元素的下边框的样式。                                     |
| border-bottom-width | 设置元素的下边框的宽度。                                     |
| border-left         | 简写属性，用于把左边框的所有属性设置到一个声明中。           |
| border-left-cololr  | 设置元素的左边框的颜色。                                     |
| border-left-style   | 设置元素的左边框的样式。                                     |
| border-left-width   | 设置元素的左边框的宽度。                                     |
| border-right        | 简写属性，用于把右边框的所有属性设置到一个声明中。           |
| border-right-color  | 设置元素的右边框的颜色。                                     |
| border-right-style  | 设置元素的右边框的样式。                                     |
| border-right-width  | 设置元素的右边框的宽度。                                     |
| border-top          | 简写属性，用于把上边框的所有属性设置到一个声明中。           |
| border-top-color    | 设置元素的上边框的颜色。                                     |
| border-top-style    | 设置元素的上边框的样式。                                     |
| border-top-width    | 设置元素的上边框的宽度。                                     |
| border-radius       | 设置圆角的边框。                                             |

## 12.CSS 用户界面样式

### 鼠标样式 cursor

```css
li {cursor:pointer;}
```

设置或检索在对象上移动的鼠标指针采用何种系统预定义的光标形状。

| 属性值      | 描述      |
| ----------- | --------- |
| default     | 小白-默认 |
| pointer     | 小手      |
| move        | 移动      |
| text        | 文本      |
| not-allowed | 禁止      |

### CSS outline

轮廓（outline）是绘制于元素周围的一条线，位于边框边缘的外围，可起到突出元素的作用。

轮廓（outline）属性指定元素轮廓的样式、颜色和宽度。

```css
intput{
    outline:none;
}   /*取消表单轮廓线/*
```

```css
textarea{
    resize:none;
}	/*取消文本域拖拽*/
```

### --CSS 轮廓属性

"CSS" 列中的数字表示哪个CSS版本定义了该属性(CSS1 或者CSS2)。

| 属性          | 说明                           | 值                                                           | CSS  |
| :------------ | :----------------------------- | :----------------------------------------------------------- | :--- |
| outline       | 在一个声明中设置所有的轮廓属性 | outline-color outline-style outline-width inherit            | 2    |
| outline-color | 设置轮廓的颜色                 | color-name hex-number rgb-number invert inherit              | 2    |
| outline-style | 设置轮廓的样式                 | none dotted dashed solid double groove ridge inset outset inherit | 2    |
| outline-width | 设置轮廓的宽度                 | thin medium thick length inherit                             | 2    |

## 13.CSS margin

CSS margin(外边距)属性定义元素周围的空间。

margin 清除周围的（外边框）元素区域。margin 没有背景颜色，是完全透明的。

margin 可以单独改变元素的上，下，左，右边距，也可以一次改变所有的属性。

| 值     | 说明                                        |
| :----- | :------------------------------------------ |
| auto   | 设置浏览器边距。 这样做的结果会依赖于浏览器 |
| length | 定义一个固定的margin（使用像素，pt，em等）  |
| %      | 定义一个使用百分比的边距                    |

> Margin可以使用负值，重叠的内容。

### 单边外边距属性

在CSS中，它可以指定不同的侧面不同的边距：

```css
margin-top:100px;
margin-bottom:100px;
margin-right:50px;
margin-left:50px;
```

### 清除内外边距

```css
*{
	margin:0px;           /*清除外边距*/
	padding;0px;          /*清除内边距*/
}
```

**注意**：行内元素为了照顾兼容性，尽量只设置左右内外边距，不要设置上下内外边距 。但是转换为块级和行内元素就可以了。

### 简写属性

为了缩短代码，有可能使用一个属性中margin指定的所有边距属性。这就是所谓的简写属性。

所有边距属性的简写属性是 **margin** :

```css
margin:100px 50px;
```

margin属性可以有一到四个值。

- margin:25px 50px 75px 100px;
  - 上边距为25px
  - 右边距为50px
  - 下边距为75px
  - 左边距为100px
- margin:25px 50px 75px;
  - 上边距为25px
  - 左右边距为50px
  - 下边距为75px
- margin:25px 50px;
  - 上下边距为25px
  - 左右边距为50px
- margin:25px;
  - 所有的4个边距都是25px

### --CSS 边距属性

| 属性          | 描述                                       |
| :------------ | :----------------------------------------- |
| margin        | 简写属性。在一个声明中设置所有外边距属性。 |
| margin-bottom | 设置元素的下外边距。                       |
| margin-left   | 设置元素的左外边距。                       |
| margin-right  | 设置元素的右外边距。                       |
| margin-top    | 设置元素的上外边距。                       |

## 14.CSS padding

CSS padding（填充）是一个简写属性，定义元素边框与元素内容之间的空间，即上下左右的内边距。

当元素的 padding（填充）内边距被清除时，所释放的区域将会受到元素背景颜色的填充。

单独使用 padding 属性可以改变上下左右的填充。

| 值     | 说明                                |
| :----- | :---------------------------------- |
| length | 定义一个固定的填充(像素, pt, em,等) |
| %      | 使用百分比值定义一个填充            |

### 单边内边距属性

在CSS中，它可以指定不同的侧面不同的填充

```css
padding-top:25px;
padding-bottom:25px;
padding-right:50px;
padding-left:50px;
```

- 上内边距是 25px
- 右内边距是 50px
- 下内边距是 25px
- 左内边距是 50px

### 简写属性

为了缩短代码，它可以在一个属性中指定的所有填充属性。

这就是所谓的简写属性。所有的填充属性的简写属性是 **padding** :

```css
padding:25px 50px;
```

Padding属性，可以有一到四个值。

-  padding:25px 50px 75px 100px;

   - 上填充为25px

   - 右填充为50px

   - 下填充为75px

   - 左填充为100px

-  padding:25px 50px 75px;

   - 上填充为25px

   - 左右填充为50px

   - 下填充为75px

-  padding:25px 50px;

   - 上下填充为25px

   - 左右填充为50px

-  padding:25px;
   - 所有的填充都是25px

### --CSS 填充属性

| 属性           | 说明                                       |
| :------------- | :----------------------------------------- |
| padding        | 使用简写属性设置在一个声明中的所有填充属性 |
| padding-bottom | 设置元素的底部填充                         |
| padding-left   | 设置元素的左部填充                         |
| padding-right  | 设置元素的右部填充                         |
| padding-top    | 设置元素的顶部填充                         |

## 15.CSS 基本选择器

[CSS选择器](https://blog.csdn.net/weixin_68917948/article/details/129870632?ops_request_misc=%257B%2522request%255Fid%2522%253A%252217F8A6AD-7C50-4A72-B299-C416C9274087%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=17F8A6AD-7C50-4A72-B299-C416C9274087&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-129870632-null-null.142^v100^control&utm_term=HTML%E9%80%89%E6%8B%A9%E5%99%A8&spm=1018.2226.3001.4187)

css选择器可以分为**基本选择器**、**包含选择器**、**属性选择器**、**伪类选择器**和**伪元素选择器**几类。

其中基本选择器又可以细分为：标签选择器、ID选择器、类选择器和通用选择器。(**ps:优先级为：ID > class > 标签 > 通配符**)

包含选择器可以分为：子代选择器、后代选择器和分组选择器。

### ID选择器

 ID选择器是通过获取`id`的属性来进行设置，使用 #+ID属性值来选中。

```css
<style>
	#black{
       color: black;
     }
</style>
...
<div id="black" > ok. </div>
```

### 类选择器

类选择器是通过获取`class`属性来进行设置，使用 .+class属性值来选中。

```css
<style>
      .green{
         color:green;
      }
</style>
...  
<div class="green"> ok. </div>
```

### 通用选择器 

通用选择器使用 **`*`** 来代指，它代表的是选中了父元素中的所有内容。

```css
<style>
    *{
      color: blue;
    }
</style>
...
<div>yes yes yes </div>
<div>no no no</div>
```

###  标签选择器

  标签选择器是通过获取标签的名称来进行设置。

```css
<style>
      div{
          color: red;
      }
</style>
...
<div>yes yes yes </div>
```

### 嵌套选择器

它可能适用于选择器内部的选择器的样式。

在下面的例子设置了四个样式：

- **`p{ }`**: 为所有 **p** 元素指定一个样式。
- **`.marked{ }`**: 为所有 **class="marked"** 的元素指定一个样式。
- **`.marked p{ }`**: 为所有 **class="marked"** 元素内的 **p** 元素指定一个样式。
- **`p.marked{ }`**: 为所有 **class="marked"** 的 **p** 元素指定一个样式。

```css
p
{
    color:blue;
    text-align:center;
}
.marked
{
    background-color:red;
}
.marked p
{
    color:white;
}
p.marked{
    text-decoration:underline;
}
```

## 16.CSS 组合选择符(包含选择器)

> 组合选择符说明了两个选择器之间的关系。

CSS组合选择符包括各种简单选择符的组合方式。

在 CSS3 中包含了四种组合方式:

- 后代选择器(以空格 ` ` 分隔)
- 子元素选择器(以大于 **`>`** 号分隔）
- 相邻兄弟选择器（以加号 **`+`** 分隔）
- 普通兄弟选择器（以波浪号 **`～`** 分隔）

### 后代选择器

后代选择器用于选取某元素的后代元素。

以下实例选取所有 `<p>` 元素插入到 `<div>` 元素中: 

```css
div p
{
  background-color:yellow;
}
```

### 子元素选择器

与后代选择器相比，子元素选择器（Child selectors）只能选择作为某元素直接/一级子元素的元素。

以下实例选择了`<div>`元素中所有直接子元素 `<p>` ：

```css
div>p
{
  background-color:yellow;
}
```

### 相邻兄弟选择器

相邻兄弟选择器（Adjacent sibling selector）可选择紧接在另一元素后的元素，且二者有相同父元素。

如果需要选择紧接在另一个元素后的元素，而且二者有相同的父元素，可以使用相邻兄弟选择器（Adjacent sibling selector）。

以下实例选取了所有位于 `<div>` 元素后的第一个 `<p>` 元素:

```css
div+p
{
  background-color:yellow;
}
```

### 后续兄弟选择器

后续兄弟选择器选取所有指定元素之后的相邻兄弟元素。

以下实例选取了所有 `<div>` 元素之后的所有相邻兄弟元素 `<p>` :

```css
div~p
{
  background-color:yellow;
}
```

### 分组选择器

```css
h1,h2,p
{
    color:green;
}
```

为了尽量减少代码，你可以使用分组选择器。

每个选择器用逗号分隔。

## 17.CSS 属性选择器

CSS 属性选择器用于根据元素的属性或属性值来选择 HTML 元素。

属性选择器可以帮助你在不需要为元素添加类或 ID 的情况下对其进行样式化。

**注意：**IE7 和 IE8 需声明 **!DOCTYPE** 才支持属性选择器！IE6 和更低的版本不支持属性选择器。

以下是常见的 CSS 属性选择器：

**1、[attribute]**

选择带有指定属性的所有元素（无论属性值是什么）。

```css
/* 选择所有具有 `type` 属性的元素 */
[type] {
  border: 1px solid red;
}
```

**2、[attribute="value"]**

选择具有指定属性和值完全匹配的元素。

```css
/* 选择所有 `type` 属性等于 `text` 的元素 */
[type="text"] {
  background-color: yellow;
}
```

**3、[attribute~="value"]**

选择属性值中包含指定词（用空格分隔的词列表之一）的元素。

```css
/* 选择属性值中包含 `button` 的元素 */
[class~="button"] {
  font-weight: bold;
}
```

**4、[attribute|="value"]**

选择具有指定值或者以指定值开头并紧跟着连字符 - 的属性值的元素，常用于语言代码。

```css
/* 选择所有 `lang` 属性是 `en` 或者以 `en-` 开头的元素 */
[lang|="en"] {
  color: green;
}
```

**5、[attribute^="value"]**

选择属性值以指定值开头的元素。

```css
/* 选择所有 `href` 属性以 `https` 开头的链接 */
[href^="https"] {
  text-decoration: none;
}
```

**6、[attribute$="value"]**

选择属性值以指定值结尾的元素。

```css
/* 选择所有 src 属性以 .jpg 结尾的图片 */
[src$=".jpg"] {
  border: 2px solid blue;
}
```

**7、[attribute*="value"]**

选择属性值中包含指定值的元素。

```css
/* 选择所有 `title` 属性中包含 `tutorial` 的元素 */
[title*="tutorial"] {
  font-style: italic;
}
```

通过属性选择器，你可以轻松选择元素并基于它们的属性设置特定样式，增加了灵活性和可维护性。

## 18.CSS 伪类选择器

CSS伪类是用来添加一些选择器的特殊效果。

### **1.语法**

伪类的语法：

```css
selector:pseudo-class {property:value;}
```

CSS类也可以使用伪类：

```css
selector.class:pseudo-class {property:value;}
```

### **2.链接伪类选择器**

在支持 CSS 的浏览器中，链接的不同状态都可以以不同的方式显示

```css
a:link {color:#FF0000;} /* 未访问的链接 */
a:visited {color:#00FF00;} /* 已访问的链接 */
a:hover {color:#FF00FF;} /* 鼠标划过链接 */
a:active {color:#0000FF;} /* 已选中的链接 */
```

**注意**：

1. 伪类的名称不区分大小写。
2. 为了确保生效，请按照LVHA的顺序进行书写。
3. 实际开发中的写法

```css
a{
	color:grey;
}
a:hover{
	color:red;
}
```



### 3.:focus伪类选择器

:focus伪类选择器用于选取获得焦点的表单元素

焦点就是光标，一般情况`<input>`类表单元素才能获取，因此这个选择器也主要针对于表单元素来说。

```css
input:focus{
	background-color:yellow;
}
```



### **4.CSS :first-child 伪类**

您可以使用 :first-child 伪类来选择父元素的第一个子元素。

**注意**：在IE8的之前版本必须声明`<!DOCTYPE>` ，这样 :first-child 才能生效。

> **4.1 匹配第一个` <p>` 元素**

在下面的例子中，选择器匹配作为任何元素的第一个子元素的 `<p>` 元素：

```css
p:first-child
{
    color:blue;
}
```

> **4.2 匹配所有`<p>` 元素中的第一个 `<i>` 元素**

在下面的例子中，选择相匹配的所有`<p>`元素的第一个 `<i>` 元素：

```css
p > i:first-child
{
    color:blue;
}
```

> **4.3 匹配所有作为第一个子元素的 `<p>` 元素中的所有 `<i>` 元素**

在下面的例子中，选择器匹配所有作为元素的第一个子元素的 `<p>` 元素中的所有 `<i>` 元素：

```css
p:first-child i
{
    color:blue;
}
```

### **5.CSS :lang 伪类**

:lang 伪类使你有能力为不同的语言定义特殊的规则

**注意：**IE8必须声明`<!DOCTYPE>`才能支持;lang伪类。

在下面的例子中，:lang 类为属性值为 no 的q元素定义引号的类型：

```css
q:lang(no) {quotes: "~" "~";}
```

### --CSS 伪类/元素

| 选择器               | 示例                  | 示例说明                                          |
| :------------------- | :-------------------- | :------------------------------------------------ |
| :checked             | input:checked         | 选择所有选中的表单元素                            |
| :disabled            | input:disabled        | 选择所有禁用的表单元素                            |
| :empty               | p:empty               | 选择所有没有子元素的p元素                         |
| :enabled             | input:enabled         | 选择所有启用的表单元素                            |
| :first-of-type       | p:first-of-type       | 选择的每个 p 元素是其父元素的第一个 p 元素        |
| :in-range            | input:in-range        | 选择元素指定范围内的值                            |
| :invalid             | input:invalid         | 选择所有无效的元素                                |
| :last-child          | p:last-child          | 选择所有p元素的最后一个子元素                     |
| :last-of-type        | p:last-of-type        | 选择每个p元素是其母元素的最后一个p元素            |
| :not(selector)       | :not(p)               | 选择所有p以外的元素                               |
| :nth-child(n)        | p:nth-child(2)        | 选择所有 p 元素的父元素的第二个子元素             |
| :nth-last-child(n)   | p:nth-last-child(2)   | 选择所有p元素倒数的第二个子元素                   |
| :nth-last-of-type(n) | p:nth-last-of-type(2) | 选择所有p元素倒数的第二个为p的子元素              |
| :nth-of-type(n)      | p:nth-of-type(2)      | 选择所有p元素第二个为p的子元素                    |
| :only-of-type        | p:only-of-type        | 选择所有仅有一个子元素为p的元素                   |
| :only-child          | p:only-child          | 选择所有仅有一个子元素的p元素                     |
| :optional            | input:optional        | 选择没有"required"的元素属性                      |
| :out-of-range        | input:out-of-range    | 选择指定范围以外的值的元素属性                    |
| :read-only           | input:read-only       | 选择只读属性的元素属性                            |
| :read-write          | input:read-write      | 选择没有只读属性的元素属性                        |
| :required            | input:required        | 选择有"required"属性指定的元素属性                |
| :root                | root                  | 选择文档的根元素                                  |
| :target              | #news:target          | 选择当前活动#news元素(点击URL包含锚的名字)        |
| :valid               | input:valid           | 选择所有有效值的属性                              |
| :link                | a:link                | 选择所有未访问链接                                |
| :visited             | a:visited             | 选择所有访问过的链接                              |
| :active              | a:active              | 选择正在活动链接                                  |
| :hover               | a:hover               | 把鼠标放在链接上的状态                            |
| :focus               | input:focus           | 选择元素输入后具有焦点                            |
| :first-letter        | p:first-letter        | 选择每个`<p>` 元素的第一个字母                    |
| :first-line          | p:first-line          | 选择每个`<p> `元素的第一行                        |
| :first-child         | p:first-child         | 选择器匹配属于任意元素的第一个子元素的 `<p> `元素 |
| :before              | p:before              | 在每个`<p>`元素之前插入内容                       |
| :after               | p:after               | 在每个`<p>`元素之后插入内容                       |
| :lang(*language*)    | p:lang(it)            | 为`<p>`元素的lang属性选择一个开始值               |



## 19.CSS 伪元素选择器

CSS 伪元素是一种特殊的选择器，它可以在不改变 HTML 结构的情况下对页面元素的特定部分进行样式设置。

CSS 伪元素是用来添加一些选择器的特殊效果。

常用的 CSS 伪元素有 `::before`、`::after`、`::first-line`、`::first-letter` 等。

**1.语法**

伪元素的语法：

```css
selector::pseudo-element {
    property: value;
}
```

CSS 类也可以使用伪元素：

```css
selector.class::pseudo-element {
    property: value;
}
```

**2.:first-line 伪元素**

"first-line" 伪元素用于向文本的首行设置特殊样式。

在下面的例子中，浏览器会根据 "first-line" 伪元素中的样式对 p 元素的第一行文本进行格式化：

```css
p:first-line 
{
    color:#ff0000;
    font-variant:small-caps;
}
```

**注意**："first-line" 伪元素只能用于块级元素。

**注意**： 下面的属性可应用于 "first-line" 伪元素：

- font properties
- color properties 
- background properties
- word-spacing
- letter-spacing
- text-decoration
- vertical-align
- text-transform
- line-height
- clear

**3.:first-letter 伪元素**

"first-letter" 伪元素用于向文本的首字母设置特殊样式：

```css
p:first-letter 
{
    color:#ff0000;
    font-size:xx-large;
}
```

**注意**： "first-letter" 伪元素只能用于块级元素。

**注意**： 下面的属性可应用于 "first-letter" 伪元素： 

- font properties
- color properties 
- background properties
- margin properties
- padding properties
- border properties
- text-decoration
- vertical-align (only if "float" is "none")
- text-transform
- line-height
- float
- clear

**4.伪元素和CSS类**

伪元素可以结合CSS类： 

```css
p.article:first-letter {color:#ff0000;}

<p class="article">文章段落</p>
```

上面的例子会使所有 class 为 article 的段落的首字母变为红色。

**5.多个伪元素**

可以结合多个伪元素来使用。

在下面的例子中，段落的第一个字母将显示为红色，其字体大小为 xx-large。第一行中的其余文本将为蓝色，并以小型大写字母显示。

段落中的其余文本将以默认字体大小和颜色来显示：

```css
p:first-letter
{
    color:#ff0000;
    font-size:xx-large;
}
p:first-line 
{
    color:#0000ff;
    font-variant:small-caps;
}
```

**6.CSS - :before 伪元素**

":before" 伪元素可以在元素的内容前面插入新内容。

下面的例子在每个 `<h1>`元素前面插入一幅图片：

```css
h1:before 
{
    content:url(smiley.gif);
}
```

**7.CSS - :after 伪元素**

":after" 伪元素可以在元素的内容之后插入新内容。

下面的例子在每个 `<h1>` 元素后面插入一幅图片：

```css
h1:after
{
    content:url(smiley.gif);
}
```

### --CSS伪类/元素

| 选择器            | 示例           | 示例说明                                          |
| :---------------- | :------------- | :------------------------------------------------ |
| :link             | a:link         | 选择所有未访问链接                                |
| :visited          | a:visited      | 选择所有访问过的链接                              |
| :active           | a:active       | 选择正在活动链接                                  |
| :hover            | a:hover        | 把鼠标放在链接上的状态                            |
| :focus            | input:focus    | 选择元素输入后具有焦点                            |
| :first-letter     | p:first-letter | 选择每个`<p>` 元素的第一个字母                    |
| :first-line       | p:first-line   | 选择每个`<p>` 元素的第一行                        |
| :first-child      | p:first-child  | 选择器匹配属于任意元素的第一个子元素的 `<p>` 元素 |
| :before           | p:before       | 在每个`<p>`元素之前插入内容                       |
| :after            | p:after        | 在每个`<p>`元素之后插入内容                       |
| :lang(*language*) | p:lang(it)     | 为`<p>`元素的lang属性选择一个开始值               |

## 20.CSS  Dimension

CSS 尺寸 (Dimension) 属性允许你控制元素的高度和宽度。同样，它允许你增加行间距。

### --CSS 尺寸属性

| 属性        | 描述                 |
| :---------- | :------------------- |
| height      | 设置元素的高度。     |
| line-height | 设置行高。           |
| max-height  | 设置元素的最大高度。 |
| max-width   | 设置元素的最大宽度。 |
| min-height  | 设置元素的最小高度。 |
| min-width   | 设置元素的最小宽度。 |
| width       | 设置元素的宽度。     |



## 21.CSS Display、Visibility、OverFlow

display属性设置一个元素应如何显示，visibility属性指定一个元素应可见还是隐藏。

### 隐藏元素 visibility:hidden

隐藏一个元素可以通过把display属性设置为"none"，或把visibility属性设置为"hidden"。但是请注意，这两种方法会产生不同的结果。

visibility:hidden可以隐藏某个元素，但隐藏的元素仍需占用与未隐藏之前一样的空间。也就是说，该元素虽然被隐藏了，但仍然会影响布局。

```css
h1.hidden {visibility:hidden;}
```

***visibility隐藏后，继续占有原来的空间。***

### 隐藏元素 display:none

display:none可以隐藏某个元素，且隐藏的元素不会占用任何空间。也就是说，该元素不但被隐藏了，而且该元素原本占用的空间也会从页面布局中消失。

```css
h1.hidden {display:none;}

display:none;     /*隐藏对象*/
display:block;    /*除了转换为块级元素之外，同时还有显示元素的意思*/
```

***display隐藏元素后，不再占有原来的位置。***

后面应用及其广泛，搭配 JS 可以做很多的网页特效

> 实例：(土豆网的隐藏图片功能)

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8"></meta>
    <title>土豆网</title>
    <style>
      *{
        margin: 0;
        padding: 0;
      }
      .tudou{
        position: relative;
        width: 444px;
        height: 320px;
        background-color: pink;
        margin: 30px auto;
      }
      .tudou img{
        width: 100%;
        height: 100%;
      }
      .mask{
        display: none;     /*隐藏*/
        position: absolute;
        width: 100%;
        height: 100%;
        left: 0;
        top: 0;
        background: rgba(0, 0, 0, 0.4) url(../image/cs.png) no-repeat center;
      }
      .tudou:hover .mask{  /*鼠标经过这个界面时将.mask的内容变为显示*/
        display: block;     /*显示*/
      }
    </style>
  </head>
  <body>
    <div class="tudou">
      <div class="mask"></div>
      <img src="../image/mosi.PNG">
    </div>
  </body>
</html>
```

### 隐藏元素 overflow

overflow 属性指定了如果内容溢出一个元素的框(超过其指定高度及宽度)时，会发生什么。

| 属性值  | 描述                                       |
| ------- | ------------------------------------------ |
| visible | 不剪切内容也不添加滚动条                   |
| hidden  | 不显示超过对象尺寸的内容，超出的部分隐藏掉 |
| scroll  | 不管超出内容否，总是显示滚动条             |
| auto    | 超出自动显示滚动条，不超出不显示滚动条     |

一般情况下，我们都不想让溢出的内容显示出来，因为溢出的部分会影响布局,但是如果有定位的盒子，请慎用`overflow:hidden` 因为它会隐藏多余的部分。

### 块和内联元素

块元素是一个元素，占用了全部宽度，在前后都是换行符。

块元素的例子：

- `<h1>`
- `<p>`
- `<div>`

内联元素只需要必要的宽度，不强制换行。

内联元素的例子：

- `<span>`
- `<a>`

### 元素显示模式的改变

可以更改内联元素和块元素，反之亦然，可以使页面看起来是以一种特定的方式组合，并仍然遵循web标准。

下面的示例把列表项显示为内联元素：

```css
li {display:inline;}
```

下面的示例把span元素作为块元素：

```css
span {display:block;}
```

**注意：**变更元素的显示类型看该元素是如何显示，它是什么样的元素。例如：一个内联元素设置为display:block是不允许有它内部的嵌套块元素。

## 22.CSS Position

> 1.浮动可以让多个块级盒子一行没有缝隙排列显示，经常用于向排列盒子。
>
> 2.定位则是可以让盒子自由的在某个盒子内移动位置或者固定屏幕中某个位置，并且可以压住其他盒子。

定位:将盒子定在某一个位置，所以定位也是在摆放盒子，按照定位的方式移动盒子。

定位=定位模式+边偏移。

定位模式用于指定一个元素在文档中的定位方式。边偏移则决定了该元素的最终位置。

`position` 属性指定了元素的定位类型。

`position` 属性的五个值：

- static
- relative
- fixed
- absolute
- sticky

元素可以使用的顶部，底部，左侧和右侧属性定位。然而，这些属性无法工作，除非事先设定position属性。他们也有不同的工作方式，这取决于定位方法。

### 1.static 定位--静态定位

HTML 元素的默认值，即没有定位，遵循正常的文档流对象。

- 静态定位按照标准流特性摆放位置，它没有边偏移
- 静态定位在布局时很少用到
- 静态定位的元素不会受到 `top`, `bottom`, `left`, `right`影响。


```css
div.static {
    position: static;
    border: 3px solid #73AD21;
}
```

### 2.fixed 定位--固定定位

元素的位置相对于浏览器窗口是固定位置。

即使窗口是滚动的它也不会移动：

```css
p.pos_fixed
{
    position:fixed;
    top:30px;
    right:5px;
}
```

**注意**： Fixed 定位在 IE7 和 IE8 下需要描述 !DOCTYPE 才能支持。

Fixed定位使元素的位置与文档流无关，因此不占据空间。

Fixed定位的元素和其他元素重叠。

**绝对定位(固定定位)会完全压住盒子**

- 浮动元素不同，只会压住它下面标准流的盒子，但是不会压住下面标准流盒子里面的文字(图片)
- 但是绝对定位(固定定位)会压住下面标准流所有的内容。
- 浮动之所以不会压住文字，因为浮动产生的目的最初是为了做文字环绕效果的。文字会围绕浮动元素

### 3.relative 定位--相对定位

相对定位是元素在移动位置的时候，是相对于它原来的位置来说的。

```css
h2.pos_left
{
    position:relative;
    left:-20px;
}
h2.pos_right
{
    position:relative;
    left:20px;
}
```

> **相对定位的特点:**

1.它是相对于自己原来的位置来移动的(移动位置的时候参照点是自己原来的位置)

2.原来在标准流的位置继续占有，后面的盒子仍然以标准流的方式对待它。(不脱标，继续保留原来位置)

#### 定位特殊特性

绝对定位和固定定位也和浮动类似。

1.行内元素添加绝对或者固定定位，可以直接设置高度和宽度

2.块级元素添加绝对或者固定定位，如果不给宽度或者高度，默认大小是内容的大小

3.脱标的盒子不会触发外边距塌陷，浮动元素、绝对定位(固定定位)元素的都不会触发外边距合并的问题

### 4.absolute 定位--绝对定位

绝对定位是元素在移动位置的时候，是相对于它祖先元素来说的。如果元素没有已定位的父元素，那么它的位置相对于`<html>`(即浏览器):

```css
h2
{
    position:absolute;
    left:100px;
    top:150px;
}
```

`absolute` 定位使元素的位置与文档流无关，因此不占据空间。

`absolute` 定位的元素和其他元素重叠。

> **绝对定位的特点:**

1.如果没有祖先元素或者祖先元素没有定位，则以**浏览器**为准定位(Document文档)。

2.如果祖先元素有定位(相对、绝对、固定定位)，则以最近一级的有定位祖先元素为参考点移动位置。

3.绝对定位不再占有原先的位置。(脱标)

**子绝父相**

这句话的意思是:子级是绝对定位的话，父级要用相对定位。

①子级绝对定位，不会占有位置，可以放到父盒子里面的任何一个地方，不会影响其他的兄弟盒子。

②父盒子需要加定位限制子盒子在父盒子内显示。

③父盒子布局时，需要占有位置，因此父亲只能是相对定位:

这就是子绝父相的由来，所以相对定位经常用来作为绝对定位的父级。

总结:因为父级需要占有位置，因此是相对定位，子盒子不需要占有位置，则是绝对定位。

#### 盒子居中算法

绝对定位的盒子居中
加了绝对定位的盒子不能通过 margin:0auto 水平居中，但是可以通过以下计算方法实现水平和垂直居中。

```css
left: 50%; /*让盒子的左侧移动到父级元素的水平中心位置*/
```

```css
margin-left: -100px; /*让盒子向左移动自身宽度的一半*/
```

### 5.sticky 定位-粘性定位

`sticky` 英文字面意思是粘，粘贴，所以可以把它称之为粘性定位。

**`position: sticky;`** 基于用户的滚动位置来定位。

粘性定位的元素是依赖于用户的滚动，在 **`position:relative`** 与 **`position:fixed`** 定位之间切换。

它的行为就像 **`position:relative;`** 而当页面滚动超出目标区域时，它的表现就像 **`position:fixed;`**，它会固定在目标位置。

元素定位表现为在跨越特定阈值前为相对定位，之后为固定定位。

这个特定阈值指的是 top, right, bottom 或 left 之一，换言之，指定 top, right, bottom 或 left 四个阈值其中之一，才可使粘性定位生效。否则其行为与相对定位相同。

**注意**： Internet Explorer, Edge 15 及更早 IE 版本不支持 sticky 定位。 Safari 需要使用 -webkit- prefix (查看以下实例)。

```css
div.sticky {
    position: -webkit-sticky; /* Safari */
    position: sticky;
    top: 0;
    background-color: green;
    border: 2px solid #4CAF50;
}
```

> **粘性定位的特点：**

1.以浏览器的可视窗口为参照点移动元素(固定定位特点)

2.粘性定位占有原先的位置(相对定位特点)

3.必须添加 top、left、right、bottom其中一个才有效

### 6.`z-index`-重叠的元素

元素的定位与文档流无关，所以它们可以覆盖页面上的其它元素

`z-index`属性指定了一个元素的堆叠顺序（哪个元素应该放在前面，或后面）

一个元素可以有正数或负数的堆叠顺序：

```css
img
{
    position:absolute;
    left:0px;
    top:0px;
    z-index:-1;
}
```

**具有更高堆叠顺序的元素总是在较低的堆叠顺序元素的前面。(数字越大优先级越高)**

- 数值可以是正整数、负整数或0,默认是 auto，数值越大，盒子越靠上
- 如果属性值相同，则按照书写顺序，后来居上
- 数字后面不能加单位
- 只有定位的盒子才有z-index属性

**注意**： 如果两个定位元素重叠，没有指定`z-index`，最后定位在HTML代码中的元素将被显示在最前面。

### --CSS 定位属性

"CSS" 列中的数字表示哪个CSS(CSS1 或者CSS2)版本定义了该属性。

| 属性       | 说明                                                         | 值                                                           | CSS  |
| :--------- | :----------------------------------------------------------- | :----------------------------------------------------------- | :--- |
| bottom     | 定义了定位元素下外边距边界与其包含块下边界之间的偏移。       | `auto` `length` `%` `inherit`                                | 2    |
| clip       | 剪辑一个绝对定位的元素                                       | `shape` `auto` `inherit`                                     | 2    |
| cursor     | 显示光标移动到指定的类型                                     | `url` `auto` `crosshair` `default` `pointer` `move` `e-resize` `ne-resize ` `nw-resize` `n-resize` `se-resize` `sw-resize` `s-resize` `w-resize` `text` `wait` `help` | 2    |
| left       | 定义了定位元素左外边距边界与其包含块左边界之间的偏移。       | `auto` `length` `%` `inherit`                                | 2    |
| overflow   | 设置当元素的内容溢出其区域时发生的事情。                     | `auto` `hidden` `scroll` `visible` `inherit`                 | 2    |
| overflow-y | 指定如何处理顶部/底部边缘的内容溢出元素的内容区域            | `auto` `hidden` `scroll` `visible` `no-display` `no-content` | 2    |
| overflow-x | 指定如何处理右边/左边边缘的内容溢出元素的内容区域            | `auto` `hidden` `scroll` `visible` `no-display` `no-content` | 2    |
| position   | 指定元素的定位类型                                           | `absolute` `fixed` `relative` `static` `inherit`             | 2    |
| right      | 定义了定位元素右外边距边界与其包含块右边界之间的偏移。       | `auto` `length` `%` `inherit`                                | 2    |
| top        | 定义了一个定位元素的上外边距边界与其包含块上边界之间的偏移。 | `auto` `length` `%` `inherit`                                | 2    |
| z-index    | 设置元素的堆叠顺序                                           | `number` `auto` `inherit`                                    | 2    |

## 23.CSS Float

> CSS 的 Float（浮动），用于创建浮动框，将其移动到一边，直到左边缘或右边缘触及包含块或另一个浮动框的边缘。

- Float（浮动），往往是用于图像，但它在布局时一样非常有用。元素的水平方向浮动，意味着元素只能左右移动而不能上下移动。一个浮动元素会尽量向左或向右移动，直到它的外边缘碰到包含框或另一个浮动框的边框为止。浮动元素之后的元素将围绕它。浮动元素之前的元素将不会受到影响。

- 有很多的布局效果，标准流没有办法完成，此时就可以利用浮动完成布局。因为浮动可以改变元素标签默认的排列方式。
- 浮动最典型的应用:可以让多个块级元素一行内排列显示
- 浮动盒子不用担心外边距塌陷问题

**网页布局第一准则:多个块级元素纵向排列找标准流，多个块级元素横向排列找浮动**

**1.语法:**

```css
选择器{
	float:属性值;
}
```

**2.属性值**

| 属性值 | 描述                   |
| ------ | ---------------------- |
| none   | 元素不浮动(**默认值**) |
| left   | 元素向**左**浮动       |
| right  | 元素向**右**浮动       |

**3.浮动特性**

1. 脱离标准普通流的控制(浮)移动到指定位置(动)，(俗称脱标)，浮动的盒子不再保留原先的位置。
2. 如果多个盒子都设置了浮动，则它们会按照属性值**一行内显示并且顶端对齐排列**。
3. 浮动元素会具有行内块元素特性。
4. 浮动元素经常和标准流父级搭配使用。
   - 为了约束浮动元素位置, 我们网页布局一般采取的策略是:
   - 先用标准流的父元素排列上下位置,之后内部子元素采取浮动排列左右位置,符合网页布局第一准则。

**4.注意点**

1. 浮动和标准流的父盒子搭配。
   - 先用标准流的父元素排列上下位置,之后内部子元素采取浮动排列左右位置
2. 一个元素浮动了，理论上其余的兄弟元素也要浮动。
   - 一个盒子里面有多个子盒子，如果其中一个盒子浮动了，那么其他兄弟也应该浮动，以防止引起问题.
   - 浮动的盒子只会影响浮动盒子后面的标准流,不会影响前面的标准流.

### 清除浮动

**1.`clear`**

- 清除浮动的本质是清除浮动元素造成的影响
- 如果父盒子本身有高度，则不需要清除浮动
- 清除浮动之后，父级就会根据浮动的子盒子自动检测高度，父级有了高度，就不会影响下面的标准流了

元素浮动之后，周围的元素会重新排列，为了避免这种情况，使用 `clear` 属性。

`clear` 属性指定元素两侧不能出现浮动元素。

**1.1 语法**

```css
选择器
{
    clear:属性值;
}
```

**1.2 属性值**

| 属性值 | 描述                                         |
| ------ | -------------------------------------------- |
| both   | 同时清除左右两侧浮动的影响                   |
| left   | 不允许**左**侧有浮动元素(清除左侧浮动的影响) |
| right  | 不允许**右**侧有浮动元素(清除右侧浮动的影响) |

**2.清除浮动-额外标签法**

额外标签法也称为隔墙法，是**W3C**推荐的做法,

额外标签法会在浮动元素末尾添加一个空的标签。例如`<div style="clear:both"></div>`，或者其他标签
(如`<br/>`等)。

优点:通俗易懂，书写方便

缺点:添加许多无意义的标签，结构化较差

注意：要求这个新的空标签必须是块级元素。

**3.清除浮动-CSS  Overflow**

> 可以给**父元素**overflow属性

CSS overflow 属性用于控制内容溢出元素框时显示的方式。

CSS overflow 属性可以控制内容溢出元素框时在对应的元素区间内添加滚动条。

overflow属性有以下值：

| 值      | 描述                                                     |
| :------ | :------------------------------------------------------- |
| visible | 默认值。内容不会被修剪，会呈现在元素框之外。             |
| hidden  | 内容会被修剪，并且其余内容是不可见的。                   |
| scroll  | 内容会被修剪，但是浏览器会显示滚动条以便查看其余的内容。 |
| auto    | 如果内容被修剪，则浏览器会显示滚动条以便查看其余的内容。 |
| inherit | 规定应该从父元素继承 overflow 属性的值。                 |

**注意**：overflow 属性只工作于指定高度的块元素上。

**注意**： 在 OS X Lion ( Mac 系统) 系统上，滚动条默认是隐藏的，使用的时候才会显示 (设置 "overflow:scroll" 也是一样的)。

默认情况下，overflow 的值为 visible， 意思是内容溢出元素框。

```css
div {
    width: 200px;
    height: 50px;
    background-color: #eee;
    overflow: visible;
}
```

**4.清除浮动 - :after 伪元素法**

:after 方式是额外标签法的升级版。也是给父元素添加

```css
.clearfix:after{
	content:" ";
	display:block;
	height:0;
	clear: both;
	visibility: hidden;
}
	.clearfix{
        /*IE6、7 专有*/
	*zoom:1;
}
```

**5.双伪元素清除浮动**

也是给父元素添加

```css
.clearfix:before,.clearfix:after{
	content:"";
	display:table;
}
.clearfix:after{
	clear:both;
}
.clearfix{
	*zoom:1;
}
```



### --CSS 浮动属性

"CSS" 列中的数字表示不同的 CSS 版本（CSS1 或 CSS2）定义了该属性。

| 属性  | 描述                               | 值                                     | CSS  |
| :---- | :--------------------------------- | :------------------------------------- | :--- |
| clear | 指定不允许元素周围有浮动元素。     | `left` `right` `both` `none` `inherit` | 1    |
| float | 指定一个盒子（元素）是否可以浮动。 | `left` `right` `none` `inherit`        | 1    |

## 24.CSS对齐

### 元素居中对齐

要水平居中对齐一个元素(如 `<div>`), 可以使用 **`margin: auto;`**。

设置到元素的宽度将防止它溢出到容器的边缘。

元素通过指定宽度，并将两边的空外边距平均分配：

```css
.center {
    margin: auto;
    width: 50%;
    border: 3px solid green;
    padding: 10px;
}
```

**注意**： 如果没有设置 **width** 属性(或者设置 100%)，居中对齐将不起作用。

### 文本居中对齐

如果仅仅是为了文本在元素内居中对齐，可以使用 **`text-align: center;`**

```css
.center {
    text-align: center;
    border: 3px solid green;
}
```

### 图片居中对齐

要让图片居中对齐, 可以使用 **`margin: auto;`** 并将它放到 **`块`** 元素中:

```css
img {
    display: block;
    margin: auto;
    width: 40%;
}
```

### 左右对齐 

**1.使用定位方式**

我们可以使用 **`position: absolute;`** 属性来对齐元素:

```css
.right {
    position: absolute;
    right: 0px;
    width: 300px;
    border: 3px solid #73AD21;
    padding: 10px;
}
```

注释：绝对定位元素会被从正常流中删除，并且能够交叠元素。

**提示**： 当使用 **`position`** 来对齐元素时, 通常 **`<body>`** 元素会设置 **`margin`** 和 **`padding`** 。 这样可以避免在不同的浏览器中出现可见的差异。

当使用 position 属性时，IE8 以及更早的版本存在一个问题。如果容器元素（在我们的案例中是 `<div class="container">`）设置了指定的宽度，并且省略了 !DOCTYPE 声明，那么 IE8 以及更早的版本会在右侧增加 17px 的外边距。这似乎是为滚动条预留的空间。当使用 position 属性时，请始终设置 !DOCTYPE 声明：

```css
body {
    margin: 0;
    padding: 0;
}
 
.container {
    position: relative;
    width: 100%;
}
 
.right {
    position: absolute;
    right: 0px;
    width: 300px;
    background-color: #b0e0e6;
}
```

**2.使用 float 方式**

我们也可以使用 **`float`** 属性来对齐元素:

```css
.right {
    float: right;
    width: 300px;
    border: 3px solid #73AD21;
    padding: 10px;
}
```

当像这样对齐元素时，对 `<body>` 元素的外边距和内边距进行预定义是一个好主意。这样可以避免在不同的浏览器中出现可见的差异。

> 注意：如果子元素的高度大于父元素，且子元素设置了浮动，那么子元素将溢出，这时候你可以使用 "**clearfix**(清除浮动)" 来解决该问题。

我们可以在父元素上添加 overflow: auto; 来解决子元素溢出的问题:

```css
.clearfix {
    overflow: auto;
}
```

当使用 float 属性时，IE8 以及更早的版本存在一个问题。如果省略 !DOCTYPE 声明，那么 IE8 以及更早的版本会在右侧增加 17px 的外边距。这似乎是为滚动条预留的空间。当使用 float 属性时，请始终设置 !DOCTYPE 声明：

```css
body {
    margin: 0;
    padding: 0;
}
 
.right {
    float: right;
    width: 300px;
    background-color: #b0e0e6;
}
```

### 垂直居中对齐 

**1.使用 `padding`**

CSS 中有很多方式可以实现垂直居中对齐。 一个简单的方式就是头部顶部使用 **`padding`**:

```css
.center {
    padding: 70px 0;
    border: 3px solid green;
}
```

如果要水平和垂直都居中，可以使用 **`padding`** 和 **`text-align: center`**:

```css
.center {
    padding: 70px 0;
    border: 3px solid green;
    text-align: center;
}
```

**2.使用 `line-height`**

```css
.center {
    line-height: 200px;
    height: 200px;
    border: 3px solid green;
    text-align: center;
}
 
/* 如果文本有多行，添加以下代码: */
.center p {
    line-height: 1.5;
    display: inline-block;
    vertical-align: middle;
}
```

**3.使用 `position` 和 `transform`**

除了使用 **`padding`** 和 **`line-height`** 属性外,我们还可以使用 **`transform`** 属性来设置垂直居中:

```css
.center { 
    height: 200px;
    position: relative;
    border: 3px solid green; 
}
 
.center p {
    margin: 0;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}
```

### 图片、表单、文字对齐

CSS 的 `vertical-align`属性使用场景:经常用于设置图片或者表单(行内块元素)和文字垂直对齐。

官方解释:用于设置一个元素的垂直对齐方式，但是它只针对于行内元素或者行内块元素有效。

(图片、表单都属于行内块元素，默认的`vertical-align`是基线对齐。)

语法：

```css
vertical-align: baseline | top | middle | bottom
```

| 值       | 描述                                   |
| -------- | -------------------------------------- |
| baseline | 默认。元素放置在父元素的基线上。       |
| top      | 把元素的顶端与行中最高元素的顶端对齐   |
| middle   | 把此元素放置在父元素的中部             |
| bottom   | 把元素的顶端与行中最低的元素的顶端对齐 |

> bug:**图片底侧会有一个空白缝隙**，原因是行内块元素会和文字的基线对齐。
> 主要解决方法有两种:
> 1.给图片添加`vertical-align:middle|top|bottom`等。(提倡使用的)
>
> 2.把图片转换为块级元素 `display:block`

## 25.CSS 导航栏

熟练使用导航栏，对于任何网站都非常重要。

使用CSS你可以转换成好看的导航栏而不是枯燥的HTML菜单。

> 导航栏注意点:
> **实际开发中，我们不会直接用链接`a` 而是用`li` 包含链接`(li+a)`的做法。**
> 1.`li+a`语义更清晰，一看这就是有条理的列表型内容。
> 2.如果直接用a，搜索引警容易辨别为有堆砌关键字嫌疑(故意堆砌关键字容易被搜索引擎有降权的风险)从而影响网站排名

### 导航栏=链接列表

作为标准的 HTML 基础一个导航栏是必须的。

在我们的例子中我们将建立一个标准的 HTML 列表导航栏。

导航条基本上是一个链接列表，所以使用 `<ul>` 和 `<li>`元素非常有意义：

```css
<ul>
  <li><a href="#home">主页</a></li>
  <li><a href="#news">新闻</a></li>
  <li><a href="#contact">联系</a></li>
  <li><a href="#about">关于</a></li>
</ul>
```

现在，让我们从列表中删除边距和填充：

```css
ul {
    list-style-type: none;
    margin: 0;
    padding: 0;
}
```

例子解析：

- list-style-type:none - 移除列表前小标志。一个导航栏并不需要列表标记
- 移除浏览器的默认设置将边距和填充设置为0

上面的例子中的代码是垂直和水平导航栏使用的标准代码。

### 垂直导航栏

上面的代码，我们只需要 `<a>`元素的样式，建立一个垂直的导航栏：

```css
a
{
    display:block;
    width:60px;
}
```

示例说明：

- display:block - 显示块元素的链接，让整体变为可点击链接区域（不只是文本），它允许我们指定宽度
- width:60px - 块元素默认情况下是最大宽度。我们要指定一个60像素的宽度

**注意**: 请务必指定 `<a>`元素在垂直导航栏的的宽度。如果省略宽度，IE6可能产生意想不到的效果。

> 实例：

```css
<style>
ul {
    list-style-type: none;
    margin: 0;
    padding: 0;
    width: 200px;
    background-color: #f1f1f1;
    height: 100%; /* 全屏高度 */
    position: fixed; 
    overflow: auto; /* 如果导航栏选项多，允许滚动 */
}

li a {
    display: block;
    color: #000;
    padding: 8px 16px;
    text-decoration: none;
}

li a.active {
    background-color: #4CAF50;
    color: white;
}

li a:hover:not(.active) {
    background-color: #555;
    color: white;
}
</style>
```

### 水平导航栏

有两种方法创建横向导航栏。使用**内联(inline)**或**浮动(float)**的列表项。

这两种方法都很好，但如果你想链接到具有相同的大小，你必须使用浮动的方法。

**1.内联列表项**

建立一个横向导航栏的方法之一是指定元素， 下述代码是标准的内联:

```css
li
{
    display:inline;
}
```

实例解析：

- display:inline; - 默认情况下，**`<li>`** 元素是块元素。在这里，我们删除换行符之前和之后每个列表项，以显示一行。

**2.浮动列表项**

在上面的例子中链接有不同的宽度。

对于所有的链接宽度相等，浮动 `<li>`元素，并指定为 `<a>`元素的宽度：

```css
li
{
    float:left;
}
a
{
    display:block;
    width:60px;
}
```

实例解析：

- float:left - 使用浮动块元素的幻灯片彼此相邻
- display:block - 显示块元素的链接，让整体变为可点击链接区域（不只是文本），它允许我们指定宽度
- width:60px - 块元素默认情况下是最大宽度。我们要指定一个60像素的宽度

> 实例：

```css
ul {
    list-style-type: none;
    margin: 0;
    padding: 0;
    overflow: hidden;
    background-color: #333;
}
 
li {
    float: left;
}
 
li a {
    display: block;
    color: white;
    text-align: center;
    padding: 14px 16px;
    text-decoration: none;
}
 
/*鼠标移动到选项上修改背景颜色 */
li a:hover {
    background-color: #111;
}
```

## 26.CSS 下拉菜单

### 基本下拉菜单

当鼠标移动到指定元素上时，会出现下拉菜单。

```css
<!DOCTYPE html>
<html>
<head>
<title>QWQ</title>
<meta charset="utf-8">
<style>
.dropdown {
  position: relative;
  display: inline-block;
}
.dropdown-content {
  display: none;
  position: absolute;
  background-color: #f9f9f9;
  min-width: 160px;
  box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
  padding: 12px 16px;
}
.dropdown:hover .dropdown-content {
  display: block;
}
</style>
</head>
<body>

<h2>鼠标移动后出现下拉菜单</h2>
<p>将鼠标移动到指定元素上就能看到下拉菜单。</p>

<div class="dropdown">
  <span>鼠标移动到我这！</span>
  <div class="dropdown-content">
    <p>柒柒子zzz</p>
    <p>www.qiqizizzz.com</p>
  </div>
</div>

</body>
</html>
```

> ### 实例解析

**HTML 部分：**

我们可以使用任何的 HTML 元素来打开下拉菜单，如：`<span>`, 或 a `<button>` 元素。

使用容器元素 (如： `<div>`) 来创建下拉菜单的内容，并放在任何你想放的位置上。

使用 `<div>` 元素来包裹这些元素，并使用 CSS 来设置下拉内容的样式。

**CSS 部分：**

`.dropdown` 类使用 `position:relative`, 这将设置下拉菜单的内容放置在下拉按钮 (使用 `position:absolute`) 的右下角位置。

`.dropdown-content` 类中是实际的下拉菜单。默认是隐藏的，在鼠标移动到指定元素后会显示。 注意 `min-width` 的值设置为 160px。你可以随意修改它。 **注意:** 如果你想设置下拉内容与下拉按钮的宽度一致，可设置 `width` 为 100% ( `overflow:auto` 设置可以在小尺寸屏幕上滚动)。

我们使用 `box-shadow` 属性让下拉菜单看起来像一个"卡片"。

`:hover` 选择器用于在用户将鼠标移动到下拉按钮上时显示下拉菜单。

### 下拉菜单

创建下拉菜单，并允许用户选取列表中的某一项：

这个实例类似前面的实例，当我们在下拉列表中添加了链接，并设置了样式：

```css
<!DOCTYPE html>
<html>
<head>
<title>QWQ</title>
<meta charset="utf-8">
<style>
/* 下拉按钮样式 */
.dropbtn {
    background-color: #4CAF50;
    color: white;
    padding: 16px;
    font-size: 16px;
    border: none;
    cursor: pointer;
}

/* 容器 <div> - 需要定位下拉内容 */
.dropdown {
    position: relative;
    display: inline-block;
}

/* 下拉内容 (默认隐藏) */
.dropdown-content {
    display: none;
    position: absolute;
    background-color: #f9f9f9;
    min-width: 160px;
    box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
}

/* 下拉菜单的链接 */
.dropdown-content a {
    color: black;
    padding: 12px 16px;
    text-decoration: none;
    display: block;
}

/* 鼠标移上去后修改下拉菜单链接颜色 */
.dropdown-content a:hover {background-color: #f1f1f1}

/* 在鼠标移上去后显示下拉菜单 */
.dropdown:hover .dropdown-content {
    display: block;
}

/* 当下拉内容显示后修改下拉按钮的背景颜色 */
.dropdown:hover .dropbtn {
    background-color: #3e8e41;
}
</style>
</head>
<body>

<h2>下拉菜单</h2>
<p>鼠标移动到按钮上打开下拉菜单。</p>

<div class="dropdown">
  <button class="dropbtn">下拉菜单</button>
  <div class="dropdown-content">
    <a href="https://github.com/qiqizizzz/qiqizizzz-codenotes">qiqizizzz 1</a>
    <a href="https://github.com/qiqizizzz/qiqizizzz-codenotes">qiqizizzz 2</a>
    <a href="https://github.com/qiqizizzz/qiqizizzz-codenotes">qiqizizzz 3</a>
  </div>
</div>

</body>
</html>
```

## 26.CSS 提示工具

提示工具在鼠标移动到指定元素后触发。

### 基础提示框

提示框在鼠标移动到指定元素上显示：

```css
<style>/* Tooltip 容器 */
.tooltip {
    position: relative;
    display: inline-block;
    border-bottom: 1px dotted black; /* 悬停元素上显示点线 */
}
 
/* Tooltip 文本 */
.tooltip .tooltiptext {
    visibility: hidden;
    width: 120px;
    background-color: black;
    color: #fff;
    text-align: center;
    padding: 5px 0;
    border-radius: 6px;
 
    /* 定位 */
    position: absolute;
    z-index: 1;
}
 
/* 鼠标移动上去后显示提示框 */
.tooltip:hover .tooltiptext {
    visibility: visible;
}</style>
 
<div class="tooltip">鼠标移动到这
  <span class="tooltiptext">提示文本</span>
</div>
```

**实例解析**

**HTML)** 使用容器元素 (like `<div>`) 并添加 **"tooltip"** 类。在鼠标移动到 `<div>` 上时显示提示信息。

提示文本放在内联元素上(如 `<span>`) 并使用**class="tooltiptext"**。

**CSS) ** **tooltip** 类使用 **position:relative**, 提示文本需要设置定位值 **position:absolute**。 **注意:** 接下来的实例会显示更多的定位效果。

**tooltiptext** 类用于实际的提示文本。模式是隐藏的，在鼠标移动到元素显示 。设置了一些宽度、背景色、字体色等样式。

CSS3  **border-radius** 属性用于为提示框添加圆角。

**:hover** 选择器用于在鼠标移动到到指定元素 `<div> `上时显示的提示。

### 定位提示工具

以下实例中，提示工具显示在指定元素的右侧(**left:105%**) 。

注意 **top:-5px** 同于定位在容器元素的中间。使用数字 **5** 因为提示文本的顶部和底部的内边距（padding）是 5px。

如果你修改 padding 的值，top 值也要对应修改，这样才可以确保它是居中对齐的。

在提示框显示在左边的情况也是这个原理。

**1.显示在右侧**

```css
.tooltip .tooltiptext {
    top: -5px;
    left: 105%; 
}
```

**2.显示在左侧**

```css
.tooltip .tooltiptext {
    top: -5px;
    right: 105%; 
}
```

**3.显示在头部**

如果你想要提示工具显示在头部和底部。我们需要使用 **margin-left** 属性，并设置为 -60px。 这个数字计算来源是使用宽度的一半来居中对齐，即： width/2 (120/2 = 60)。

```css
.tooltip .tooltiptext {
    width: 120px;
    bottom: 100%;
    left: 50%; 
    margin-left: -60px; /* 使用一半宽度 (120/2 = 60) 来居中提示工具 */
}
```

**4.显示在底部**

```css
.tooltip .tooltiptext {
    width: 120px;
    top: 100%;
    left: 50%; 
    margin-left: -60px; /* 使用一半宽度 (120/2 = 60) 来居中提示工具 */
}
```

### 添加箭头

我们可以用CSS 伪元素 ::after 及 content 属性为提示工具创建一个小箭头标志，箭头是由边框组成的，但组合起来后提示工具像个语音信息框。

以下实例演示了如何为显示在顶部的提示工具添加底部箭头：

**1.顶部提示框/底部箭头：**

```css
.tooltip .tooltiptext::after {
    content: " ";
    position: absolute;
    top: 100%; /* 提示工具底部 */
    left: 50%;
    margin-left: -5px;
    border-width: 5px;
    border-style: solid;
    border-color: black transparent transparent transparent;
}
```

**实例解析**:

在提示工具内定位箭头: **top: 100%** , 箭头将显示在提示工具的底部。**left: 50%** 用于居中对齐箭头。

**注意：** **border-width** 属性指定了箭头的大小。如果你修改它，也要修改 **margin-left** 值。这样箭头才能居中显示。

**border-color** 用于将内容转换为箭头。设置顶部边框为黑色，其他是透明的。如果设置了其他的也是黑色则会显示为一个黑色的四边形。

**2.底部提示框/顶部箭头**：

```css
.tooltip .tooltiptext::after {
    content: " ";
    position: absolute;
    bottom: 100%;  /* 提示工具头部 */
    left: 50%;
    margin-left: -5px;
    border-width: 5px;
    border-style: solid;
    border-color: transparent transparent black transparent;
}
```

**3.右侧提示框/左侧箭头**：

```css
.tooltip .tooltiptext::after {
    content: " ";
    position: absolute;
    top: 50%;
    right: 100%; /* 提示工具左侧 */
    margin-top: -5px;
    border-width: 5px;
    border-style: solid;
    border-color: transparent black transparent transparent;
}
```

**4.左侧提示框/右侧箭头：**

```css
.tooltip .tooltiptext::after {
    content: " ";
    position: absolute;
    top: 50%;
    left: 100%; /* 提示工具右侧 */
    margin-top: -5px;
    border-width: 5px;
    border-style: solid;
    border-color: transparent transparent transparent black;
}
```

### 淡入效果

我们可以使用 CSS3 `transition` 属性及 `opacity` 属性来实现提示工具的淡入效果:

```css
.tooltip .tooltiptext {
    opacity: 0;
    transition: opacity 1s;
}
 
.tooltip:hover .tooltiptext {
    opacity: 1;
}
```

## 28.CSS 媒体类型

媒体类型允许你指定文件将如何在不同媒体呈现。该文件可以以不同的方式显示在屏幕上，在纸张上，或听觉浏览器等等。 

一些 CSS 属性只设计了某些媒体。例如 **`voice-family`** 属性是专为听觉用户代理。其他一些属性可用于不同的媒体类型。例如， **`font-size`** 属性可用于屏幕和印刷媒体，但有不同的值。屏幕和纸上的文件不同，通常需要一个更大的字体，**`sans-serif`** 字体比较适合在屏幕上阅读，而 **`serif`** 字体更容易在纸上阅读。

### @media 规则

@media 规则允许在相同样式表为不同媒体设置不同的样式。

在下面的例子告诉我们浏览器屏幕上显示一个 14 像素的 Verdana 字体样式。但是如果页面打印，将是 10 个像素的 Times 字体。请注意，`font-weight` 在屏幕上和纸上设置为粗体：

```css
@media screen
{
    p.test {font-family:verdana,sans-serif;font-size:14px;}
}
@media print
{
    p.test {font-family:times,serif;font-size:10px;}
}
@media screen,print
{
    p.test {font-weight:bold;}
}
```

### 其他媒体类型

**注意**：媒体类型名称不区分大小写。

| 媒体类型   | 描述                                                   |
| :--------- | :----------------------------------------------------- |
| all        | 用于所有的媒体设备。                                   |
| aural      | 用于语音和音频合成器。                                 |
| braille    | 用于盲人用点字法触觉回馈设备。                         |
| embossed   | 用于分页的盲人用点字法打印机。                         |
| handheld   | 用于小的手持的设备。                                   |
| print      | 用于打印机。                                           |
| projection | 用于方案展示，比如幻灯片。                             |
| screen     | 用于电脑显示器。                                       |
| tty        | 用于使用固定密度字母栅格的媒体，比如电传打字机和终端。 |
| tv         | 用于电视机类型的设备。                                 |



## 29.CSS 计数器

CSS 计数器通过一个变量来设置，根据规则递增变量。

------

### 使用计数器自动编号

CSS 计数器根据规则来递增变量。

CSS 计数器使用到以下几个属性：

- `counter-reset` - 创建或者重置计数器
- `counter-increment` - 递增变量
- `content` - 插入生成的内容
- `counter()` 或 `counters()` 函数 - 将计数器的值添加到元素

要使用 CSS 计数器，得先用 counter-reset 创建：

以下实例在页面创建一个计数器 (在 body 选择器中)，每个 `<h2>` 元素的计数值都会递增，并在每个 `<h2>` 元素前添加 `"Section <计数值>:"`

```css
body {
  counter-reset: section;
}
 
h2::before {
  counter-increment: section;
  content: "Section " counter(section) ": ";
}
```

### 嵌套计数器

以下实例在页面创建一个计数器，在每一个 `<h1>` 元素前添加计数值 `"Section <主标题计数值>."`, 嵌套的计数值则放在 `<h2>` 元素的前面，内容为 `"<主标题计数值>.<副标题计数值>":`

```css
body {
  counter-reset: section;
}
 
h1 {
  counter-reset: subsection;
}
 
h1::before {
  counter-increment: section;
  content: "Section " counter(section) ". ";
}
 
h2::before {
  counter-increment: subsection;
  content: counter(section) "." counter(subsection) " ";
}
```

计数器也可用于列表中，列表的子元素会自动创建。这里我们使用了 `counters()` 函数在不同的嵌套层级中插入字符串:

```css
ol {
  counter-reset: section;
  list-style-type: none;
}
 
li::before {
  counter-increment: section;
  content: counters(section,".") " ";
}
```

### --CSS 计数器属性

| 属性              | 描述                                                |
| :---------------- | :-------------------------------------------------- |
| content           | 使用 ::before 和 ::after 伪元素来插入自动生成的内容 |
| counter-increment | 递增一个或多个值                                    |
| counter-reset     | 创建或重置一个或多个计数器                          |

## 30.CSS 网页布局

通过盒子模型，清楚知道大部分html标签是一个盒子。

通过CSS浮动、定位可以让每个盒子排列成为网页。

一个完整的网页，是标准流、浮动、定位一起完成布局的，每个都有自己的专门用法。

1.标准流

可以让盒子上下排列或者左右排列，垂直的块级盒子显示就用标准流布局。

2.浮动

可以让多个块级元素一行显示或者左右对齐盒子，多个块级盒子水平显示就用浮动布局。

3.定位

定位最大的特点是有层叠的概念，就是可以让多个盒子前后叠压来显示。如果元素自由在某个盒子内移动就用定位布局。

```css
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>qiqizizzz(qiqizizzz.com)</title>
<style>
* {
  box-sizing: border-box;
}
 
body {
  font-family: Arial;
  padding: 10px;
  background: #f1f1f1;
}
 
/* 头部标题 */
.header {
  padding: 30px;
  text-align: center;
  background: white;
}
 
.header h1 {
  font-size: 50px;
}
 
/* 导航条 */
.topnav {
  overflow: hidden;
  background-color: #333;
}
 
/* 导航条链接 */
.topnav a {
  float: left;
  display: block;
  color: #f2f2f2;
  text-align: center;
  padding: 14px 16px;
  text-decoration: none;
}
 
/* 链接颜色修改 */
.topnav a:hover {
  background-color: #ddd;
  color: black;
}
 
/* 创建两列 */
/* Left column */
.leftcolumn {   
  float: left;
  width: 75%;
}
 
/* 右侧栏 */
.rightcolumn {
  float: left;
  width: 25%;
  background-color: #f1f1f1;
  padding-left: 20px;
}
 
/* 图像部分 */
.fakeimg {
  background-color: #aaa;
  width: 100%;
  padding: 20px;
}
 
/* 文章卡片效果 */
.card {
  background-color: white;
  padding: 20px;
  margin-top: 20px;
}
 
/* 列后面清除浮动 */
.row:after {
  content: "";
  display: table;
  clear: both;
}
 
/* 底部 */
.footer {
  padding: 20px;
  text-align: center;
  background: #ddd;
  margin-top: 20px;
}
 
/* 响应式布局 - 屏幕尺寸小于 800px 时，两列布局改为上下布局 */
@media screen and (max-width: 800px) {
  .leftcolumn, .rightcolumn {   
    width: 100%;
    padding: 0;
  }
}
 
/* 响应式布局 -屏幕尺寸小于 400px 时，导航等布局改为上下布局 */
@media screen and (max-width: 400px) {
  .topnav a {
    float: none;
    width: 100%;
  }
}
</style>
</head>
<body>

<div class="header">
  <h1>我的网页</h1>
  <p>重置浏览器大小查看效果。</p>
</div>

<div class="topnav">
  <a href="#">链接</a>
  <a href="#">链接</a>
  <a href="#">链接</a>
  <a href="#" style="float:right">链接</a>
</div>

<div class="row">
  <div class="leftcolumn">
    <div class="card">
      <h2>文章标题</h2>
      <h5>2019 年 4 月 17日</h5>
      <div class="fakeimg" style="height:200px;">图片</div>
      <p>一些文本...</p>
      <p> I'm qiqizizzz.</p>
    </div>
    <div class="card">
      <h2>文章标题</h2>
      <h5>2019 年 4 月 17日</h5>
      <div class="fakeimg" style="height:200px;">图片</div>
      <p>一些文本...</p>
      <p> I'm qiqizizzz.</p>
    </div>
  </div>
  <div class="rightcolumn">
    <div class="card">
      <h2>关于我</h2>
      <div class="fakeimg" style="height:100px;">图片</div>
      <p>关于我的一些信息..</p>
    </div>
    <div class="card">
      <h3>热门文章</h3>
      <div class="fakeimg"><p>图片</p></div>
      <div class="fakeimg"><p>图片</p></div>
      <div class="fakeimg"><p>图片</p></div>
    </div>
    <div class="card">
      <h3>关注我</h3>
      <p>一些文本...</p>
    </div>
  </div>
</div>

<div class="footer">
  <h2>底部区域</h2>
</div>

</body>
</html>
```

## 31.CSS !important 规则

CSS 中的 !important 规则用于增加样式的权重。

**!important** 与优先级无关，但它与最终的结果直接相关，使用一个 !important 规则时，此声明将覆盖任何其他声明。

```css
#myid {
  background-color: blue;
}
 
.myclass {
  background-color: gray;
}
 
p {
  background-color: red !important;
}
```

以上实例中，尽管 ID 选择器和类选择器具有更高的优先级，但三个段落背景颜色都显示为红色，因为 !important 规则会覆盖 background-color 属性。

**重要说明**

使用 !important 是一个坏习惯，应该尽量避免，因为这破坏了样式表中的固有的级联规则 使得调试找 bug 变得更加困难了。

当两条相互冲突的带有 !important 规则的声明被应用到相同的元素上时，拥有更大优先级的声明将会被采用。

以下实例我们在查看 CSS 源码时就不是很清楚哪种颜色最重要：

```css
#myid {
  background-color: blue !important;
}
 
.myclass {
  background-color: gray !important;
}
 
p {
  background-color: red !important;
}
```

**使用建议：**

- **一定**要优先考虑使用样式规则的优先级来解决问题而不是 `!important`
- **只有**在需要覆盖全站或外部 CSS 的特定页面中使用 `!important`
- **永远不要**在你的插件中使用 `!important`
- **永远不要**在全站范围的 CSS 代码中使用 `!important`

### 何时使用 !important

如果要在你的网站上设定一个全站样式的 CSS 样式可以使用 `!important`。

如果想要设置所有按钮具有相同的外观，我们可以将 `!important` 规则添加到按钮的样式属性中，如下所示：

```css
.button {
  background-color: #8c8c8c !important;
  color: white !important;
  padding: 5px !important;
  border: 1px solid black !important;
}
 
#myDiv a {
  color: red;
  background-color: yellow;
}
```





# 二、CSS3

## 0.CSS3 边框

用 CSS3，你可以创建圆角边框，添加阴影框，并作为边界的形象而不使用设计程序，如 Photoshop。

在本章中，您将了解以下的边框属性：

- border-radius
- box-shadow
- border-image

## 1.CSS3 圆角边框

### CSS3 `border-radius` 属性

使用 CSS3 `border-radius` 属性，你可以给任何元素制作 "圆角"。

语法：

```css
border-radius:length;
```

- 参数值可以为数值或百分比的形式
- 如果盒子是正方形，想要设置为一个圆，把数值修改为高度或者宽度的一半即可，或者直接写为50%
- 如果盒子是个矩形，设置为高度的一半就可以做

> 实例:

```css
#rcorners1 {
    border-radius: 25px;          //圆角边框属性
    background: #8AC007;
    padding: 20px;
    width: 200px;
    height: 150px;
}
```

### 简写属性

如果你在 border-radius 属性中只指定一个值，那么将生成 4 个 圆角。

但是，如果你要在四个角上一一指定，可以使用以下规则：

- **四个值:** 第一个值为左上角，第二个值为右上角，第三个值为右下角，第四个值为左下角。
- **三个值:** 第一个值为左上角, 第二个值为右上角和左下角，第三个值为右下角
- **两个值:** 第一个值为左上角与右下角，第二个值为右上角与左下角
- **一个值：** 四个圆角值相同

以下为三个实例:

1. 四个值 - border-radius: 15px 50px 30px 5px。
2. 三个值 - border-radius: 15px 50px 30px。
3. 两个值 - border-radius: 15px 50px。

### CSS3 圆角属性

| 属性                       | 描述                                    |
| :------------------------- | :-------------------------------------- |
| border-radius              | 所有四个边角 `border-radius` 属性的缩写 |
| border-top-left-radius     | 定义了左上角的弧度                      |
| border-top-right-radius    | 定义了右上角的弧度                      |
| border-bottom-right-radius | 定义了右下角的弧度                      |
| border-bottom-left-radius  | 定义了左下角的弧度                      |

## 2.CSS3 盒阴影

CSS3 中的 `box-shadow` 属性被用来添加阴影:

```css
div
	{
	box-shadow: 10px 10px 5px #888888;
	}
```

> **语法**

```css
box-shadow: h-shadow v-shadow blur spread color inset;
/*前两个属性值是必需的*/
```

**注意：**boxShadow 属性把一个或多个下拉阴影添加到框上。该属性是一个用逗号分隔阴影的列表，每个阴影由 2-4 个长度值、一个可选的颜色值和一个可选的 inset 关键字来规定。省略长度的值是 0。

| 值       | 说明                                                         |
| :------- | :----------------------------------------------------------- |
| h-shadow | 必需的。水平阴影的位置。允许负值                             |
| v-shadow | 必需的。垂直阴影的位置。允许负值                             |
| blur     | 可选。模糊距离                                               |
| spread   | 可选。阴影的大小                                             |
| color    | 可选。阴影的颜色。在[CSS颜色值](https://www.runoob.com/cssref/css_colors_legal.aspx)寻找颜色值的完整列表 |
| inset    | 可选。从外层的阴影（开始时）改变阴影内侧阴影                 |

## 3.CSS3 文字阴影

**语法**

```css
text-shadow: h-shadow v-shadow blur color;
```

**注意：** text-shadow属性连接一个或更多的阴影文本。属性是阴影，指定的每2或3个长度值和一个可选的颜色值用逗号分隔开来。已失时效的长度为0。

> 实例：(**文字阴影模糊效果**)

```css
a1{
    display: inline-block;
    margin-top: 10px;
    margin-left: 20px;
    text-decoration: none;
    color: rgb(102, 102, 102);
    text-shadow: 1px 2px 8px #ff0000;
}
<a href="#" class="a1">【特惠】爆款耳机5折秒！</a><br>
```

| 值       | 描述                                                         |
| :------- | :----------------------------------------------------------- |
| h-shadow | 必需。水平阴影的位置。允许负值。                             |
| v-shadow | 必需。垂直阴影的位置。允许负值。                             |
| blur     | 可选。模糊的距离。                                           |
| color    | 可选。阴影的颜色。参阅 [CSS 颜色值](https://www.runoob.com/cssref/css-colors-legal.html)。 |

## 4.CSS3 Sprites

使用精表图核心总结:

1.精灵图主要针对于小的背景图片使用。

2.主要借助于背景位置来实现--`background-position`

3.一般情况下精灵图都是负值。(千万注意网页中的坐标:x轴右边走是正值，左边走是负值，y轴同理。)

```html
<!-- 一个实例 -->
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8"></meta>
	<title>Text Code</title>
  <style>
    .box1{
      display: inline-block;
      width: 144px;
      height: 116px;
      background: url(../img/abcd.jpg) -110px -553px;
    }
    .box2{
      display: inline-block;
      width: 119px;
      height: 115px;
      background: url(../img/abcd.jpg) -472px -417px;
    }
    .box3{
      display: inline-block;
      width: 133px;
      height: 120px;
      background: url(../img/abcd.jpg) 0 -411px;
    }
    .box4{
      display: inline-block;
      width: 65px;
      height: 120px;
      background: url(../img/abcd.jpg) -323px -133px;
    }
    .box5{
      display: inline-block;
      width: 111px;
      height: 129px;
      background: url(../img/abcd.jpg) 0 0;
    }
    .box6{
      display: inline-block;
      width: 119px;
      height: 125px;
      background: url(../img/abcd.jpg) -252px -272px; 
    }
  </style>
</head>
<body>
  <div class="box1"></div>
  <div class="box2"></div>
  <div class="box3"></div>
  <div class="box4"></div>
  <div class="box5"></div>
  <div class="box6"></div>
</body>
```

# 三、CSS高级技巧

## 1.CSS 三角

网页中常见一些三角形，使用CSS直接画出来就可以，不必做成图片或者字体图标。

```css
.box1{
      height: 0;
      width: 0;
      /*line-height:0;
      font-size:0;    低版本的浏览器需要写这两句话   */
      border:100px solid transparent;   /* transparent设置为透明的颜色 */
      margin: 20px auto;
      border-right-color: pink;
    }
```

<img src="C:/Users/wuqian/Desktop/note/img/csssanjiao.png" alt="csssanjiao" style="zoom:33%;" />如图所示，这是一个顶端朝左的三角。

> 实例

```css
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8"></meta>
	<title>Text Code</title>
  <style>
    .box1{
      position: relative;
      width: 300px;
      height: 100px;
      background-color: rgb(61, 115, 198);
      margin: 20px auto;
    }
    .box1 span{
      position: absolute;
      top:40px;
      right:-20px;
      width: 0;
      height: 0;
      border: 10px solid transparent;
      border-left-color: rgb(61, 115, 198);
    }
  </style>
</head>
<body>
  <div class="box1">
    <span></span>
  </div>
</body>
```

![csssanjiaoanli](C:/Users/wuqian/Desktop/note/img/csssanjiaoanli.png)效果如图所示

## 2.溢出的文字省略号显示

**1.单行文本溢出显示省略号--必须满足三个条件**

```css
/*1.先强制一行内显示文本*/
white-space:nowrap;  /*(默认normal自动换行)*/
/*2.超出的部分隐藏*/
overflow: hidden;
/*3.文字用省略号替代超出的部分*/
text-overflow:ellipsis;
```

**2.多行文本溢出显示省略号**

多行文本溢出显示省略号，有较大兼容性问题，适合于webKit浏览器或移动端(移动端大部分是webkit内核)

```css
overflow: hidden;
text-overflow:ellipsis;
/*弹性伸缩盒子模型显示 */
display:-webkit-box;
/*限制在一个块元素显示的文本的行数*/
-webkit-line-clamp:2;
/*设置或检索伸缩盒对象的子元素的排列方式*/
-webkit-box-orient:vertical;
```

## 3.margin负值运用

1.让每个盒子margin 往左侧移动 -1px 正好压住相邻盒子边框

2.鼠标经过某个盒子的时候，提高当前盒子的层级即可(如果没有有定位，则加相对定位(保留位置)，如果有定位，则加z-index)

```css
	ul li{
      /*position:absolute*/
      float: left;
      list-style: none;
      width: 150px;
      height: 200px;
      border: 1px solid red;
      margin-left: -1px;
    }
    ul li:hover{
      /*position:relative*/
      z-index: 1;
      border: 1px solid blue;
    }
```

## 4.文字围绕浮动元素

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8"></meta>
	<title>Text Code</title>
  <style>
    *{
      margin: 0;
      padding: 0;
    }
    .box{
      width: 300px;
      height: 70px;
      background-color: pink;
      margin: 0 auto;
      padding: 5px;
    }
    .pic{
      float: left;     /*通过浮动来实现*/
      width: 120px;
      height: 60px;
      margin-right: 5px;
    }
    .pic img{
      width: 100%;
    }
  </style>
</head>
<body>
  <div class="box">
    <div class="pic">
      <img src="..." alt="">
    </div>
    <p>我是qiqizizzz，onefwfwpfnwpefwefeaffwfsefsefsfafvsefvgbydafsf</p>
  </div>
</body>
```

## 5.行内块巧妙运用

![css1](..\img\css1.png)**实例图**

代码实现:

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8"></meta>
	<title>Text Code</title>
  <style>
    .box{
      margin-top: 30px;
      text-align: center;
    }
    .box a{
      display: inline-block;
      width: 36px;
      height: 36px;
      background-color: #f7f7f7;
      border: 1px solid #ccc;
      text-align: center;     /*核心代码*/
      line-height: 36px;
      text-decoration: none;
      color: #333;
      font-size: 14px;
    }
    .box .prev,
    .box .next{
      width: 85px;
    }
  </style>
</head>
<body>
  <div class="box">
    <a href="#" class="prev">&lt;&lt;上一页</a>
    <a href="#">2</a>
    <a href="#">3</a>
    <a href="#">4</a>
    <a href="#">5</a>
    <a href="#">6</a>
    <a href="#">7</a>
    <a href="#" class="next">&gt;&gt;下一页</a>
  </div>
</body>
```

## 6.CSS 三角强化

**1.实现直角三角形**

```css
.box{
      height: 0;
      width: 0;
      /*1.只保留右边的边框有颜色*/
      border-color:transparent red transparent transparent;

      /*2.样式都是solid */
      border-style: solid;

      /*3.上边框宽度要大,右边框宽度稍小,其余的边框该为0*/
      border-width:100px 50px 0 0;
    }
```

