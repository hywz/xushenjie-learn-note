###背景图片
```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style>
		.box{
			width: 400px;
			height: 400px;
			background-color: skyblue;
			background-image: url(avatar.jpg);
			background-repeat: no-repeat;
			background-position: 10px 200px;
		}
		.img{
			width: 100px;
			height: 100px;
			background-color: deeppink;
			background-image: url(img.png);
			background-repeat: no-repeat;
			background-position: -50px -100px;
		}
		.box1{
			height: 1000px;
			background-color: green;
			opacity: .4;
		}
		body{
			background: url(avatar.jpg) no-repeat center fixed;
			background-attachment: scroll fixed;
		}
	</style>
</head>
<body>
	<div class="box">
		
	</div>
	<div class="img">
		
	</div>
	<div class="box1">
		
	</div>
</body>
</html>
```

###盒子模型
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
			background-color: deeppink;
			content: 物品内容;
/*			padding: 内边距(填充物);
			border: 边框;
			margin: 外边距 盒子与盒子之间的间距;
			设置的宽高作用在content内容区域*/
}
	</style>
</head>
<body>
	<div class="box">
		
	</div>
</body>
</html>
```

###padding
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
			background-color: skyblue;
			padding: 10px 20px 20px 10px;
		}
	</style>
</head>
<body>
	<div class="box">
		
	</div>
</body>
</html>
```

###border
```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style>
		div{
			background-color: deeppink;
			padding: 12.5px;
			border: 10px double skyblue;
			border-radius: 50%;
			margin: auto;
			position: absolute;
			left: 50%;
			top: 50%;
			transform: translate(-50% -50%);
			-webkit-transform: translate(-50%, -50%);   
            -moz-transform: translate(-50%, -50%);   
            -ms-transform: translate(-50%, -50%);   
            -o-transform: translate(-50%, -50%); 
			/*border-style: solid dashed dotted double;  */
		}
		.box{
			width: 300px;
			height: 300px;
		}
		.box1{
			width: 250px;
			height: 250px;
		}
		.box2{
			width: 200px;
			height: 200px;
		}
		.box3{
			width: 150px;
			height: 150px;
		}
		.box4{
			width: 100px;
			height: 100px;
		}
		.box5{
			width: 50px;
			height: 50px;
		}

	</style>
</head>
<body>
	<div class="box">
		<div class="box1">
			<div class="box2">
				<div class="box3">
					<div class="box4">
						<div class="box5">
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</body>
</html>
```

###margin
```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style>
		/*清楚默认样式*/
		*{
			margin: 0;
			padding: 0;
		}
		a{
			text-decoration: none;
		}
		ul{
			list-style: none;
		}
		.box{
			width: 300px;
			height: 300px;
			background-color: deeppink;
			margin: 20px;
			display: inline-block;
			/*margin-bottom: 20px;
			margin-top: 30px;
			margin-left: 30px;
			margin-right: 50px;*/
			/*简写写法  和padding 一样*/
			/*margin: 30px 50px 20px 30px;*/
			/*margin: 10px 20px 30px;*/
			/*margin: 10px 30px;*/
		}
		.box1{
			width: 200px;
			height: 200px;
			background-color: skyblue;
			display: inline-block;
		}
		.box2{
			width: 400px;
			height: 400px;
			background-color: red;
			margin: 20px auto
		}

	</style>

</head>
<body>
	<div class="box">
		
	</div>
	<div class="box1">
		
	</div>
	<div class="box2">
		
	</div>
</body>
</html>
```

###margin问题
1. 垂直方向上margin会出现重叠现象,谁大谁生效
2. 对里面盒子设置margin-top作用在了外部盒子上
3. 嵌套崩塌解决办法:
	1. 给父类增加overflow:hidden
	2. 给父类盒子加一个极小的padding

###显示和隐藏
1. display: none; 隐藏了,不占据位置
2. visibility: hidden; 隐藏了,依然占据位置

