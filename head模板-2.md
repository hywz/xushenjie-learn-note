### 带二级导航的head模板
+ html
```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>首页</title>
	<link rel="stylesheet" href="reset.css">
	<link rel="stylesheet" href="head.css">
</head>
<body>
	<div class="head">
		<div class="head-c">
			<a href="#" class="logo"></a>
			<ul class="nav">
				<li class="nav-item on">
					<a href="index.html" class="active">
						首页
					</a>
					<span class="line">
					</span>
				</li>
				<li class="nav-item">
					<a href="web/wedding/index.html">
						婚纱礼服
					</a>
					<span class="line">
					</span>
				</li>
				<li class="nav-item">
					<a href="web/jewelry/index.html">
						珠宝配饰
					</a>
					<span class="line">
					</span>
				</li>
				<li class="nav-item">
					<a href="web/activity/index.html">
						最新活动
					</a>
					<span class="line">
					</span>
				</li>
				<li class="nav-item">
					<a href="web/aboutus/index.html">
						关于我们
					</a>
					<span class="line">
					</span>
					<!-- 二级导航 -->
					<ul class="down">
						<li class="down-item">
							<a href="web/designer/index.html">
								设计师
								<span>
									>
								</span>
							</a>
						</li>
						<li class="down-item">
							<a href="web/aboutus/index.html">
								品牌故事
								<span>
									>
								</span>
							</a>
						</li>
					</ul>
				</li>
			</ul>
		</div>
	</div>
</body>
</html>
```
+ css
```css
.head{
	width: 100%;
}
.head-c{
	height: 67px;
	width: 1200px;
	margin: 0 auto;
	line-height: 67px;
	position: relative;
}
.head .logo{
	background: url(logo.png) no-repeat;
	width: 142px;
	height: 34px;
	display: block;
	position: relative;
	top: 16.5px;
}
.head .nav{
	height: 67px;
	width: 571px;
	position: absolute;
	right: 0;
	top: 0;
	display: -webkit-flex;
	display: -moz-flex;
	display: -ms-flex;
	display: -o-flex;
	display: flex;
	justify-content: space-between;
}
.nav .nav-item{
	float: left;
	font-size: 13.37px;
}
.nav-item a{
	color: #666;
}
.nav-item .active{
	color: #1d1d1d;
}
.nav-item .line{
	height: 1px;
	background: #b9ab77;
	display: none;
	position: relative;
	bottom: 23px;
}
.nav-item a:hover{
	color: #1d1d1d;
}
.nav-item a:hover+.line{
	display: block;
}
.nav-item.on .line{
	display: block;
}
/* 二级导航 */
.head .nav .down{
	z-index: 1;
}
.nav-item .down{
	font-size: 10px;
	display: none;
	position: absolute;
	width: 80px;
	right: -13.265px;
	bottom: -30px;
}
.nav-item .down .down-item{
	height: 25px;
	line-height: 25px;
	position: relative;
	text-indent: 1em;
	background: white;
}
.nav-item .down span{
	display: inline-block;
	display: none;
	position: absolute;
	right: 10px;
	top: -2.5px;
}
.nav-item:hover .down{
	display: block;
	background: #DDDDDD;
}
.nav-item .down-item:hover span{
	display: inline-block;
}
.nav-item .down-item:hover{
	background: #DDDDDD;
}
```