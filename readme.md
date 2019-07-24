# 新的征程
## web前端介绍
### web前端开发做什么
> pc端web开发；移动端web开发；混合app开发；网页游戏/移动端网页游戏开发；网页特效开发；后台开发(node.js)；微信小程序开发等 。
### 我们学什么
> 参照excel

## 软件架构
### c/s client-server 
+ 比如 qq /360 / LoL / war3 / 吃鸡
+ 数据交互采用特有协议 
+ 在每台主机上安装
+ 更新/迁移 麻烦
+ 安全性 
+ 客户端硬件要求
+ 服务端压力相对较小

### b/s broswer-server
+ 比如: qq空间 / 网站后台 / 缴费系统 / 淘宝
+ 数据交换http协议;https协议相对安全
+ 只需要通过浏览器访问特定的(域名/ip),输入登陆账号密码即可使用
+ 更新 主需要服务器更新,客户端浏览器即可使用
+ 服务端压力稍微大一点. 一般复杂的计算会通过缓存或者负载均衡等形式缓解服务器压力.客户端只负责渲染.
+ 浏览器权限有限,cpu的资源调配 和 显卡的计算能力 

## 电脑基本环境配置
+ 常用软件安装
	- ie浏览器 ie8(特殊,存在兼容问题)和ie10等更高级浏览器
	- chrome浏览器,谷歌.当下最好的浏览器. 速度快,方便调试,集成了手机模拟器.
	- firefox 火狐. 后端程序猿的最爱. 方便调试,但是没有手机模拟器.
	- 360浏览器,双核. "极速"(chrome内核)/"兼容"(ie内核)
	
+ 电脑隐藏文件/ 隐藏后缀名
	- 隐藏文件
	- 隐藏后缀名

+ 输入法
	- 关闭输入法的快捷键
	- 中文使用英文标点

# 前端基础
## HTML 
> HTML超文本标记语言。


### html的结构
> html由三部分组成。分为结构、表现、行为。 html页面采用纯文本形式编写，通过html中的不同标签来区分不同的部分和功能。所见即所得！

+ 结构： html的标签构成了整个网页的结构，比如哪里是标题、哪里是段落，哪里是图片。
	- 标签都是成对出现的，比如： <标签></标签>
	- 标签内部可以包含属性，都是以key="value"的形式出现，比如： <标签 属性名="属性名">  标签的内容 </标签>
	- 文档声明： <!doctype html>,用于声明告诉浏览器，当前页面采用html5的标准来写。
	- 页面的基本结构
	```html
		<!doctype html>

		<html>
			<head>
				<title>不凡学院</title>
			</head>
			<body>
				欢迎来到不凡学院！
			</body>

		</html>
	```
+ 表现： 通过css来控制页面的样式。比如字体大小、背景颜色、字体颜色等。。
+ 行为： 通过javascript（简称js） 来控制页面的行为。指的页面和用户的交互行为。

### 常用标签
+ `<html>` 页面的跟标签，一个页面只能有一个跟标签。 其余所有的内容 都应该写在html标签内部。
+ `<head>` 这里的内容不会再浏览器中直接显示，该标签用于辅助浏览器解析页面。
	- `<meta>` 用于设置网页的元数据，比如使用的字符集编码等  `<meta charset="utf-8">`
	- 用于设置关键字 ```<meta name="keywords" content="xxx" />```
	- 用于设置描述信息 ```<meta name="description" content="xxxx" />```
	
