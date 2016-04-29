# 简介

SVG 意为可缩放矢量图形（Scalable Vector Graphics）。
SVG 使用 XML 格式定义图像。

什么是SVG？

- SVG 指可伸缩矢量图形 (Scalable Vector Graphics)
- SVG 用来定义用于网络的基于矢量的图形
- SVG 使用 XML 格式定义图形
- SVG 图像在放大或改变尺寸的情况下其图形质量不会有所损失
- SVG 是万维网联盟的标准
- SVG 与诸如 DOM 和 XSL 之类的 W3C 标准是一个整体

SVG 是 W3C 推荐标准

SVG 于 2003 年 1 月 14 日成为 W3C 推荐标准。

与其他图像格式相比，使用 SVG 的优势在于：

- SVG 可被非常多的工具读取和修改（比如记事本）
- SVG 与 JPEG 和 GIF 图像比起来，尺寸更小，且可压缩性更强。
- SVG 是可伸缩的
- SVG 图像可在任何的分辨率下被高质量地打印
- SVG 可在图像质量不下降的情况下被放大
- SVG 图像中的文本是可选的，同时也是可搜索的（很适合制作地图）
- SVG 可以与 Java 技术一起运行
- SVG 是开放的标准
- SVG 文件是纯粹的 XML

在html5中 `<svg>` 标签可以直接插入到 html 页面中使用。

# 标签

## rect 标签

用来创建矩形，以及矩形的变种

<svg version="1.2" height="350">
  <rect height="300" width="100"
        x="50" y="40"
        rx="20"
        ry="20"
        style="
          fill: rgb(255,255,0);
          stroke-width: 2;
          stroke: rgb(0,0,0);
          fill-opacity: 0.1;
          stroke-opacity: 0.6;
        "></rect>
</svg>

```html
<svg version="1.2" height="350">
  <rect height="300" width="100"
        x="50" y="40"
        rx="20"
        ry="20"
        style="
          fill: rgb(255,255,0);
          stroke-width: 2;
          stroke: rgb(0,0,0);
          fill-opacity: 0.1;
          stroke-opacity: 0.6;
        "></rect>
</svg>
```

1. rect 元素的 width 和 height 属性定义矩形的高度和宽度
2. style 属性用来定义 css 属性
3. css 的 fill 属性定义矩形的填充颜色
4. css 的 stroke-width 属性定义矩形边框的宽度
5. css 的 stroke 属性定义矩形边框的颜色
6. x 定义矩形左侧的位置
7. y 定义矩形顶端的位置
8. rx, ry 可以使矩形产生圆角

## circle 标签

创建圆形

<svg>
  <circle r="50" cx="55" cy="55" stroke="black" stroke-width="2" fill="red"></circle>
</svg>

1. 测试发现, chrome 下面svg的默认大小是 300 * 150 的大小
2. cx 和 cy 属性定义圆点的 x 和 y 坐标。如果省略 cx 和 cy，圆的中心会被设置为 (0, 0)
3. r 属性定义圆的半径。

```html
<svg>
  <circle r="50" cx="55" cy="55" stroke="black" stroke-width="2" fill="red"></circle>
</svg>
```

## ellipse 标签

用来创建椭圆

<svg>
  <ellipse rx="50" ry="25" cx="55" cy="30" fill="red" stroke="black" stroke-width="2"></ellipse>
</svg>

```
<svg>
  <ellipse rx="50" ry="25" cx="55" cy="30" fill="red" stroke="black" stroke-width="2"></ellipse>
</svg>
```

1. rx 属性定义水平半径
2. ry 属性定义垂直半径

## line 标签

用来创建线条

<svg>
  <line x1="5" y1="5" x2="200" y2="100" stroke-width="2" stroke="red"></line>
</svg>

```
<svg>
  <line x1="5" y1="5" x2="200" y2="100" stroke-width="2" stroke="red"></line>
</svg>
```

1. x1 属性在 x 轴定义线条的开始
2. y1 属性在 y 轴定义线条的开始
3. x2 属性在 x 轴定义线条的结束
4. y2 属性在 y 轴定义线条的结束

## polygon 标签

用来创建含有不少于三个边的图形

<svg width="400" height="400">
  <polygon points="120,100 200,210 80,250" fill="#ccc" stroke="#000" stroke-width="1"></polygon>
  </svg>

<svg width="400" height="400">
  <polygon points="220,100 300,210 170,250 123,234" fill="#ccc" stroke="#000" stroke-width="1"></polygon>
</svg>

```
<!-- 三角形 -->
<svg width="400" height="400">
  <polygon points="120,100 200,210 80,250" fill="#ccc" stroke="#000" stroke-width="1"></polygon>
  </svg>

<!-- 四边形 -->
<svg width="400" height="400">
  <polygon points="220,100 300,210 170,250 123,234" fill="#ccc" stroke="#000" stroke-width="1"></polygon>
</svg>
```

