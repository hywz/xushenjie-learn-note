### 网站首页head模板
#### 大多数网站首页可以套用的head模板:

- html内容
```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>网站首页</title>
	<link rel="stylesheet" href="css/reset.css">
	<link rel="stylesheet" href="css/head.css">
</head>
<body>
	<div class="head">
		<!-- 版心 -->
		<div class="head-c">
			<!-- logo -->
			<a href="#" class="logo"></a>
			<!-- 导航 -->
			<ul class="nav">
				<li class="nav-item">
					<a href="首页.html" class="inter on">
					首页
					</a>
					<div class="line active"></div>
				</li>
				<li class="nav-item">
					<a href="项目.html" class="inter">
					项目
					</a>
					<div class="line"></div>
				</li>
				<li class="nav-item">
					<a href="产品.html" class="inter">
					产品
					</a>
					<div class="line"></div>
				</li>
				<li class="nav-item">
					<a href="服务.html" class="inter">
					服务
					</a>
					<div class="line"></div>
				</li>
				<li class="nav-item">
					<a href="新闻.html" class="inter">
					新闻
					</a>
					<div class="line"></div>
				</li>
				<li class="nav-item">
					<a href="关于.html" class="inter">
					关于
					</a>
					<div class="line"></div>
				</li>
			</ul>
		</div>
	</div>
</body>
</html>
```
- reset.css
```css
/* http://meyerweb.com/eric/tools/css/reset/ 
   v2.0 | 20110126
   License: none (public domain)
*/

html, body, div, span, applet, object, iframe,
h1, h2, h3, h4, h5, h6, p, blockquote, pre,
a, abbr, acronym, address, big, cite, code,
del, dfn, em, img, ins, kbd, q, s, samp,
small, strike, strong, sub, sup, tt, var,
b, u, i, center,
dl, dt, dd, ol, ul, li,
fieldset, form, label, legend,
table, caption, tbody, tfoot, thead, tr, th, td,
article, aside, canvas, details, embed, 
figure, figcaption, footer, header, hgroup, 
menu, nav, output, ruby, section, summary,
time, mark, audio, video {
	margin: 0;
	padding: 0;
	border: 0;
	font-size: 100%;
	font: inherit;
	vertical-align: baseline;
	text-decoration: none;
}
/* HTML5 display-role reset for older browsers */
article, aside, details, figcaption, figure, 
footer, header, hgroup, menu, nav, section {
	display: block;
}
body {
	line-height: 1;
}
ol, ul {
	list-style: none;
}
blockquote, q {
	quotes: none;
}
blockquote:before, blockquote:after,
q:before, q:after {
	content: '';
	content: none;
}
a{
	text-decoration: none;
}
table {
	border-collapse: collapse;
	border-spacing: 0;
}
/*设置字体*/
@font-face {
    font-family: 'Regular'; 
    src: url('../font/PingFangSC-Regular-sans-serif.ttf');
    font-weight: normal;
    font-style: normal;
  }
@font-face {
    font-family: 'Light'; 
    src: url('../font/PingFangSC-Light-sans-serif.ttf');
    font-weight: normal;
    font-style: normal;
  }
@font-face {
    font-family: 'Ultralight'; 
    src: url('../font/PingFangSC-Ultralight-sans-serif.ttf');
    font-weight: normal;
    font-style: normal;
  }
 @font-face {
    font-family: 'Thin'; 
    src: url('../font/PingFangSC-Thin-sans-serif.ttf');
    font-weight: normal;
    font-style: normal;
  }
html,body,a { 
	font-family: Thin, sans-serif;
	color: #767676;
 }
 ```
- head.css
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
	<!-- flex布局 -->
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
```
- 具体宽高等像素值由各个网站规定而定.