+ `<title>`用于设置页面显示的标题，再浏览器的选项卡头部显示，可能对seo有帮助
```html
	<!DOCTYPE html>
	<html lang="en">
	<head>
		<!-- 字符集编码 meta标签是给浏览器识别的 告诉浏览器使用utf-8形式解析当前页面 -->
		<meta charset="UTF-8">
		<!-- seo 搜索引擎优化 -->
		<!-- 百度搜索引擎抓取的关键词 -->
		<meta name="keywords" content="不凡学院,郑州UI培训,河南郑州UI设计培训,河南郑州前端开发培训,郑州H5培训,郑州WEB前端培训,郑州HTML5前端培训,郑州软件培训">
		<!-- 百度搜索结果展示的内容 -->
		<meta name="description" content="河南郑州不凡学院开设UI设计培训课程和web前端开发课程。北京一线讲师现场教学，学习就等于工作。做自己擅长的事，分享知识与快乐！">
		<title>常用标签</title>
	</head>

```
+ `<body>`
	- 用于设置网页的主题，网页中所展示的所有内容 都在body中。
	- 注意： body中的多个换行和多个空格都会被当做一个空格来处理。 

+ `<h1>~<h6>` 标题标签。在html中一共有6级标题。 h1 是最大的标题，一般在页面中只能出现一次。其他的无所谓。
+ `<p>` 段落标签
+ `<br/>` 换行标签
+ `<hr/>` 水平线换行标签
+ `<iframe>`  内联框架标签，画中画
	- src 内容的链接 比如 src="http://www.baidu.com"
	- widht/height  iframe的宽和高
	- frameborder = 0  去掉默认边框
+ `<a>`  超链接，可以跳转到其他页面
	- href 跳转的地址
	- target: _self 默认 当前页面跳转
	- target: _blank 新的窗口打开
	- target: _parent / _top 配合内联框架使用。再父类窗口/顶级父类窗口跳转页面.
