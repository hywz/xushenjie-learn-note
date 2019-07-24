## H5+CSS3-01
### H5新标签
+ section元素 
表示页面中的一个内容区块,比如章节、页眉、页脚或页面的其他部分。可以和h1、 h2……等元素结合起来使用，表示文档结构。例：HTML5中`<section>……</section>`;HTML4中`<div> ……</div>`。
+ article元素 
表示页面中一块与上下文不相关的独立内容。比如一篇文章。
+ aside元素 
表示article元素内容之外的、与article元素内容相关的辅助信息。
HTML`<aside>`元素表示一个页面的一部分， 它的内容跟这个页面的其它内容的关联性不强，或者是没有关联，单独存在。`<aside>`元素通常显示成侧边栏(sidebar)或一些插入补充内容。通常用来在侧边栏显示一些定义，比如目录、索引、术语表等；也可以用来显示相关的广告宣传，作者的介绍，Web应用，相关链接，当前页内容简介等。
+ header元素 
表示页面中一个内容区块或整个页面的标题。
+ hgroup元素 
表示对整个页面或页面中的一个内容区块的标题进行组合。
+ footer元素 
表示整个页面或页面中一个内容区块的脚注。一般来说，他会包含创作者的姓名、创作日期以及创作者的联系信息。
+ nav元素 
表示页面中导航链接的部分。
+ figure元素 
表示一段独立的流内容，一般表示文档主体流内容中的一个独立单元。
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>

<body>
    <header>
        <hgroup></hgroup>
        <nav></nav>
    </header>
    <section></section>
    <aside>

    </aside>
    <footer></footer>
    <input type="text" disabled>
    <button disabled>禁用</button>
    <input type="checkbox" disabled>

    <a href="http://www.baidu.com" target="_parent">hello world</a>
    <iframe src="./2-input新标签.html" frameborder="0"></iframe>
</body>

</html>
```
### 表单元素
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        
        .line {
            margin: 110px auto;
            width: 200px;
            height: 10px;
            background-color: #00FFFF;
        }
        
        .inner {
            width: 2px;
            height: 10px;
            background-color: orangered;
        }
    </style>
</head>

<body>
    <form action="/h5c3/01/html新标签.html">
        邮箱: <input type="email" name="" id=""><br> 
        网址: <input type="url" name="" id=""><br> 
        数字: <input type="number" name="" id=""><br> 
        范围: <input type="range" name="" id=""><br> 
        颜色: <input type="color" name="" id=""><br> 
        日期: <input type="date" name="" id=""><br> 
        时间: <input type="time" name="" id=""><br> 
        手机号码: <input type="tel" name="" id=""> 
        性别: <input type="text" list="data">
         <!-- <datalist> 数据列表  自动补全
	    实际开发中：需要自动补全的内容列表项可能很多，不可能挨个展示在页面中，一般是通过ajax局部页面刷新技术实现的。
        与input 配合使用 -->
        <datalist id="data">
            <option>男</option>
            <option>女</option>
        </datalist>
        <br>
        <!-- <meter>  meter元素用来表示规定范围内的数量值，如磁盘使用量比例饿、关键词匹配程度等。需要注意的是，meter不可以用来标记那些没有已知范围的任意值，如重量、高度，除非已经设定了它们值的范围。表示度量器，不建议用作进度条 -->
        <meter value="81" min="0" max="100" low="60" high="80"></meter><br>
        <progress value="22" max="100"></progress><br>
        <input type="submit" value="提交"><br>
    </form>
    <div class="line">
        <div class="inner"></div>
    </div>
    <script>
        var line = document.querySelector('.line');
        var inner = document.querySelector('.inner');
        var timer = setInterval(function() {
            var start = inner.offsetWidth;
            if (start + 1 === line.offsetWidth) {
                console.log('stop...')
                clearInterval(timer);
            }
            inner.style.width = start + 1 + 'px';
        }, 17)
    </script>

</body>

</html>
```
### 表单属性
+ placeholder 占位符
+ autofocus 获取焦点
+ multiple 文件上传多选或多个邮箱地址 
+ autocomplete 自动完成，用于表单元素，也可用于表单自身(on/off)
+ form 指定表单项属于哪个form，处理复杂表单时会需要 一般一个页面只有一个form
+ novalidate 关闭验证，可用于<form>标签
+ required 必填项
+ pattern 正则表达式 验证表单
 手机号:`<input type="tel" name="tel" required="required"       pattern="^(\+86)?1[3,5,8](\d{9})$">`
