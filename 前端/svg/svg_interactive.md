# SVG 交互

## 使用CSS

除了定义对象的属性外，也可以通过CSS来样式化填充和描边。语法和在html里使用CSS一样，只不过你要把background-color、border改成fill和stroke。注意，不是所有的属性都能用CSS来设置。上色和填充的部分一般是可以用CSS来设置的，比如fill，stroke，stroke-dasharray等，但是不包括下面会提到的渐变和图案等功能。另外，width、height，以及路径的命令等等，都不能用css设置。判断它们能不能用CSS设置还是比较容易的。

CSS可以利用style属性插入到元素的行间：

```
<rect x="10" height="180" y="10" width="180" style="stroke: black; fill: red;"/>
```

或者利用`<style>`。就像在html里这样的`<style>`一般放在`<head>`里，在svg里`<style>`则放在`<defs>`标签里。

<svg width="200" height="200" xmlns="http://www.w3.org/2000/svg" version="1.1">
  <defs>
    <style type="text/css">
       #MyRect {
         stroke: black;
         fill: red;
       }
    </style>
  </defs>
  <rect x="10" height="180" y="10" width="180" id="MyRect"/>
</svg>

```
<svg width="200" height="200" xmlns="http://www.w3.org/2000/svg" version="1.1">
  <defs>
    <style type="text/css">
       #MyRect {
         stroke: black;
         fill: red;
       }
    </style>
  </defs>
  <rect x="10" height="180" y="10" width="180" id="MyRect"/>
</svg>
```

如上把样式放到一块你可以更轻松地调整一大组元素的样式，同样你也可以使用hover这样的伪类来创建翻转之类的效果:

```
#MyRect:hover {
   stroke: black;
   fill: blue;
 }
```

<svg width="200" height="200" xmlns="http://www.w3.org/2000/svg" version="1.1">
  <defs>
    <style type="text/css">
       #MyRect {
         stroke: black;
         fill: red;
       }
       #MyRect:hover {
       	stroke:red;
       	fill: black;
       }
    </style>
  </defs>
  <rect x="10" height="180" y="10" width="180" id="MyRect"/>
</svg>

所有的SVG元素的初始display值都是inline

## svg clip

擦除已经创建的元素的部分内容，最初看起来有点矛盾。但是如果你打算在SVG中创建一个半圆形，你将很快发现下面的属性的作用了。Clipping用来移除在别处定义的元素的部分内容。在这里，任何半透明效果都是不行的。它只能要么显示要么不显示。

<svg version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
  <defs>
    <clipPath id="cut-off-bottom">
      <rect x="0" y="0" width="200" height="100"/>
    </clipPath>
  </defs>
  <circle cx="100" cy="100" r="100" fill="red" clip-path="url(#cut-off-bottom)" />
</svg>

```
<svg version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
  <defs>
    <clipPath id="cut-off-bottom">
      <rect x="0" y="0" width="200" height="100"/>
    </clipPath>
  </defs>
  <circle cx="100" cy="100" r="100" fill="red" clip-path="url(#cut-off-bottom)" />
</svg>
```

svg 默认填充的颜色是黑色

## 嵌入矢量图像

<svg version="1.1"
     xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"
     width="200" height="200">
  <image x="90" y="-65" width="128" height="146" transform="rotate(45)"
     xlink:href="https://developer.mozilla.org/media/img/mdn-logo.png"/>
</svg>

```
<svg version="1.1"
     xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"
     width="200" height="200">
  <image x="90" y="-65" width="128" height="146" transform="rotate(45)"
     xlink:href="https://developer.mozilla.org/media/img/mdn-logo.png"/>
</svg>
```