1. points 属性定义多边形每个角的 x 和 y 坐标


## polyline 标签

`<polyline>` 标签用来创建仅包含直线的形状。

<svg>
<polyline points="2,2 2,20 20,20 20,40 40,40 40,60" fill="none" stroke="black" stroke-width="2"></polyline>
</svg>

```
<svg>
  <polyline points="2,2 2,20 20,20 20,40 40,40 40,60" fill="none" stroke="black" stroke-width="2"></polyline>
</svg>
```

## path 标签

`<path>` 标签用来定义路径

下面的命令可用于路径数据：

- M = moveto
- L = lineto
- H = horizontal lineto
- V = vertical lineto
- C = curveto
- S = smooth curveto
- Q = quadratic Belzier curve
- T = smooth quadratic Belzier curveto
- A = elliptical Arc
- Z = closepath

**注释：**以上所有命令均允许小写字母。大写表示绝对定位，小写表示相对定位。

```
<svg height="210" width="400">
  <path d="M150 0 L75 200 L225 200 Z" />
</svg>
```

<svg height="210" width="400">
  <path d="M150 0 L75 200 L225 200 Z" />
</svg>


**贝斯曲线**

The following example creates a quadratic Bézier curve, where A and C are the start and end points, B is the control point:

下面的例子创建了一个贝斯曲线，A和C的起点和终止点，B是控制点。

<svg height="400" width="450">
  <path id="lineAB" d="M 100 350 l 150 -300" stroke="red"
  stroke-width="3" fill="none" />
  <path id="lineBC" d="M 250 50 l 150 300" stroke="red"
  stroke-width="3" fill="none" />
  <path d="M 175 200 l 150 0" stroke="green" stroke-width="3"
  fill="none" />
  <path d="M 100 350 q 150 -300 300 0" stroke="blue"
  stroke-width="5" fill="none" />
  <!-- Mark relevant points -->
  <g stroke="black" stroke-width="3" fill="black">
    <circle id="pointA" cx="100" cy="350" r="3" />
    <circle id="pointB" cx="250" cy="50" r="3" />
    <circle id="pointC" cx="400" cy="350" r="3" />
  </g>
  <!-- Label the points -->
  <g font-size="30" font-family="sans-serif" fill="black" stroke="none"
  text-anchor="middle">
    <text x="100" y="350" dx="-30">A</text>
    <text x="250" y="50" dy="-10">B</text>
    <text x="400" y="350" dx="30">C</text>
  </g>
</svg>

```
<svg height="400" width="450">
  <path id="lineAB" d="M 100 350 l 150 -300" stroke="red"
  stroke-width="3" fill="none" />
  <path id="lineBC" d="M 250 50 l 150 300" stroke="red"
  stroke-width="3" fill="none" />
  <path d="M 175 200 l 150 0" stroke="green" stroke-width="3"
  fill="none" />
  <path d="M 100 350 q 150 -300 300 0" stroke="blue"
  stroke-width="5" fill="none" />
  <!-- Mark relevant points -->
  <g stroke="black" stroke-width="3" fill="black">
    <circle id="pointA" cx="100" cy="350" r="3" />
    <circle id="pointB" cx="250" cy="50" r="3" />
    <circle id="pointC" cx="400" cy="350" r="3" />
  </g>
  <!-- Label the points -->
  <g font-size="30" font-family="sans-serif" fill="black" stroke="none"
  text-anchor="middle">
    <text x="100" y="350" dx="-30">A</text>
    <text x="250" y="50" dy="-10">B</text>
    <text x="400" y="350" dx="30">C</text>
  </g>
</svg>
```

注意这里的大写字母和小写字母的区别

注意`<path id="lineAB" d="M 100 350 l 150 -300" stroke="red" stroke-width="3" fill="none" />` 里面的`M 100 350 l 150 -300`。大写字母表示绝对路径，小写字母表示相对路径。`l` 后面的的坐标`150 -300` 是相对于前面的`M`指定的坐标`100 350` 来计算的。 


这个路径用起来比较麻烦。建议使用 svg 编辑器

## Text 

<svg height="30" width="200" xmlns:xlink="http://www.w3.org/1999/xlink">
  <a xlink:href="http://www.w3schools.com/svg/" target="_blank">
    <text x="0" y="15" fill="red">I love SVG!</text>
  </a>
</svg>

```
<svg height="30" width="200" xmlns:xlink="http://www.w3.org/1999/xlink">
  <a xlink:href="http://www.w3schools.com/svg/" target="_blank">
    <text x="0" y="15" fill="red">I love SVG!</text>
  </a>
</svg>
```

