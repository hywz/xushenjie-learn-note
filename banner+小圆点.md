###banner+小圆点的实现
+ html部分
```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>网站首页</title>
	<link rel="stylesheet" href="css/reset.css">
	<link rel="stylesheet" href="css/index.css">
</head>
<body>
	<div class="head">
		<div class="head-c">
			<a href="#" class="logo"></a>
			<ul class="nav">
				<li class="nav-item">
					<a href="首页.html" class="inter on">首页</a>
					<div class="line active"></div>
				</li>
				<li class="nav-item">
					<a href="项目.html" class="inter">项目</a>
					<div class="line"></div>
				</li>
				<li class="nav-item">
					<a href="产品.html" class="inter">产品</a>
					<div class="line"></div>
				</li>
				<li class="nav-item">
					<a href="服务.html" class="inter">服务</a>
					<div class="line"></div>
				</li>
				<li class="nav-item">
					<a href="新闻.html" class="inter">新闻</a>
					<div class="line"></div>
				</li>
				<li class="nav-item">
					<a href="关于.html" class="inter">关于</a>
					<div class="line"></div>
				</li>
			</ul>
		</div>
	</div>
	<!-- banner部分 -->
	<div class="banner">
		<!-- 图片 -->
		<img src="img/首页/banner.png" alt="" class="ban">
		<!-- 小圆点 -->
		<div class="dots">
			<ul class="dot-items">
				<li class="dot active"></li>
				<li class="dot"></li>
				<li class="dot"></li>
				<li class="dot"></li>
				<li class="dot"></li>
			</ul>
		</div>
	</div>
</body>
</html>
```
+ css部分
```css
.head{
	width: 100%;
}
.head-c{
	height: 100px;
	width: 1200px;
	margin: 0 auto;
	line-height: 100px;
	position: relative;
	overflow: hidden;
}
.head .logo{
	background: url(../img/首页/logo.png);
	display: block;
	width: 221px;
	height: 52px;
	margin-top: 24px;
}
.head .nav{
	width: 576px;
	height: 100px;
	display: -webkit-flex;
	display: -moz-flex;
	display: -ms-flex;
	display: -o-flex;
	display: flex;
	justify-content: space-between;
	position: absolute;
	right: 0;
	top: 0;
}
.head .nav .nav-item{
	float: left;
	font-size: 14px;
	width: 36px;
}
.nav .on{
	font-size: 18px;
	color: #668aca;
}
.nav .active{
	display: block;
}
.nav .line{
	height: 1px;
	width: 36px;
	background: #668aca;
	display: none;
	position: relative;
	bottom: 34px;
}
.inter:hover+.line{
	display: block;
}
.inter:hover{
	font-size: 18px;
	color: #668aca;
}
/*banner部分*/
.banner{
	position: relative;
	width: 100%;
}
.banner .ban{
	width: 100%;
}
/*小圆点*/
.banner .dots{
	width: 150px;
	height: 14px;
	left: 50%;
	transform: translateX(-50%);
	position: absolute;
	bottom: 16px;
}
.banner .dot{
	float: left;
	width: 8px;
	height: 8px;
	border-radius: 50%;
	border: 3px solid transparent;
	margin-right: 16px;
	background: white;
	-webkit-background-clip: content-box;
	-moz-background-clip: content-box;
	background-clip: content-box;
	cursor: pointer;
}
.banner .dot:hover{
	border-color: white;
	background: #668aca;
}
.banner .dots .active{
	border-color: white;
	background: #668aca;
}