```html
	<!DOCTYPE html>
	<html lang="en">
	<head>
		<meta charset="UTF-8">
		<title>Document</title>
	</head>
	<body>
		<iframe src="http://www.baidu.com" width="500px" height="400px" frameborder=0 ></iframe>
		
		<hr>

		<a href="http://www.baidu.com" target="_self">百度</a>
		<a href="http://www.baidu.com" target="_parent">父亲窗口打开百度</a>
		<a href="http://www.baidu.com" target="_top">顶层父类窗口打开百度</a>
	</body>
	</html>

```
### 图片及路径
+ `<img/>`	
	- src 图片资源的路径
	- alt 如果图片资源不存在，则显示alt的内容。不是必须的。
	- 图片的格式： jpeg / png /gif(动图） /webp(google) ，使用的时候尽量使用大小合适的图片
+ 相对路径，基于当前的文件
	- 如果是同一级文件，直接引用 
	- 如果是同级文件夹的下一级文件，则直接访问同级文件夹再访问下一级，例如： img/bf.png
	- 上一级文件，使用../   
	- 多层上一级可以使用../../ 指上一级的上一级
+ 绝对路径
	- 本地路径： 比如：D:\不凡学院\html基础\课件\dev\avatar.jpg
	- 网络资源： 比如： https://ss0.baidu.com/6ONWsjip0QIZ8tyhnq/it/u=2404337643,717943884&fm=58
+ 一般采用相对路径。
```html
	<!DOCTYPE html>
	<html lang="en">
	<head>
		<meta charset="UTF-8">
		<title>Document</title>
	</head>
	<body>
		<!-- 相对路径 -->
		<img src="avatar.jpg" alt="对不起，图片找不到！">
		<hr>
		<img src="img/bf.png">
		<hr>
		<!-- 本地绝对路径 -->
		<img src="D:\不凡学院\html基础\课件\dev\avatar.jpg" alt="">
		<!-- 网络绝对路径 -->
		<hr>
		<img src="https://ss0.baidu.com/6ONWsjip0QIZ8tyhnq/it/u=2404337643,717943884&fm=58" alt="">
	</body>
	</html>

```

### html基本规范(xhml语法规范)
+ html不区分大小写,但是尽量使用小写
+ html的注释不能嵌套(注释是给代码加说明,不能再页面中显示)  语法: <!-- 注释内容部分 -->
+ html的标签必须完整.  比如: <p>  </p>  <p>  <p> </p>,明细不是成对的,及时浏览器能解析,但是是错误的! 
+ html标签是可以嵌套的.
+ 标签的属性必须加双引号.

### 字体标签
+ `<em>` 斜体.少用.
+ `<strong>`  加粗,表示强调.
+ `<i>`  `<b>`  单纯的表示斜体和加粗,没用语义化.
+ `<sup>` 下标 比如: 5<sup>2</sup>
+ `<sub>` 上标 比如: H<sub>2</sub>O
```html
	<em>我是谁!</em>
	<strong>who am I ?</strong>
	<i>我是谁!</i>
	<b>who am I ?</b>
	5<sup>2</sup>
	H<sub>2</sub>O

```

### 列表
+ 无序列表 ul li
	- 一般使用无序列表.
	- 前面的小黑点或者1,2,3都需要去掉,自己实现样式,方便控制.
	- list-style:none
	- 列表可以相互嵌套
+ 有序列表  ol  li
+ 自定义列表   dl  dt  dd
```html
	<ul>
		<li>箱包</li>
		<li>数码</li>
		<li>咨询
			<ul>
				<li>法律咨询</li>
				<li>数学咨询</li>
			</ul>
		</li>
	</ul>
	<ol>
		<li>起床</li>
		<li>洗脸</li>
		<li>吃饭</li>
	</ol>
	<dl>
		<dt>html基础</dt>
			<dd>基本标签</dd>
			<dd>属性</dd>
		<dt>css基础</dt>
			<dd>css语法</dd>
			<dd>css引入方式</dd>
	</dl>

```
### 表单
+ `<form>` 用于包括输入框,提交数据
	- action 提交的地址,暂时不用理解
	- method 提交数据的方法 get/post,如果不写,默认是get方式.
+ `<input>` 表单输入框,根据tpye的类型,表现不同的形式
	- type: text  必须 单行文本输入框
	- name: 当前表单的名称  目前必须要有,因为提交的时候后台程序需要通过name属性获取表单的内容.
	- value: xx  当前表单的内容.value是提交的结果.如果设置了vlaue,则是当前表单的默认值.
+ `<input>`: type:password  密码输入框
+ `<input>`: type:radio  单选
	- name 必须要有,这里表明当前的单选输入框为一组
	- value 必须要有,因为单选按钮提交的结果是value的值. value一般采用数字编码的形式表示.
	- checked  默认选中
+ `<input>`: type:checkbox  多选
	- name 同radio
	- value 同radio
	- checked  默认选中
+ `<select>`  option  下拉框
	- name 属性需要设置
	- value 每个option都要设置value
	- selected 默认选中
+ `<input>`: type:file  上传
	- 当选中的时候 ,实际文件并没有被上传上来
	- multiple 可以实现多选
+ `<textarea>` 多行文本输入框
	- cols /rows  文本框的宽度和高度
	- name值需要设置,value指的是标签内部的内容
+ `<input>` type:submit 提交按钮
	- value 按钮显示的内容
	- 点击后表单被提交到 form.action 配置的地址
+ `<label>` 用于包括输入框的头部和输入框 使之称为一体。多用于单选和多选。
+ readonly 只读属性，输入框内容不能更改。
+ disabled 禁用  表单的值再提交时会被舍弃。
+ `<fieldset>` `<legend>` 可以实现表单的分组。
+ get提交
	- 参数被放到地址提交,比如: /D:/abc?username=张三&pwd=123&sex=0&experience=0
	- 不安全
	- 地址栏拼接的参数长度有限,一般是<4k
	- 一般用于获取数据
+ post提交
	- 地址栏不显示提交内容,再请求体显示
	- 相对安全
	- 提交的数据量没有上限
	- 一般用于提交保存数据
```html
	<!-- action 是当前表单提交的地址 -->
	<form action="www.bufanui.com" method="get">
		<fieldset>
			<legend>基本信息</legend>
			用户名: <input type="text" readonly  name="username" value="张三"> <br>
			曾用名： <input type="text" disabled  name="oldname" value="张小三"><br>
			密码: <input type="password" name="pwd"> <br>	
			性别: 
				<label>
					男: <input type="radio" name="sex"  value="0"> 
				</label>
				<label>
					女: <input type="radio" checked  name="sex"  value="1"> <br>
				</label>
		</fieldset>
		
		<fieldset>
			<legend>补充信息</legend>
			爱好: 
			<label>
				篮球: <input type="checkbox" name="like" value="basketball">
			</label>
			<label>
				足球: <input type="checkbox" checked name="like" value="football">
			</label>
			<label>
				乒乓: <input type="checkbox" name="like" value="pingpang"><br>
			</label>

	    工作年龄: 
	    	<select name="experience">
	    		<option value="0">--无--</option>
	    		<option value="1">1年</option>
	    		<option value="2" selected>2~3年</option>
	    		<option value="3">3~5年</option>
	    	</select> <br>
    	上传头像: <input type="file" name="avatar" multiple> <br>
    	个人描述: <textarea name="desc" cols="30" rows="4">
    				我对工作有极大地热情,我喜欢写代码!
    				我大学时候是一个德智体美劳全面发展的废柴!
    			</textarea> <br>
		</fieldset>
				
		
    	<input type="submit" value="提交">
	</form>
```

### 转义字符
+ 空格	`&nbsp;`	`&#160;`
+ <	小于号	`&lt;`	`&#60;`
+ >	大于号	`&gt;`	`&#62;`
```html
	<p>这是一个 &lt;p&gt;标签</p>
	<p>张&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;三</p>
```
### table 数据表格
+ `<table>` 
	- align（表格的位置） : left| center | right
	- border: 1   边框，同时为td生成边框
	- cellspacing: 10  单元格之间的间距
	- cellpadding: 30  文字和单元格之间的间距
	- bgcolor:    设置表格的背景色
+ `<tr>`
	- bgcolor: 设置当前行的背景色
	- align: left | center | right  文字对齐方式
+ `<th>`
+ `<td>`
	- colspan  表格所占据的列
	- rowspan  表格所占的行
```html
	<!-- 复杂表单 -->
	<table border="1" cellspacing="10" cellpadding="10">
		<tr>
			<th>时间</th>
			<th>周一</th>
			<th>周二</th>
			<th>周三</th>
			<th>周四</th>
			<th>周五</th>
		</tr>
		<tr>
			<td rowspan="2">上午</td>
			<td>语文</td>
			<td colspan="2">数学</td>
			<td>语文</td>
			<td>语文</td>
		</tr>
		<tr>
			<td>思想品德</td>
			<td>思想品德</td>
			<td>思想品德</td>
			<td>思想品德</td>
			<td>思想品德</td>
		</tr>
		<tr>
			<td rowspan="2">下午</td>
			<td>体育</td>
			<td>体育</td>
			<td>体育</td>
			<td>体育</td>
			<td>体育</td>
		</tr>
		<tr>
			<td>自然</td>
			<td>自然</td>
			<td>自然</td>
			<td>自然</td>
			<td>自然</td>
		</tr>

	</table>

```
## css
> css全称层叠样式表 (Cascading Style Sheets),用于实现页面的样式。

### 书写位置
+ 行内样式  ``` <p style="color: red">我是一个p标签</p>  ```
+ 内部样式  ``` <style>  p{color:blue;} </style>```
+ 引入样式  ```<link rel="stylesheet" href="style.css">```
+ 区别：
	- 行内样式 严重耦合 用的非常少！
	- 内部样式 测试使用，但是当前页面的样式只能再当前页面使用。
	- 引入样式 上线时候使用。 可以再多个页面复用外部样式。
### css选择器
+ 标签选择器
+ class选择器
+ id选择器
	```css
		/*标签选择器*/
		h1{
			color: red;
		}
		/*class选择器*/
		.h2{
			color: blue;
		}
		/*id选择器*/
		#h3{
			color: orange;
		}
	
	```
+ 交集选择器
+ 并集选择器
+ 后代选择器
+ *通配符
```css
		/*标签p 和.p1的交集*/
		p.p1{
			color: red;
		}
		.p2.danger{
			color: blue;
		}
		/*并集选择器 都被选中*/
		.p1,.p2{
			font-size: 30px;
		}
		/*后代选择器 空格*/
		.p3 a{
			color: red;
		}
		/** 通配符 选择所有标签*/
		*{
			/*background-color: pink;*/
		}

```

### css的单位
+ px 像素单位
+ em 基于当前字体的倍数： text-indent: 2em;
+ 颜色
	- 预定义颜色： blue  yellow  pink  purple  red  等
	- 十六进制： 每两位表示一种颜色的深度  分别表示 red  green  blue; 比如： #ff00ff
``` shell
			十六进制==> 十进制换算
			十进制：  	0  1  2  3  4  5  6  7  8  9   
			十六进制：  0  1  2  3  4  5  6  7  8  9   a(10)  b(11)   c(12)  d(13)   e(14)   f(15)
			比如： 1e  ==>  1*16 + e ==> 16+ 14 = 30;
				ff ==> f * 16 + f ==> 15*16 + 15 = 255;	
			比如一个颜色是 aabbcc ==> abc, #00ffaa ==> #0fa
```
	- rgb:   rgb(0,0,255) ==> 绿色 ； rgb和十六进制是可以互换的。
	- rgba:  rgba(0,0,255,0.5) ==> 跟rgb一样，a是透明度：0~1； 0.5==> .5
	
### 常用属性
| 属性名称 | 属性作用 | 值 |
| ------ | ------ | ------ |
| width / height  | 宽高(块状单位有效) | px 百分比 em等 |
| background-color | 背景颜色 | color |
| cololr | 字体颜色 | color |
| font-size | 字体大小 | px  em等 |
| text-align | 文字对齐方式 | center left right  
| text-index | 首行缩进 | px  em等 |
| font-family | 字体 | 微软雅黑	Microsoft YaHei、黑体 SimHei、Arial等 |
| font-weight | 字体加粗 | 100-900.加粗700-900/ bolder lighter normal |
| font-style | 字体样式 | Italic 斜体 / normal 正常 |
| line-height | 行高 | 单位： px  /倍数 /  百分比 ;- 设置文字的行间距- 单行文字垂直居中 ：行高=父类盒子高度  |
| font | 字体缩写 | `font:italic bolder 20px/1.2 'Arial','Microsoft YaHei'   |


### 背景图片
| 属性名称 | 属性作用 | 值 |
| ------ | ------ | ------ |
| background-color  | 背景图片颜色 | color |
| background-image  | 背景图片 | url(‘1.png’);  |
| background-repeat  | 平铺方式 | repeat 、 no-repeat  、 repeat-x 、 repeat-y  |
| background-position  | 图片位置 | left、 right、 top、 bottom、 center |
| background-attachment  | 背景滚动 | scroll、fixed (注意：基于body的定位） |
| background  | 简写（顺序不能错） | background: green url(1.jpg) no-repeat center center fixed; |

```html
	<!DOCTYPE html>
	<html lang="en">
	<head>
		<meta charset="UTF-8">
		<title>Document</title>
		<style>
			body{
				background-image: url('img/banner.jpg');
				background-repeat: no-repeat;
				background-position: left top;
				/*是否跟最滚动*/
				background-attachment: fixed;
			}
			.d1{
				width: 100%;
				height:400px;
				/*background-color: green;*/
				/*background-image: url('img/bf.png');*/
				/*background-repeat: no-repeat;*/
				/*center 默认的是x轴  y轴默认居中*/
				/*跟数学的坐标系是不同的，x轴为正 ，y轴向下正 */
				/*background-position: -35px 30%;*/
				background: green  url('img/bf.png') no-repeat right 200px fixed;
				/*如果设置了fixed 那么背景图片的位置将会基于body*/
				/*background-attachment:fixed;*/
				/*精灵图片 雪碧图 做案例的时候再补充*/
				background-color: purple;
			}
			.d2{
				widows: 100%;
				height: 1000px;
				background-color: pink;
				/*透明度 ： 0~1  */
				opacity: .5;
			}
		</style>
	</head>
	<body>
		<!-- div 是一个标签，不表示任何的内容，没有自带样式。只是用于划分结构 -->
		<div class="d1">
			
		</div>
		<div class="d2">
			
		</div>
	</body>
	</html>

```

### 标签的表现形式
+ 块状标签  独占一行，宽高有效。 比如： div   p  h1~h6  form  table   hr  br  ul>li   ol>li dl>dt/dd 
+ 行内块标签  可以同一行显示，宽高有效。  比如: input select  img   button 
+ 行内标签  可以同一行显示，但是宽高无效， margin-top/margin-bottom 无效。。  比如： a   span   strong  del ins  em  i  b  等字体标签

### 盒子模型
> CSS处理网页时，它认为每个元素都包含在一个不可见的盒子里。包含内容区域、 padding（内边距） 、 border（边框）、margin（盒子与盒子的距离）

+ padding
	- padding:10px 20px 30px 40px 这样会设置元素的上、右、下、左四个方向的内边距。
	- padding:10px 20px 30px; 分别指定上、左右、下四个方向的内边距
	- padding:10px 20px; 分别指定上下、左右四个方向的内边距
	- padding:10px;同时指定上左右下四个方向的内边距
	- 同时在css中还提供了padding-top、padding-left、padding-right、padding-bottom分别用来指定四个方向的内边距。
```html
	<style>
		.d1{
			width: 300px;
			height: 300px;
			background-color: green;
			/*padding: 50px  100px 30px 80px;
			padding-left: 100px;*/
			padding: 100px;
		}
	</style>
```

+ margin
	- 用法和padding类似，同样也提供了四个方向的margin-top/right/bottom/left。
	- margin: xxx auto;可以使元素居中。
	- 嵌套崩塌：两个盒子发生嵌套的时候，给子类设置maring会给父类造成一种崩塌现象，子类的margin-top没有效果，而直接作用到父类。
	- 解决方案：  1. 父类  overflow: hidden ; 2. 父类 设置极小的padding
	- 重叠： 如果垂直两个块状元素同时设置了margin-bottom和margin-top,那么这两个值将会发生重叠,不会累加，哪个值大用哪个。
	- margin-top/margin-bottom 对于行内元素无效。
```html
	.d2{
		width:200px;
		height:200px;
		background-color: red;
		/*margin: 100px;
		margin-top: 200px;*/
		/*d2将会左右居中*/
		margin: 100px auto;
	}
	<!-- ======================= -->
	<!-- 当两个盒子发生嵌套的时候，给子类设置maring会给父类造成一种崩塌现象，子类的margin-top没有效果，而直接作用到父类 -->
	<!-- 解决方案： 1. 父类  overflow: hidden
			   2. 父类 设置极小的padding -->
	<div class="box">
		<div class="inner-box">
			
		</div>
	</div>

	<hr>
	
	<!-- 如果垂直两个块状元素同时设置了margin-bottom和margin-top,那么这两个值将会发生重叠,不会累加，哪个值大用哪个 -->
	<div class="box2">
		
	</div>
	<div class="box3">
		
	</div>	
```
+ border
	- 可以在元素周围创建边框，边框是元素可见框的最外部。
	- border:1px solid red 分别指定了边框的宽度、颜色和样式,是一种缩写： border-widht:  border-style border-color
	- border-style: none (默认)  /  dashed(虚线) / dotted（点）  / solid(实线)  /  double(双实线)
	- 可以单独设置某一条边框： border-right: 20px solid blue;
```html

	.d1{
		width: 200px;
		height:200px;
		background-color: green;
		/*简写属性*/
		/*border: 10px solid red;*/
		border-width: 10px;
		border-style: solid;
		border-color: red;
		/*右边单独添加20像素*/
		border-right: 20px solid blue;
	}

```


+ 影响盒子大小的因素
	- border
	- padding  特殊：继承的盒子在父盒子宽度范围内，padding值不会影响该盒子大小。
	
+ display 我们可以通过修改display来修改元素的性质。
	– block：设置元素为块元素
	– inline：设置元素为行内元素
	– inline-block：设置元素为行内块元素
	– none：隐藏元素
	- 转换的必要性：比如可以把a标签转换为块状元素，进而实现一个按钮的样式。
+ visibility 和display不同，使用visibility隐藏一个元素，隐藏后其在文档中所占的位置会依然保持，不会被其他元素覆盖。
```html
	.baidu{
			/*display 可以改变元素的表现形式*/
			display: inline-block;
			width:300px;
			height:300px;
			background-color: pink;
		}
	.p1{
			/*display:none;*/
			visibility:hidden;
		}

```
+ overflow 相关标签里面的内容超出了样式的宽度和高度时如何处理
	– visible：默认值
	– scroll：添加滚动条
	– auto：根据需要添加滚动条
	– hidden：隐藏超出盒子的内容
```html
	.d1{
			width: 200px;
			height: 200px;
			background-color: green;
			overflow: auto;
			/*overflow: scroll;
			overflow: hidden;*/
		}

```
	
### 文档流
+ 块状标签独占一行
+ 行内元素可以同一行显示，如果不够会自动换行
+ 自上而下的展示

### 浮动
> 浮动指的是使元素脱离原来的文本流，在父元素中浮动起来。

+ 块级元素和行内元素都可以浮动，当一个行内元素浮动以后将会自动变为一个块级元素.
+ 当一个块级元素浮动以后，宽度会默认被内容撑开，所以当漂浮一个块级元素时我们都会为其指定一个宽度。
当一个元素浮动以后，其下方的元素会上移。元素中的内容将会围绕在元素的周围。
+ 浮动会使元素完全脱离文本流，也就是不再在文档中在占用位置。
+ 元素设置浮动以后，会一直向上漂浮直到遇到父元素的边界或者其他浮动元素。
+ 元素浮动以后即完全脱离文档流，这时不会再影响父元素的高度。也就是浮动元素不会撑开父元素。
+ 浮动元素默认会变为块元素，即使设置display:inline以后其依然是个块元素。

### 浮动的影响
+ 如果子类元素设置了浮动，而父类元素没有设置高度，或者高度比子类元素小，那么子类元素脱离了文档流，就无法把父类盒子撑开。那么整个文档的结构将受到破快。
+ 清除浮动的影响： clear: left/right/both  不允许当前元素的left/right/both有浮动元素。
	- 在浮动元素的最后面追加一个空的div,设置clear:both即可清除浮动的影响。
+ 因为浮动会对文档流造成影响，所以能用流式布局 就不要使用浮动。
+ 补充：1.display：inline-block 标签的换行符会被显示为空格  2.float:right  会改变标签的前后顺序。
```html
	<!DOCTYPE html>
	<html lang="en">
	<head>
		<meta charset="UTF-8">
		<title>Document</title>
		<style>
			*{
				margin: 0;
				padding: 0;
			}
			.header{
				width: 100%;
				height: 100px;
				background-color: green;
			}
			.content{
				width: 100%;
				/*height: 500px;*/
				background-color: pink;
			}
			/*同级要浮动，都浮动*/
			.content .aside{
				float:left;
				width: 200px;
				height: 300px;
				background-color:red;
			}
			.content .main{
				float:left;
				width: 800px;
				height:900px;
				background-color: gray;
			}
			.footer{
				width: 100%;
				height: 100px;
				background-color: black;
			}
			/*不允许当前元素左右出现浮动元素  这样可以清除浮动的影响*/
			.clr{
				clear: both;
			}
		</style>
	</head>
	<body>
		<div class="header">
			
		</div>
		<div class="content">
			<div class="aside">
				
			</div>
			<div class="main">
				
			</div>
			<div class="clr"></div>
		</div>
		<div class="footer">
			
		</div>
	</body>
	</html>
```

### 定位
> 通过postion属性可以实现元素的定位。元素定位之后，需要通过设置left和top值对元素定位。

+ static 默认
+ relative 相对定位。 相对元素本身的位置定位。
	- 当开启了相对定位以后，可以使用top、right、bottom、left四个属性对元素进行定位。
	- 如果不设置元素的偏移量，元素位置不会发生改变。
	- 相对定位不会使元素脱离文本流。元素在文本流中的位置不会改变。
	- 相对定位不会改变元素原来的特性。
	- 相对定位会使元素的层级提升，使元素可以覆盖文本流中的元素。

```html
	.d1{
		position: relative;
		left: 100px;
		top: 100px;
		width: 200px;
		height: 200px;
		background-color: green;
	}

```

+ absolute 绝对定位指使元素相对于html元素或离他最近的祖先定位元素进行定位。
	- 当开启了绝对定位以后，可以使用top、right、bottom、left四个属性对元素进行定位。
	- 绝对定位会使元素完全脱离文本流。
	- 绝对定位的块元素的宽度会被其内容撑开。
	- 绝对定位会使行内元素变成块元素。
	- 一般使用绝对定位时会同时为其父元素指定一个相对定位，以确保元素可以相对于父元素进行定位。
```html
	.d1{
		/*有绝对的事情吗？绝对的值必须有参照物*/
		/*如何才能既保证父类有定位元素 而且父类不会再原来的位置偏移*/
		/*子绝父相*/
		position: relative;
		left: 0;
		top: 0;
	/*	left: 100px;
		top: 100px;*/
		margin-left: 100px;
		width:400px;
		height:400px;
		background-color: green;
	}
	.d11{
		position: absolute;
		left: 100px;
		top: 100px;
		width:150px;
		height: 150px;
		background-color: red;
	}

	<div class="d1">
		<div class="d11">
			
		</div>
	</div>

```
+ fixed 固定定位。元素会被锁定在屏幕的某个位置上，当访问者滚动网页时，固定元素会在屏幕上保持不动。
	- 固定定位不占据原来的位置，会脱标。
	- 给元素设置固定定位之后，元素位置从浏览器左上角出发。
	- 可以将行内元素转换为行内块元素。
```html
	.zx{
			position: fixed;
			right: 100px;
			bottom: 200px;
			width: 200px;
			height: 200px;
			background-color: red;
		}

	<a class="zx" href="#">
		w shi a
	</a>

```
+ z-index 当元素开启定位以后就可以设置z-index这个属性。默认是0.值越大，越靠上。
	- z-index可以指定一个整数作为参数，值越大元素显示的优先级越高，也就是z-index值较大的元素会显示在网页的最上层。
```html
	.d1,.d2,.d3{
		position: fixed;
		left: 0;
		top:0px;
		width: 200px;
		height: 200px;
		background-color: green;
	}
	.d1{
		z-index: 9;
	}
	.d2{
		left:30px;
		top: 30px;
		background-color: blue;
		z-index:2;
	}
	.d3{
		left: 80px;
		top: 80px;
		background-color: red;
		z-index: 0;
	}


	<div class="d1">
		d1
	</div>
	<div class="d2">
		d2
	</div>
	<div class="d3">
		d3
	</div>

```

### 规避脱标流 
>经验： 一般布局采用标准流，如果布局实现不了用浮动。定位一般用于解决小范围的某个标签的位置。

+ 能用标准流（没有脱标）解决就不用浮动
+ 解决不了就考虑有浮动（页面布局类型，“不完全脱标”）
+ 浮动解决不了用定位（小图标，完全脱标，不影响内容）

### 结束
> html和css基础内容基本概况完毕，当然只掌握这些内容是不够的。

		