## Stroke 

svg 提供了丰富的画笔🖌️样式

- stroke
- stroke-width
- stroke-linecap
- stroke-dasharray

<svg height="80" width="300">
  <g fill="none">
    <path stroke="red" d="M5 20 l215 0" />
    <path stroke="black" d="M5 40 l215 0" />
    <path stroke="blue" d="M5 60 l215 0" />
  </g>
</svg>

```
<svg height="80" width="300">
  <g fill="none">
    <path stroke="red" d="M5 20 l215 0" />
    <path stroke="black" d="M5 40 l215 0" />
    <path stroke="blue" d="M5 60 l215 0" />
  </g>
</svg>
```

<svg height="80" width="300">
  <g fill="none" stroke="black">
    <path stroke-width="2" d="M5 20 l215 0" />
    <path stroke-width="4" d="M5 40 l215 0" />
    <path stroke-width="6" d="M5 60 l215 0" />
  </g>
</svg>

```
<svg height="80" width="300">
  <g fill="none" stroke="black">
    <path stroke-width="2" d="M5 20 l215 0" />
    <path stroke-width="4" d="M5 40 l215 0" />
    <path stroke-width="6" d="M5 60 l215 0" />
  </g>
</svg>
```

<svg height="80" width="300">
  <g fill="none" stroke="black" stroke-width="6">
    <path stroke-linecap="butt" d="M5 20 l215 0" />
    <path stroke-linecap="round" d="M5 40 l215 0" />
    <path stroke-linecap="square" d="M5 60 l215 0" />
  </g>
</svg>

```
<svg height="80" width="300">
  <g fill="none" stroke="black" stroke-width="6">
    <path stroke-linecap="butt" d="M5 20 l215 0" />
    <path stroke-linecap="round" d="M5 40 l215 0" />
    <path stroke-linecap="square" d="M5 60 l215 0" />
  </g>
</svg>
```

<svg height="80" width="300">
  <g fill="none" stroke="black" stroke-width="4">
    <path stroke-dasharray="5,5" d="M5 20 l215 0" />
    <path stroke-dasharray="10,10" d="M5 40 l215 0" />
    <path stroke-dasharray="20,10,5,5,5,10" d="M5 60 l215 0" />
  </g>
</svg>

```
<svg height="80" width="300">
  <g fill="none" stroke="black" stroke-width="4">
    <path stroke-dasharray="5,5" d="M5 20 l215 0" />
    <path stroke-dasharray="10,10" d="M5 40 l215 0" />
    <path stroke-dasharray="20,10,5,5,5,10" d="M5 60 l215 0" />
  </g>
</svg>
```

# 滤镜

## 简介

SVG 滤镜用来向形状和文本添加特殊的效果。

在 SVG 中，可用的滤镜有：

- feBlend
- feColorMatrix
- feComponentTransfer
- feComposite
- feConvolveMatrix
- feDiffuseLighting
- feDisplacementMap
- feFlood
- feGaussianBlur
- feImage
- feMerge
- feMorphology
- feOffset
- feSpecularLighting
- feTile
- feTurbulence
- feDistantLight
- fePointLight
- feSpotLight

**注释：**您可以在每个 SVG 元素上使用多个滤镜！

## 高斯模糊

必须在 `<defs>` 标签中定义 SVG 滤镜。

高斯模糊（Gaussian Blur）

`<filter>` 标签用来定义 SVG 滤镜。`<filter>` 标签使用必需的 id 属性来定义向图形应用哪个滤镜？

`<filter>` 标签必须嵌套在 `<defs>` 标签内。`<defs>` 标签是 definitions 的缩写，它允许对诸如滤镜等特殊元素进行定义。

```
<svg>
  <defs>
    <filter id="gaussian_blur">
      <feGaussianBlur in="SourceGraphic" stdDeviation="3"></feGaussianBlur>
    </filter>
  </defs>
  <ellipse cx="100" cy="50" rx="70" ry="30" fill="red" stroke-width="4" stroke="black" filter="url(#gaussian_blur)"></ellipse>
</svg>
```

<svg>
  <defs>
    <filter id="gaussian_blur">
      <feGaussianBlur in="SourceGraphic" stdDeviation="3"></feGaussianBlur>
    </filter>
  </defs>
  <ellipse cx="100" cy="50" rx="70" ry="30" fill="red" stroke-width="4" stroke="black" filter="url(#gaussian_blur)"></ellipse>
</svg>

代码解释：

