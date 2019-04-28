###html结构
```html
	<!DOCTYPE html>
	<!-- 声明文档类型的,告诉浏览器以html5的标准去解析页面,快捷键:!+Tap -->
	<!-- 添加注释的方式Ctrl+/ -->
	<!-- 注释用来解释代码,方便你项目的维护 -->
	<html lang="en">
	<!-- html中大多数标签大多都是成对出现的 -->
	<!-- 标签中的形式:<开始标签 (开始标签的属性)>标签内的内容(也可以是其他标签,文本)</结束标签> -->
	<!-- 标签属性:标签的附加信息 -->
	<!-- lang="en"英文环境 -->
	<head>
		<!-- 辅助浏览器解析页面,这里面的部分不会出现在浏览器当中 -->
		<meta charset="UTF-8">
		<!-- charset="UTF-8"字符集编码(优化后的全球码) -->
		<!-- meta包含了网站中的元信息 -->
		<meta name="description" content="保存网站的描述信息,搜索结果的内容">
		<meta name="keywords" content="网站的关键词,搜索引擎搜索后的结果内容的标题">
		<!-- seo优化,搜索引擎优化 -->
		<title>Document</title>
		<!-- 展示在tab栏中的网站的标题 -->
	</head>
	<body>
		<!-- 网站中的主体,这里面的内容会显示在浏览器当中 -->
		Hello world!
	</body>
	</html>
```

###常见标签

1. 标题标签

	`<h1>`--`<h6>`

2. 段落标签
```html
	<p>唐诗选集<br>经典</p>
	<h2>静夜思</h2>
	<h3>李白</h3>
	<p>床前明月光,</p>
	<p>疑是地上霜.</p>
	<p>举头望明月,</p>
	<p>低头思故乡.</p>
```
3. 图片标签
```html
<img src="" alt="">
<!-- 属性与属性之间空格隔开
src属性:图片的地址
alt属性:图片找不到时显示图片里的内容 -->
<img src="C:/Users/Administrator/Desktop/工具/新建文件夹 (2)/a.jpg" alt="本地绝对路径-公路">
<img src="https://zhengxin-pub.bj.bcebos.com/logopic/f92eaa82260a2dbb710fa82d56a7cb42_fullsize.jpg@s_1,w_484,h_484" alt="网络绝对路径-小米">
<img src="bf.png" alt="相对路径-当前同一目录">
<img src="../avatar.jpg" alt="相对路径-上一级目录">
<img src="img/b.png" alt="相对路径-下一级目录">
```
4. 超链接标签
```html
<a href="https://www.mi.com/" target="_blank">小米商城</a>
<!-- 新窗口打开页面 -->
<!-- target属性: -->
<!-- _blank新窗口打开 -->
<!-- _self当前窗口打开(默认) -->
<!-- 实现图片的跳转 -->
<a href="https://www.mi.com/" target="_self">
	<img src="https://zhengxin-pub.bj.bcebos.com/logopic/f92eaa82260a2dbb710fa82d56a7cb42_fullsize.jpg@s_1,w_484,h_484" alt="">
</a>
```
5. 分割线

	`<hr>`

6. 字体标签
```html
<em>斜体:表示一段内容中的着重点</em>
<strong>加粗:表示一个内容的重要性</strong>
<br>
没有语义化:
<i>斜体</i><b>加粗</b>
上标:5<sup>2</sup>
下标:h<sub>2</sub>o
<ins>这一段文字有下划线</ins>
<del>这一段有删除线</del>
<!-- 5转义字符
空格 &nbsp; &#160;
小于号 &lt; &#60;
大于号 &gt; &#62; -->
<p></p>
&lt;p&gt;&lt;/p&gt;
<!-- 还有很多 -->
```
7. 列表标签

+ 有序列表
```html
<ol>
	<li>手机</li>
	<li>数码</li>
	<li>摄影</li>
</ol>
```
+ 无序列表

```html
<ul>
	<li>猫</li>
	<li>狗</li>
	<li>羊</li>
</ul>
```
+ 自定义列表
```html
		<dl>
			<dt>第一章</dt>
				<dd>大闹天宫</dd>
			<dt>第二章</dt>
				<dd>桃园三结义</dd>
			<dt>第三章</dt>
				<dd>赤壁之战</dd>
		</dl>
```

### 表格
```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
</head>
<body>
	<table border="1" align="center" cellspacing="5" cellpadding="5" bgcolor="blue">
		<caption>课程表</caption>
		<!-- tr行 -->
		<tr bgcolor="red">
			<!-- th表头 -->
			<th>周一</th>
			<th>周二</th>
			<th>周三</th>
		</tr>
		<tr align="center">
			<!-- td单元格 -->
			<td rowspan="4">语文</td>
			<td colspan="2">数学</td>
		</tr>
		<tr>
			<td>数学</td>
			<td>英语</td>
		</tr>
		<tr>
			<td>数学</td>
			<td>英语</td>
		</tr>
		<tr>
			<td>数学</td>
			<td>英语</td>
		</tr>
	</table>
</body>
</html>
```
### 表单

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
</head>
<body>
	<form action="提交地址">
		用户名:<input type="text" name="用户名">
		<br>
		密码:<input type="password" name="密码">
	</form>
	<!-- html不区分大小写,但是尽量使用小写
	html的注释不能嵌套(注释是给代码加说明,不能再页面中显示) 
	html的标签必须完整. 
	html标签是可以嵌套的.(嵌套的时候一定要注意缩进)
	标签的属性必须加双引号. -->
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
    			</textarea> <br>
		</fieldset>
				
		
    	<input type="submit" value="提交">
	</form>
</body>
</html>
```