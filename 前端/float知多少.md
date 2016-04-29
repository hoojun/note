# Float知多少

## 产生问题

先从一个简单的例子说起：

```html
<div class="parent">
    <div class="child-left"></div>
    <div class="child-right"></div>
</div>
```

```css
.parent {
    width: 200px;
    margin:  30px auto;
    border: solid 5px #3498db;
}
[class^='child'] {
  opacity: 0.8;
}

.child-left {
    float: left;
    height: 100px;
    width: 120px;
    background: #2ecc71;
}
.child-right {
    float: right;
    height: 100px;
    width: 80px;
    background: #e74c3c;
}
```

效果大概是这样：（设置透明度只是为了演示）

<style type="text/css">
.my-demo .parent {
    width: 200px;
    margin: 30px auto;
    border: solid 5px #3498db;
}
.my-demo .child-left{
	opacity: 0.8;
}
.my-demo .child-right {
  opacity: 0.8;
}
.my-demo .child-left {
    float: left;
    height: 100px;
    width: 120px;
    background: #2ecc71;
}
.my-demo .child-right {
    float: right;
    height: 100px;
    width: 80px;
    background: #e74c3c;
}
</style>
<div class="my-demo">
	<div class="parent">
    <div class="child-left"></div>
    <div class="child-right"></div>
</div>
</div>


我们看到的效果是父元素并没有包裹住，两个 float 的子元素，并且它自身的高度为 0。

相信很多前端er都曾为此困惑不已，为什么子元素都 float 会导致父元素高度为 0？据说 clear:both 可以用来清除浮动，那为什么给父元素加上之后没有效果？google，百度一番之后找到了解药—clearfix。

## 什么是clearfix

.clearfix 可以说是很多前端开发者不可缺少的**补丁**。它可以用来闭合浮动，修复父元素高度坍塌的问题。

```
.clearfix:before,
.clearfix:after {
  content: "";
  display: table;
}

.clearfix:after {
  clear: both;
}

.clearfix {
  zoom: 1; /* ie 6/7 */
}
```

用法，还是使用上面的例子

```
<div class="parent clearfix">
    <div class="child-left"></div>
    <div class="child-right"></div>
</div>
```

<div class="my-demo">
	<div class="parent clearfix">
    <div class="child-left"></div>
    <div class="child-right"></div>
</div>
</div>

给父元素加上 clearfix 类名就搞定了。

喜欢折腾的同学肯定知道其实给父容器增加下列属性中的一个都能达到相同效果

```
overflow: auto;
display: table;
position: absolute;
float: left;
```

背后究竟发生了什么？带着问题，继续学习几个新名词。

## 清除浮动 还是 闭合浮动 ?

可能是由于 clear 属性命名的关系，我们经常只会说清除浮动，但是确切地说清除浮动对应的是 clear: left|right|both|none|inherit;

而上面的例子，我们是想让浮动的元素闭合，减少浮动带来的影响，应该是属于闭合浮动的范围。