+    formaction应用于提交按钮上，如：`<input type="submit" formaction="xxx.action">`
+ 表单事件:
    - oninput 用户输入内容时触发，可用于移动端输入字数统计
    - oninvalid 验证不通过时触发
```html
<form action="abc">
 手机号:   
    <input type="text" name="phone" maxlength="11" pattern="^(0|86|17951)?1[0-9]{10}" 
    oninvalid="setCustomValidity('请输入11位手机号');"/>
    <br>
  <input type="submit">
</form>
```
### frame
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>

<body>
    <iframe src="./2-input新标签.html" frameborder="1" width="500" height="200"></iframe><br>
    <br>
    <iframe src="http://www.baidu.com" frameborder="0" width="500" height="200"></iframe>
</body>

</html>
```
### 全屏显示
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        img {
            width: 200px;
        }
        
        .box:fullscreen img {
            width: 100%;
        }
    </style>
</head>

<body>
    <div class="box">
        <!-- 设置img的全屏样式,让box全屏显示 -->
        <img src="../img/1.jpg" alt="">
    </div>
    <script>
        var box = document.querySelector('.box'),
            img = document.querySelector('img');
        box.onclick = function() {
                if (ifFullscreen()) {
                    //退出全屏必须使用 document的api
                    if (document.exitFullscreen) {
                        document.exitFullscreen()
                    } else if (document.webkitCancelFullScreen) {
                        document.webkitCancelFullScreen();
                    } else if (document.mozCancelFullScreen) {
                        document.mozCancelFullScreen();
                    }
                } else {
                    // 开启全屏 需要作用到元素上面
                    if (box.requestFullscreen) {
                        box.requestFullscreen();
                    } else if (box.webkitRequestFullscreen) {
                        box.webkitRequestFullscreen();
                    } else if (box.mozRequestFullscreen) {
                        box.mozRequestFullscreen();
                    } else {
                        alert("sorry,无法全屏");
                    }
                }
            }
            // 判断是否是全屏
        function ifFullscreen() {
            return document.fullscreen || document.webkitIslFullScreen || document.mozCancelFullScreen || false;
        }
    </script>
</body>

</html>
```
### css hack
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        
        header {
            width: 200px;
            height: 200px;
            background-color: red;
        }
        
        .box {
            width: 200px;
            height: 200px;
            background-color: orange;
        }
    </style>
    <!--[if gte IE 8]>
		<link rel="stylesheet" href="ie8.css">
	<![endif]-->
</head>

<body>
    <!-- 在不支持HTML5新标签的浏览器里，会将这些新的标签解析成行内元素(inline)对待，所以我们只需要将其转换成块元素(block)即可使用，但是在IE9版本以下，并不能正常解析这些新标签，但是却可以识别通过document.createElement('tagName')创建的自定义标签，于是我们的解决方案就是将HTML5的新标签全部通过document.createElement('tagName')来创建一遍，这样IE低版本也能正常解析HTML5新标签了，在实际开发中我们更多采用的是通过检测IE浏览器的版本来加载三方的一个JS库来解决兼容问题。
    lte：就是Less than or equal to的简写，也就是小于或等于的意思。
    lt ：就是Less than的简写，也就是小于的意思。
    gte：就是Greater than or equal to的简写，也就是大于或等于的意思。
    gt ：就是Greater than的简写，也就是大于的意思。
    !： 就是不等于的意思，跟javascript里的不等于判断符相同
    注意：在非IE浏览器中是看不到效果的 -->
    <header>
    </header>
    <div class="box"></div>

</body>

</html>
```
### seo
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <!-- 2017 9月份   百度清风算法:对于网站恶意堆叠关键词 会降级 -->
    <!-- seo优化 -->
    <!-- 网站描述,会在百度的搜索结果中 -->
    <meta name="description" content="河南郑州不凡学院开设UI设计培训课程和web前端开发课程。北京一线讲师现场教学，学习就等于工作。做自己擅长的事，分享知识与快乐！">
    <!-- 关键词: 百度搜索 哪些词 容易被抓取 -->
    <meta name="keywords" content="不凡学院,郑州UI培训,河南郑州UI设计培训,河南郑州前端开发培训,郑州H5培训,郑州WEB前端培训,郑州HTML5前端培训,郑州软件培训">
    <title>[官网] 不凡学院_河南郑州UI设计培训_河南郑州前端开发培训_郑州软件开发</title>
</head>
<style>
    a {
        text-indent: -999999px;
    }
</style>

<body>
    <!-- 1. 关键词很重要  根据经验,title 目前应该比 keywords 权重高
			 2. 注意清风算法
			 	a) 在标题<head>部分不能随意堆叠关键词
			 	b) img不能alt堆叠关键词
			 	c) 可以在页面的内容的适当部分体现关键词
			 	d) logo 一定要写关键词
		 	 3. 注意网站链接(外链 内链)
		 	 4. 优质内容 原创内容 体现关键词
		 	 5. 更新 经常更新
         -->
    <a href="">不凡ui 郑州培训  前端培训 郑州前端</a>
    <img src="./img/avatar.jpg" alt="不凡ui 郑州培训  前端培训 郑州前端" title="">
</body>

</html>
```
### 多媒体
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        .line {
            width: 1000px;
            height: 20px;
            background-color: #00FFFF;
        }
        
        .inner {
            /* width: 2px; */
            height: 20px;
            background-color: orangered;
        }
    </style>
