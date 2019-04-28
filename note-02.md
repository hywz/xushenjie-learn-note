### 补充标签
1. `<div>` 标签
	自动换行 独占一行
2. `<span>` 标签
	照顾特殊内容 不会自动换行
3. `<iframe>` 标签
	嵌套窗口

### 标签的常见属性
1. id 唯一标识,不重复.
2. class 类名,归到某一类.
3. title 标签描述信息,鼠标悬浮时会出现.

### class
```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style>
		/*style标签内部书写样式*/
		div{
			font-size: 20px;
			background-color: skyblue;
		};
		/*选择器{
			样式名:样式值;
			样式名:样式值;
		}*/
	</style>
</head>
<body>
	<div class="box">
		css层叠样式表,用于控制标签的样式,用来给网页设置样式.
		<br>
		对于一个标签,可以重复设置样式.
	</div>
</body>
</html>
```
### 简单选择器
```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style>
		p{
			font-size: 50px;
			text-align: center;
		}
		.txt{
			background-color: skyblue;
		}
		#p1{
			color: yellow;
		}
	</style>
</head>
<body>
	<p class="txt" id="p1">Hello world!</p>
</body>
</html>
```

### 书写位置
```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<link rel="stylesheet" href="style.css">
	<style>
		p{
			text-align: center;
		}
	</style>
</head>
<body>
	<p style="font-size: 50px">Hello world!</p>
	<!-- 行内样式:耦合性太强,少些. -->
</body>
</html>
```

### 复杂选择器
```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style>
		/*后代选择器*/
		.box .text{
			color: yellow;
		}
		/*交集选择器*/
		.text.text2{
			color: skyblue;
		}
		/*并集选择器*/
		h2,p{
			text-align: center;
		}
		.box{
			font-size: 40px;
		}
		/*通配符*:选中所有标签*/
		*{
			font-weight: bolder;
		}
	</style>
</head>
<body>
	<div class="box">
		<h2 class="title">标题</h2>
		<p class="text">文本1</p>
		<p class="text text2">文本2</p>
	</div>
</body>
</html>
```

###css继承性
```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style>
		a{
			direction: none;
		}
		.box{
			color: skyblue;
			font-size: 50px;
		/*p继承了颜色,字体大小,a继承了字体大小*/
		}
		.box a{
			color: yellow;
		}
	</style>
</head>
<body>
	<div class="box">
		<p>hello,world!</p>
		<a href="#">百度</a>
	</div>
</body>
</html>
```
###层叠性
```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style>
		p{
			color: orange;
		}
		p{
			color: red;
		}
	</style>
</head>
<body>
	<p>Hello,world!</p>
</body>
</html>
```

###权重问题
```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style>
		#text{
			color: red;
		}
		.box{
			color: black;
		}
		div{
			color: orange;
		}
/*		行内样式1000>id选择器100>class选择器10>标签选择器1>继承属性,通配符权重为0
		权重一样的话,后写的会覆盖前边写的(就近原则).*/
	</style>
</head>
<body>
	<div class="box" id="text" style="color: skyblue;">hello,world!</div>
</body>
</html>
```

###常见单位
```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style>
		.box{
			background-color: #B42CC2;
			width: 500px;
			height: 500px;
		}
		p{
			width: 50%;
			height: 50%;
			font-size: 40px;
			color: rgba(33,31,8,.5);
			text-indent: 2em;
			background-color: skyblue;
		}

	</style>
</head>
<body>
	<div class="box">
		<p>
			你好,之华!
<!-- 		颜色单位:
			1.预定义颜色:red,blue...
			2.十六进制:#B42CC2
			3.rgb(red,green,blue)0-255,rgba(254,244,133,.5)
			像素单位:px
			em:相当于当前字号的倍数
			百分比:通常是对于父类的百分比 -->
		</p>
	</div>
</body>
</html>
```

###常用属性
```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style>
		.box{
			width: 500px;
			height: 500px;
			font-style: italic;
			color: skyblue;
			background-color: pink;
			font-family: 微软雅黑;
			font-weight: 800;
			text-align: center;
			text-indent: 2em;
			line-height: 500px;
			font-size: 50px;
			/*单行居中对齐line-height=盒子的高度*/
		}
	</style>
</head>
<body>
	<div class="box">
		不凡学院
	</div>
</body>
</html>
```

###标签的表现形式
1. 块状元素
	自动换行 可以设置宽高有效
	宽度不写的情况下,默认100%
	`<div>` `<h1>`-`<h6>` `<p>` `<ul>` `<li>` `<ol>` `<li>` `<di`> `<dt>` `<dd>` `<table>` `<form>`...
2. 行内元素
	不会自动换行
	设置宽高 无效
	`<span>` `<a>`...
3. 行内块元素
	不会自动换行
	设置宽高 有效 
	`<input>` `<img>` `<button>`...

###标签表现形式的转换
```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style>
		/*display:block块状/inline行内/inline-block行内块*/
		span{
			display: block;
			width: 50px;
			height: 50px;
			background-color: pink;
		}
		ul{
			list-style: none;
		}
		li{
			display: inline-block;
			background-color: skyblue;
			width: 10px;
			height: 50px;
			text-align: center;
			line-height: 50px;
		}
	</style>
</head>
<body>
	<span>不凡学院</span>
	<span>天气很好</span>
	<br>
	<br>
	<br>
	<br>
	<ul>
		<li>1</li><li>2</li><li>3</li><li>4</li><li>5</li>
	</ul>
</body>
</html>
```
