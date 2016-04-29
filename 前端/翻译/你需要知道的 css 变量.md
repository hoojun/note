# 你需要知道的 css 变量

当web项目变得比较大的时候，它们的css通常会变得庞大而凌乱。为了解决这个问题，新的css变量很快得到主流浏览器的支持，让开发者可以重用和方便地编写重复出现的css属性。

以前我们都是使用sass和less 这个用工具来解决这些问题。但是在使用之前，我们需要预处理或者编译，然后使用。现在css变量得到了原生的支持。可以直接在浏览器中直接使用了。

## 定义和使用 css变量

css 变量遵循其他方式定义 css 的范围和继承规则，最容易的使用它们的方式是定义全局变量，通过在`:root` 伪类中添加声明，以至于所有的选择器都可以继承至它.

```
:root{
    --awesome-blue: #2196F3;
}
```

我们可以使用`var(...)`的语法方式访问变量中的值。需要注意的是，变量名称是大小写敏感的。因此`--foo != --FOO`.

```
.some-element{
    background-color: var(--awesome-blue);
}
```

## 浏览器支持情况

现在，只有Firefox 直接支持 css 变量。然而，chrome 49 以后的版本也将默认支持该项特性。如果使用的老版本的 chrome 48. 你可以通过 `chrome://flags/` 然后找到 ` Enable experimental Web Platform features` 开启该项特性，可以从[Can I Use CSS Variables](http://caniuse.com/#search=css-variables)查看更多的详细信息。

## 例子1 - 主题颜色

当我们需要一遍又一遍地使用相同的规则用于多个元素时，CSS中的变量是非常有用的。比如，在主题中重复的颜色，取代为了复用相同的颜色，我门每次都要赋值粘贴的方式。我们可以用一个变量来代替。

现在，如果你的客户不喜欢蓝色，我们只需要在定义css变量的地方修改就可以了。如果没有css变量。我们需要先搜索然后替换每一个出现的地方。

**css代码1**

```
:root{
    --primary-color: #B1D7DC;
    --accent-color: #FF3F90;
}

html{
    background-color: var(--primary-color);
}

h3{
    border-bottom: 2px solid var(--primary-color);
}

button{
    color: var(--accent-color);
    border: 1px solid var(--accent-color);
}
```

**html代码片段**

```
<div class="container">
    <h3>Dialog Window</h3>
    <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Morbi vulputate vitae nibh sed sodales. Maecenas non vulputate lacus, sed convallis eros. Cras sollicitudin, felis sit amet pharetra mattis, metus lectus ullamcorper magna.</p>
    <button>Confirm</button>
</div>
```

**css代码2**

```
*{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

html{
    padding: 30px;
    font: normal 13px/1.5 sans-serif;
    color: #546567;
    background-color: var(--primary-color);
}

.container{
    background: #fff;
    padding: 20px;
}

h3{
    padding-bottom: 10px;
    margin-bottom: 15px;
}

p{
    background-color: #fff;
    margin: 15px 0;
}

button{
    font-size: 13px;
    padding: 8px 12px;
    background-color: #fff;
    border-radius: 3px;
    box-shadow: none;
    text-transform: uppercase;
    font-weight: bold;
    cursor: pointer;
    opacity: 0.8;
    outline: 0;
}

button:hover{
    opacity: 1;
}
```

## 例子2 -  可读的属性名字

css 变量另外一个非常有用的地方是当我们想保存一个复杂的属性时，我们不需要记住它. 比如像`box-shadow`,`transform`,`font`这些具有多个参数值的css规则。

通过变量来替换属性，我们让它变得语意化并且可读。

**css 代码片段**

```
:root{
    --tiny-shadow: 0 2px 1px 0 rgba(0, 0, 0, 0.2);
    --animate-right: translateX(20px);
}
li{
    box-shadow: var(--tiny-shadow);
}
li:hover{
    transform: var(--animate-right);
}
```

**html 代码片段**

```html
<ul>
    <li>Hover on me!</li>
    <li>Hover on me!</li>
    <li>Hover on me!</li>
</ul>
```

**css 代码片段**
```css
html{
    background-color: #F9F9F9;
}
ul{
    padding: 20px;
    list-style: none;
    width: 300px;
}
li{
    font: normal 18px sans-serif;
    padding: 20px;
    transition: 0.4s;
    margin: 10px;
    color: #444;
    background-color: #fff;
    cursor: pointer;
}
```

## 例子3 - 动态改变变量

当一个自定义的变量被多次声明，标准的层级规则有助于解决样式冲突问题，在样式表中最低定义的将会覆盖在它上面定义的变量。

下面的代码演示了在用户操作的时候动态的改变属性是多么的方便，同时还能保持代码清晰简洁。


**css 代码片段**

```
.blue-container{
	--title-text: 18px;
	--main-text: 14px;
}
.blue-container:hover{
	--title-text: 24px;
	--main-text: 16px;
}
.green-container:hover{
	--title-text: 30px;
	--main-text: 18px;
}
.title{
	font-size: var(--title-text);
}
.content{
	font-size: var(--main-text);
}
```

**html 代码片段**

```
<div class="blue-container">
	<div class="green-container">
		<div class="container">
			<p class="title">A Title</p>
			<p class="content">Hover on the different color areas to change the size of this text and the title.</p>
		</div>
	</div>
</div>
```

**css 代码片段**

```
*{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

html{
    background: #eee;
    padding: 30px;
    font: 500 14px sans-serif;
    color: #333;
    line-height: 1.5;
}

.blue-container{
	background: #64B5F6;
	padding-left: 50px;
}

.green-container{
	background: #AED581;
	padding-left: 50px;
}

.container{
    background: #fff;
    padding: 20px;
}

p{
	transition: 0.4s;
}

.title{
	font-weight: bold;
}
```

## 几个使用技巧

正如你说看见的，css 变量使用起来是非常的简单，并且用不了多的时间，开发者们到处都可以使用它们了。在文章的最后，还有几件事情值得提一下：


- `var()` 函数还有第二参数，当变量没有提供值的时候，它可以作为一个备用的值。
```
width: var(--custom-width, 20%);
```

- 可以嵌套自定义属性
```
--base-color: #f93ce9;
--background-gradient: linear-gradient(to top, var(--base-color), #444);
```

- 可以和`calc()`函数结合使用。不幸的是，现在只有Firefox支持。
```
--container-width: 1000px;
max-width: calc(var(--container-width) / 2);
```

如果原意尝试css的新功能，但请记住，这仍然是一种实验性的技术。就目前而言，不建议在敏感的项目中使用。




