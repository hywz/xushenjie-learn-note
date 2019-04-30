###hover背景图的切换
+ html部分
```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>简装首页</title>
	<link rel="stylesheet" href="css/reset.css">
	<link rel="stylesheet" href="css/背景图切换.css">
</head>
<body>
	<div class="pho">
		<div class="bg">
			<img src="img/首页/沙发.png" alt="" class="picture">
			<div class="line"></div>
		</div>
		<div class="text">
			<p>
				<span class="cn">床</span>
				<span class="en">BED</span>
			</p>
		</div>
	</div>
</body>
</html>
```
+ css部分
```css
.pho{
	/*窗口垂直居中*/
	position: absolute;
	left: 50%;
	top: 50%;
	-webkit-transform: translate(-50%, -50%);
	-ms-transform: translate(-50%, -50%);
	-o-transform: translate(-50%, -50%);
	transform: translate(-50%, -50%);
	height: 114px;
	width: 164px;
	text-align: center;
}
.pho .bg{
	/*背景图片像素大小*/
	width: 164px;
	height: 86px;
	/*图片垂直居中行高一定要有*/
	line-height: 86px;
}
.pho .bg .picture{
	/*图片垂直居中*/
	vertical-align: middle;
}
.pho .cn{
	font-size: 14px;
}
.pho .en{
	font-size: 12px;
}
.pho .line{
	width: 16px;
	height: 1px;
	position: absolute;
	background: #668aca;
	left: 74px;
	bottom: 0;
	display: none;
}
.text{
	margin-top: 7px;
}
.bg:hover{
	background: url(../img/首页/center-bg.png);
}
.bg:hover+.text{
	color: #668aca;
}
.bg:hover .line{
	display: block;
}
```