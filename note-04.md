###overflow
+ overflow: hidden; 隐藏
+ overflow: visible; 默认
+ overflow: scroll; 水平垂直方向添加滚动条
+ overflow: auto; 根据实际情况添加滚动条

###文档流
+ 自上而下,自左而右
+ 块级元素,独占一行
+ 行内元素 行内块元素 同行展示,这一行占满了,就另起一行 

###浮动
+ 块级元素和行内元素都可以浮动,当一个行内元素浮动以后将会自动变为一个块级元素.
+ 当一个块级元素浮动以后,宽度会默认会被内容撑开,所以当漂浮一个块级元素时我们都会为其指定一个宽度.
+ float:right 改变标签顺序,用得少.

###浮动的表现形式
+ 脱离了文档流,下面的元素会上移.
+ 元素浮动以后即完全脱离文档流,这时不会再影响父元素的高度.也就是浮动元素不会撑开父元素.

###浮动的影响
```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style>
		*{
			padding: 0;
			margin: 0;
		}
		.header{
			height: 200px;
			background-color: blue;
		}
		.main{
			/*height: 500px;*/
			background-color: pink;
		}
		.aside{
			width: 200px;
			height: 500px;
			background-color: skyblue;
			float: left;
		}
		.container{
			height: 500px;
			/*width: 500px;*/
			background-color: deeppink;
			float: left;
		}
		.footer{
			height: 200px;
			background-color: black;
		}
		.clr{
			clear: both;
			/*清除浮动的影响*/
		}
	</style>
</head>
<body>
	<div class="header"></div> 
	<div class="main">
		<div class="aside"></div>
		<div class="container"></div>
		<div class="clr"></div>
	</div> 
	<div class="footer"></div>
</body>
</html>
```

###导航
```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style>
		*{
			padding: 0;
			margin: 0;
		}
		a{
			text-decoration: none;
		}
		ul{
			list-style: none;
		}
		.nav{
			list-style: none;
			margin: 0 auto;
			margin-top: 100px;
			width: 400px;
			height: 100px;
		}
		.nav .nav-item{
			width: 100px;
			height: 1;
			background-color: skyblue;
			float: left;
			text-align: center;
			line-height: 100px;
			cursor: pointer;

		}
		.nav .nav-item a{
			color: white;
		}
		.nav .nav-item:hover{
			background-color: white;
		}
		.nav .nav-item:hover a{
			color: red;
		}
		.nav .nav-item:hover span{
			display: none;
		}
	</style>
</head>
<body>
	<ul class="nav">
		<li class="nav-item">
			<a href="#">首页<span>信息
				</span></a>
		</li>
		<li class="nav-item"><a href="#">娱乐</a></li>
		<li class="nav-item"><a href="#">绯闻</a></li>
		<li class="nav-item"><a href="#">关于</a></li>
	</ul>
</body>
</html>
```

###定位
+ position属性可以把一个元素放到网页中的任何位置 可选值:
	- static默认
	- relative相对定位 不会改变原来元素的特性
	- absolute绝对定位
	- fixed固定定位
	- sticky了解

###绝对定位
```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style>
		*{
			padding: 0;
			margin: 0;
		}
		/*div{*/
/*			position: absolute;
			left: 100px;
			top: 100px;*/
		/*}*/
		.box{
			width: 500px;
			height: 500px;
			background-color: pink;
/*			position: absolute;
			left: 100px;
			top: 100px;*/
			margin: 80px;
		}
		.box1{
			width: 300px;
			height: 300px;
			background-color: skyblue;
		}
		.box2{
			width: 200px;
			height: 200px;
			background-color: green;
			position: absolute;
			left: 100px;
			top: 100px;
		}
		span{
			position: absolute;
			left: 50px;
			top: 50px;
			width: 200px;
			height: 200px;
			background-color: deeppink;
		}
	</style>
</head>
<body>
	<div class="box">
		<div class="box1">
			<div class="box2"></div>
		</div>
		<span>
			hello,world!
		</span>
	</div>
</body>
</html>
```

###固定定位
```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style>
		*{
			padding: 0;
			margin: 0;
		}
		.box{
			height: 500px;
			background-color: pink;
		}
		.box1{
			width: 100px;
			height: 100px;
			background-color: red;
			position: fixed;
			/*相对浏览器,做定位*/
			left: 100px;
			top: 100px;
		}
		.box2{
			height: 1000px;
			background-color: blue;
		}
	</style>
</head>
<body>
	<div class="box">
		<div class="box1"></div>
	</div>
	<div class="box2"></div>
</body>
</html>
```