- `<filter>` 标签的 id 属性可为滤镜定义一个唯一的名称（同一滤镜可被文档中的多个元素使用）
- `filter:url` 属性用来把元素链接到滤镜。当链接滤镜 id 时，必须使用 # 字符
- 滤镜效果是通过 `<feGaussianBlur>` 标签进行定义的。fe 后缀可用于所有的滤镜
- `<feGaussianBlur>` 标签的 `stdDeviation` 属性可定义模糊的程度
- `in="SourceGraphic"` 这个部分定义了由整个图像创建效果

# 渐变

SVG 渐变必须在 <defs> 标签中进行定义。

渐变是一种从一种颜色到另一种颜色的平滑过渡。另外，可以把多个颜色的过渡应用到同一个元素上。

在 SVG 中，有两种主要的渐变类型：

- 线性渐变

- 放射性渐变

## 线性渐变

<linearGradient> 可用来定义 SVG 的线性渐变。

<linearGradient> 标签必须嵌套在 <defs> 的内部。<defs> 标签是 definitions 的缩写，它可对诸如渐变之类的特殊元素进行定义。

线性渐变可被定义为水平、垂直或角形的渐变：

- 当 y1 和 y2 相等，而 x1 和 x2 不同时，可创建水平渐变
- 当 x1 和 x2 相等，而 y1 和 y2 不同时，可创建垂直渐变
- 当 x1 和 x2 不同，且 y1 和 y2 不同时，可创建角形渐变

**水平渐变**

```
<svg >
  <defs>
    <linearGradient id="orange_red" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" style="stop-color:rgb(255,255,0);stop-opacity:1"/>
      <stop offset="100%" style="stop-color:rgb(255,0,0);stop-opacity:1"/>
    </linearGradient>
  </defs>
  <ellipse cx="100" cy="60" rx="85" ry="55" style="fill:url(#orange_red)"/>
</svg>
```

<svg >
  <defs>
    <linearGradient id="orange_red" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" style="stop-color:rgb(255,255,0);stop-opacity:1"/>
      <stop offset="100%" style="stop-color:rgb(255,0,0);stop-opacity:1"/>
    </linearGradient>
  </defs>
  <ellipse cx="100" cy="60" rx="85" ry="55" style="fill:url(#orange_red)"/>
</svg>

代码解释：

- `<linearGradient>` 标签的 id 属性可为渐变定义一个唯一的名称

- `fill:url(#orange_red)` 属性把 ellipse 元素链接到此渐变

- `<linearGradient>` 标签的 x1、x2、y1、y2 属性可定义渐变的开始和结束位置

- 渐变的颜色范围可由两种或多种颜色组成。每种颜色通过一个 `<stop>` 标签来规定。offset 属性用来定义渐变的开始和结束位置。

**垂直渐变**

<svg>
  <defs>
    <linearGradient id="orange_red" x1="0%" y1="0%" x2="0%" y2="100%">
      <stop offset="0%" style="stop-color:rgb(255,255,0);stop-opacity:1"/>
      <stop offset="100%" style="stop-color:rgb(255,0,0);stop-opacity:1"/>
    </linearGradient>
  </defs>
  <ellipse cx="100" cy="60" rx="85" ry="55" style="fill:url(#orange_red)"/>
</svg>

```
<svg>
  <defs>
    <linearGradient id="orange_red" x1="0%" y1="0%" x2="0%" y2="100%">
      <stop offset="0%" style="stop-color:rgb(255,255,0);stop-opacity:1"/>
      <stop offset="100%" style="stop-color:rgb(255,0,0);stop-opacity:1"/>
    </linearGradient>
  </defs>
  <ellipse cx="100" cy="60" rx="85" ry="55" style="fill:url(#orange_red)"/>
</svg>
```

## 放射性渐变

`<radialGradient>` 用来定义放射性渐变。

`<radialGradient>` 标签必须嵌套在 `<defs>` 中。`<defs>` 标签是 definitions 的缩写，它允许对诸如渐变等特殊元素进行定义。

```
<svg>
  <defs>
    <radialGradient id="grey_blue" cx="50%" cy="50%" r="50%" fx="50%" fy="50%">
      <stop offset="0%" style="stop-color:rgb(255,255,0); stop-opacity:0"/>
      <stop offset="100%" style="stop-color:rgb(255,0,0); stop-opacity:1"/>
    </radialGradient>
  </defs>
  <circle r="50" cx="55" cy="55" fill="url(#grey_blue)"></circle>
</svg>
```

<svg>
  <defs>
    <radialGradient id="grey_blue" cx="50%" cy="50%" r="50%" fx="50%" fy="50%">
      <stop offset="0%" style="stop-color:rgb(255,255,0); stop-opacity:0"/>
      <stop offset="100%" style="stop-color:rgb(255,0,0); stop-opacity:1"/>
    </radialGradient>
  </defs>
  <circle r="50" cx="55" cy="55" fill="url(#grey_blue)"></circle>
</svg>