[那些年我们一起清除过的浮动](http://www.iyunlu.com/view/css-xhtml/55.html)

## 文档流
 
从我接触前端开始，听到的都是文档流，文档流，但真正的称谓应该叫做普通流或常规流（英文为：normal flow ）。我的理解是按照HTML标签的位置顺序把元素从上到小，从左到右逐行排版的过程。

在 css2.1 中提到的 [w3c-定位方案](https://www.w3.org/html/ig/zh/wiki/CSS2/visuren#positioning-scheme)有三种：

> 普通流，包括对块级框的块格式，对行级框的行格式，对块级框和行级框的相对定位。
> 浮动，在浮动模型中，一个框先按照正常排版来摆放，再将它从排版流中取出并尽可能地向左或向右偏移。其它内容可以排在一个浮动的周围。
> 绝对定位，在绝对定位模型中，一个框会从排版流中完全脱离出来（它对后续的兄弟没有影响），并相对其包含块来指定其位置。（包括 absolute, fixed ）

所以浮动也会脱离普通流，但属于一种比较‘特殊’的脱离，其他内容还会围绕在浮动元素周围，这时候父元素无法感知到它的存在。

## BFC

BFC 全称为 Block Formatting Context，很多人直译叫它块格式化上下文。它是CSS2.1规范定义的，是页面 CSS 视觉渲染的一部分，用于决定块盒子的布局及浮动相互影响范围的一个区域。简单来说，BFC 就是一种属性，这种属性会影响着元素的定位以及与其兄弟元素之间的相互作用。

**创建**

下面的情况会产生新的BFC:

- 根元素或其它包含它的元素
- 浮动 (元素的 float 不为 none)
- 绝对定位元素 (元素的 position 为 absolute 或 fixed)
- 行内块 inline-blocks (元素的 display: inline-block)
- 表格单元格 (元素的 display: table-cell，HTML表格单元格默认属性)
- 表格标题 (元素的 display: table-caption, HTML表格标题默认属性)
- overflow 的值不为 visible的元素
- 弹性盒 flex boxes (元素的 display: flex 或 inline-flex)
范围

一个BFC包含创建该上下文元素的所有子元素，但不包括创建了新BFC的子元素的内部元素。

**特性**

BFC最显著的效果是建立一个隔离的空间，断绝空间内外元素相互的作用。当然，还有更多的特性：

- 内部的盒会在垂直方向一个接一个排列（可以看作BFC中有一个的常规流）；
- 处于同一个BFC中的元素相互影响，可能会发生margin collapse；
- 每个元素的margin box的左边，与容器块border box的左边相接触(对于从左往右的格式化，否则相反)。即使存在浮动也是如此；
- BFC就是页面上的一个隔离的独立容器，容器里面的子元素不会影响到外面的元素，反之亦然；
- 计算BFC的高度时，考虑BFC所包含的所有元素，连浮动元素也参与计算；
- 浮动盒区域不叠加到BFC上；
- 看到这里，再回头想想之前的几个小问题：

## 问题解决

### 为什么坍塌？

为什么会坍塌？ float 脱离了普通流，并且创建了新的BFC，而父元素不具备产生 BFC 的条件，所以它的高度为0。

### 如何解决？

通过了解BFC的特性我们知道，BFC会把它包含的浮动元素高度也算在里面，也就是闭合浮动。拿 overflow: auto 举例：
overflow: auto 并不会闭合浮动，而是 overflow: auto 会创建一个新的BFC，避免浮动的元素侵入其他元素。

父元素上clear: both 不起作用？

这应该算是语义理解错了，clear: both 是让两边都不能有浮动元素，清除上方元素“浮动导致高度坍塌”，所以在父元素上用是没有效果的，通常放在浮动元素的下方，同样也会引起父元素拉伸以包裹浮动元素。

### 父元素上clear: both 不起作用？

这应该算是语义理解错了，clear: both 是让两边都不能有浮动元素，清除上方元素“浮动导致高度坍塌”，所以在父元素上用是没有效果的，通常放在浮动元素的下方，同样也会引起父元素拉伸以包裹浮动元素。

## 推荐阅读

<ul>
<li><a href="http://www.iyunlu.com/view/css-xhtml/55.html" target="_blank" rel="external">那些年我们一起清除过的浮动</a></li>
<li><a href="http://www.cnblogs.com/elcarim5efil/p/4745796.html" target="_blank" rel="external">学习块格式化上下文（BlockFormattingContext）</a></li>
<li><a href="https://css-tricks.com/all-about-floats/" target="_blank" rel="external">All About Floats</a></li>
<li><a href="http://stackoverflow.com/questions/12871710/what-does-the-css-rule-clear-both-do" target="_blank" rel="external">Stackoverflow what-does-the-css-rule-clear-both-do</a></li>
<li><a href="http://stackoverflow.com/questions/6196725/how-does-the-css-block-formatting-context-work" target="_blank" rel="external">Stackoverflow how-does-the-css-block-formatting-context-work</a></li>
<li><a href="http://fuseinteractive.ca/blog/understanding-humble-clearfix#.VvjnPRJ94Wo" target="_blank" rel="external">http://fuseinteractive.ca/blog/understanding-humble-clearfix#.VvjnPRJ94Wo</a></li>
<li><a href="http://kayosite.com/block-formatting-contexts-in-detail.html" target="_blank" rel="external">详说 Block Formatting Contexts (块级格式化上下文)</a></li>
</ul>