###index
```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style>
		.box{
			width: 300px;
			height: 300px;
			background-color: pink;
			z-index: 3;
			position: relative;
		}
		.box1{
			width: 200px;
			height: 200px;
			background-color: blue;
			
		}
		.box2{
			width: 100px;
			height: 100px;
			background-color: red;
		}
		.box3{
			width: 100px;
			height: 100px;
			background-color: green;
			z-index: 2;
			position: absolute;
			left: 50px;
			top: 50px;
		}
	</style>
</head>
<body>
	<div class="box">
		<div class="box1">
			<div class="box2"></div>
		</div>
		<div class="box3">
		</div>
	</div>


</body>
</html>
```

###定位案例
```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style>
		*{
			padding: 0;
			margin: 0;
		}
		a{
			text-decoration: none;
		}
		ul{
			list-style: none;
		}
		.main{
			width: 1226px;
			height: 460px;
			background-image: url(xm.jpg);
			background-size: 100%;
			margin: 0 auto;
			margin-top: 140px;
			position: relative;
		}
		.main .category{
			width: 234px;
			height: 460px;
			background:rgba(0,0,0,0.6);
		}
		.category li{
			display: block;
			height: 42px;
			line-height: 42px;
			padding-left: 30px;
			cursor: pointer;
			position: relative;
		}
		.category ul{
			position: relative;
			top: 20px;
		}
		.category a{
			color: white;
			font-size: 14px;
		}
		.category li:hover{
			background-color: #FF6700;
		}
		.category img{
			position: absolute;
			top:12px;
			right: 20px;
			line-height: 16px;
			width: 16px;
			height: 16px;
		}
		.main .arr-l{
			width: 41px;
			height: 69px;
			position: absolute;
			left: 234px;
			top: 50%;
			margin-top: -34.5px;
			background: url(大左箭头.png) no-repeat center;
		}
		.main .arr-r{
			width: 41px;
			height: 69px;
			position: absolute;
			right: 0;
			top: 50%;
			margin-top: -34.5px;
			background: url(大右箭头.png) no-repeat center;
		}
		.main .arr:hover{
			background-color: rgba(0,0,0,0.5);

		}
		.main .pager a{
			width: 6px;
			height: 6px;
			border-radius: 50%;
			display: block;
			background-color: #56373D;
			margin: 1px;
		}
		.main .pager{
			float: left;
			width: 8px;
			height: 8px;
			border-radius: 50%;
			background-color: #8D8D8D;
			margin-right: 10px;
		}
		.main .page{
			position: absolute;
			right: 30px;
			bottom: 25px;
			height: 10px;
		}
		.main .pager a:hover{
			background-color: white;
		}
	</style>
</head>
<body>
	<div class="main">
		<div class="category">
			<ul>
				<li><a href="#">买手机 送话费<img src="右箭头.png" alt=""></a></li>
				<li><a href="#">买手机 送话费<img src="右箭头.png" alt=""></a></li>
				<li><a href="#">买手机 送话费<img src="右箭头.png" alt=""></a></li>
				<li><a href="#">买手机 送话费<img src="右箭头.png" alt=""></a></li>
				<li><a href="#">买手机 送话费<img src="右箭头.png" alt=""></a></li>
				<li><a href="#">买手机 送话费<img src="右箭头.png" alt=""></a></li>
				<li><a href="#">买手机 送话费<img src="右箭头.png" alt=""></a></li>
				<li><a href="#">买手机 送话费<img src="右箭头.png" alt=""></a></li>
				<li><a href="#">买手机 送话费<img src="右箭头.png" alt=""></a></li>
				<li><a href="#">买手机 送话费<img src="右箭头.png" alt=""></a></li>
			</ul>
		</div>
		<a href="#" class="arr-l arr"></a>
		<a href="#" class="arr-r arr"></a>
		<ul class="page">
			<li class="pager"><a href="#"></a></li>
			<li class="pager"><a href="#"></a></li>
			<li class="pager"><a href="#"></a></li>
			<li class="pager"><a href="#"></a></li>
			<li class="pager"><a href="#"></a></li>
		</ul>
	</div>
</body>
</html>
```