</head>

<body>
    <audio src="./lib/小手拍拍.mp3" controls>不支持</audio><br>
    <video src="./lib/movie.ogg" width="1000" height="600" controls>
        
    </video><br>
    <div class="line">
        <div class="inner"></div>
    </div>
    <br>
    <button class="load">加载动画</button>
    <button class="pause">暂停</button>
    <button class="play">播放</button>
    <button class="fullPage">全屏显示</button>
    <script>
        var vd = document.querySelector('video');
        var load = document.querySelector(".load");
        var play = document.querySelector(".play");
        var pause = document.querySelector(".pause");
        var fullPage = document.querySelector(".fullPage");
        var inner = document.querySelector('.inner');
        var line = document.querySelector('.line');
        load.onclick = function() {
            vd.src = "../../../迅雷下载/生活大爆炸.The.Big.Bang.Theory.S11E01.中英字幕.HDTVrip.720P-人人影视.mp4";
            vd.load(); // 加载视频源
        }
        play.onclick = function() {
            vd.play(); // 播放
        }
        pause.onclick = function() {
            vd.pause(); //暂停
        }
        fullPage.onclick = function() {
                vd.webkitRequestFullScreen();
            }
            // 视频来源解析完毕事件
        vd.oncanplay = function() {
                console.log('解析完毕...')
            }
            // 视频播放时的事件
        vd.ontimeupdate = function() {
                //当前时间
                // console.log(vd.currentTime);
                inner.style.width = (vd.currentTime / vd.duration) * line.offsetWidth + 'px';
            }
            //加载完毕事件
        vd.onended = function() {
            console.log("播放完了 ...")
        }

        line.onmousedown = function() {
            line.onmousemove = function(e) {
                e = event || window.event;
                vd.currentTime = (e.offsetX / line.offsetWidth) * vd.duration;
                inner.style.width = (vd.currentTime / vd.duration) * line.offsetWidth + 'px';
            }
            line.onclick = function(e) {
                e = event || window.event;
                vd.currentTime = (e.offsetX / line.offsetWidth) * vd.duration;
                inner.style.width = e.offsetX + 'px';
            }

        }
        line.onmouseup = function() {
            line.onmousemove = null;
        }
    </script>
</body>

</html>
```
### H5新的选择器
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        
        .box {
            width: 100px;
            height: 100px;
            background-color: red;
        }
    </style>
</head>

<body>
    <div class="box"></div>
    <div class="box"></div>
    <div class="box"></div>
    <div class="box"></div>
    <ul id="nav">
        <li>li_1</li>
        <li>li_2</li>
        <li>li_3</li>
        <li>li_4</li>
        <li>li_5</li>
    </ul>
    <script>
        // querySelector  单个选择器 只选择第一个符合条件的元素
        var box = document.querySelector('.box');
        var nav = document.querySelector('#nav');
        var li = document.querySelector('li')

        // querySelectorAll 选择符合条件的元素的集合
        var boxs = document.querySelectorAll('.box');
        var lis = document.querySelectorAll('li');
    </script>
</body>

</html>
```
### H5操作类名
+ 以往操作类名:
    - 已知元素类名   ele.className = "xxx xxxx"   ele.setAttribute("class","xxx xxx");
    - 未知  封装函数
    - jq addClass removeClass
+ 操作类名新方法: classList    ele.classList.add()/remove()/toggle()/contains() 只能操作单个类名
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style type="text/css">
        * {
            margin: 0;
            padding: 0;
        }
        
        .red {
            color: red;
        }
        
        .fb {
            font-weight: bold;
        }
        
        .big {
            font-size: 30px;
        }
        
        .bg {
            background-color: #00FFFF;
        }
        
        .white {
            color: #fff;
        }
        
        button {
            padding: 10px 20px;
        }
    </style>
</head>

<body>
    <p>不凡学院</p>
    <button>添加red</button>
    <button>添加fb</button>
    <button>切换big</button>
    <button>切换bg</button>
    <button>添加white</button>
    <button>清空类名</button>
    <script>
        var pEle = document.querySelector('p');
        var btns = document.querySelectorAll('button');

        btns[0].onclick = function() {
            pEle.classList.add('red');
        }
        btns[1].onclick = function() {
            pEle.classList.add('fb');
        }
        btns[2].onclick = function() {
            pEle.classList.toggle('big');
        }
        btns[3].onclick = function() {
            var status = pEle.classList.contains('bg');
            if (status) {
                pEle.classList.remove('bg');
            } else {
                pEle.classList.add('bg');
            }
        }
        btns[4].onclick = function() {
            pEle.classList.add("white");
        }
        btns[5].onclick = function() {
            pEle.className = '';
        }
    </script>
</body>

</html>
```
### 自定义属性
写法: 在标签内部data-ownName="ownValue 可以通过  ele.dataset 获取设置的自定义属性
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style type="text/css">
        * {
            margin: 0;
            padding: 0;
        }
        
        .box {
            width: 200px;
            height: 200px;
            background-color: red;
        }
    </style>
</head>

<body>
    <!-- 自定义属性  写法 在标签内部  data-ownName="ownValue"  可以通过  ele.dataset 获取设置的自定义属性 -->
    <div class="box" data-name="张三"></div>
    <script>
        var box = document.querySelector('.box');
        console.log(box.dataset);
        box.onclick = function(e) {
            console.log(e.target.dataset);
        }
    </script>
</body>

</html>
```
### 本地存储
1. `storage` 存储: `window.sessionStorage` `window.localStorage` (向本地保存数据,有可能在浏览器内存里面，有可能在硬盘上面)

2. 特性
	+ 设置、读取方便
	+ 容量较大，`sessionStorage` 约5M、`localStorage` 约20M 不同的浏览器大小可能有差异
	+ 均只能存储字符串类型的对象（虽然规范中可以存储其他原生类型的对象，但是目前为止没有浏览器对其进行实现），可以将对象 `JSON.stringify()` 编码后存储

3. `window.sessionStorage`
	+ 生命周期为当前窗口或标签页，一旦窗口或标签页被关闭了，那么所有通过 `sessionStorage` 存储的数据也就被清空了。
	+ 在同一个窗口下数据可以共享

4. `window.localStorage`
	+ 永久生效，除非手动删除
	+ 可以多窗口共享
	+ IE8 以上的 IE 版本才支持 `localStorage` 这个属性
	+ `localStorage` 本质上是对字符串的读取，如果存储内容多的话会消耗内存空间，会导致页面变卡

5. 两者本质区别：不同浏览器无法共享 `localStorage` 或 `sessionStorage` 中的信息。相同浏览器的不同页面间可以共享相同的 `localStorage`（页面属于相同域名和端口），但是不同页面或标签页间无法共享 `sessionStorage` 的信息。

6. 方法详解
	+ `setItem(key, value)` 设置存储内容
	+ `getItem(key)` 读取存储内容
	+ `removeItem(key)` 删除键值为key的存储内容
	+ `clear()` 清空所有存储内容
	+ `key(n)` 以索引值来获取对应的键

```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8">
    <title>本地存储</title>
</head>

<body>
    <input type="text" class="username">
    <button class="btn">存储session</button>
    <button class="btn2">存储local</button>
    <button class="btn3">获取session</button>
    <button class="btn4">获取local</button>
    <button class="btn5">删除</button>
    <button class="btn6">清空</button>
    <button class="btn7">根据index获取</button>
    <p class="text"></p>
    <script src="https://cdn.bootcss.com/jquery/3.4.0/jquery.min.js"></script>
    <script>
        window.localStorage.setItem('age', 30);

        $('.btn').click(function() {
            // session 和服务器建立链接,那么session存在于整个回话过程
            window.sessionStorage.setItem('name', $('.username').val());
        })
        $('.btn2').click(function() {
            //localStorage 可以把数据存储到本地 不会过期
            window.localStorage.setItem('name', $('.username').val());
        })
        $('.btn3').click(function() {
            var name = window.sessionStorage.getItem('name');
            $('.text').text(name);
        })
        $('.btn4').click(function() {
            var name = window.localStorage.getItem('name');
            $('.text').text(name);
        })
        $('.btn5').click(function() {
            window.localStorage.removeItem('name');
        })
        $('.btn6').click(function() {
            window.localStorage.clear();
        })
        $('.btn7').click(function() {
            var key = window.localStorage.key(0);
            console.log('key==>' + key);
        })
    </script>
</body>

</html>
```