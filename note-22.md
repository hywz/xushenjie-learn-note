## BOM-2
### 事件对象event
+ `Event` 对象代表事件的状态，比如事件在其中发生的元素、键盘按键的状态、鼠标的位置、鼠标按钮的状态
+ 获得event对象兼容性写法: `event || window.event`
+ `event.target` 事件的目标	获得target兼容型写法:  `event.target || event.srcElement`
+ `e.pageX/Y`		获取鼠标点击的相对于页面的位置
+ `e.clientX/Y`	获取鼠标点击的相对于可视区域的位置
+ `e.screenX/Y`	获取鼠标点击的相对于屏幕的位置
+ `e.offsetX/Y`		表示鼠标指针位置相对于触发事件的对象的位置
+ `event.type`	事件的类型
+ `event.button` 鼠标点击的按键(只认识三个键) 可在`onmousedown` 事件中测试
    + === 0 您点击了鼠标左键
    + === 1 您点击了鼠标中键
    + === 2 您点击了鼠标右键
### 鼠标拖拽
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <script src="../../jQuery/lib/jquery-3.4.1.min.js"></script>
    <title>Document</title>
    <style>
        .box1 {
            margin: 50px auto;
            width: 600px;
            height: 500px;
            border: 1px solid slateblue;
        }
        
        .box {
            position: absolute;
            width: 200px;
            height: 200px;
            background-color: skyblue;
        }
    </style>
</head>

<body>
    <div class="box1">
        <div class="box"></div>
    </div>

    <script>
        var box = $('.box');
        var box1 = $('.box1');
        var box1X = box1.offset().left,
            box1Y = box1.offset().top,
            box1W = box1.width(),
            boX1H = box1.height(),
            boxW = box.width(),
            boxH = box.height();
        // console.log(box1X);
        // console.log(box1W);
        box.mousedown(function(e) {
            var e = event || window.event,
                originX = e.offsetX,
                originY = e.offsetY;
            window.onmousemove = function(e) {
                e = event || window.event;
                var distanceX = e.pageX - originX,
                    distanceY = e.pageY - originY;
                if (distanceX < box1X) {
                    distanceX = box1X;
                }
                if (distanceX > box1W + box1X - boxW) {
                    distanceX = box1W + box1X - boxW;
                }
                if (distanceY < box1Y) {
                    distanceY = box1Y;
                }
                if (distanceY > boX1H + box1Y - boxH) {
                    distanceY = boX1H + box1Y - boxH;
                }
                box[0].style.left = distanceX + 'px';
                box[0].style.top = distanceY + 'px';
            }
            window.onmouseup = function() {
                window.onmousemove = null;
            }
        })
    </script>
</body>

</html>
```
### 鼠标跟随
```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8">
    <title>鼠标跟随</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        
        .box1 {
            width: 600px;
            height: 400px;
            margin: 50px auto;
            border: 1px solid #000;
        }
        
        .box {
            position: absolute;
            width: 200px;
            height: 200px;
            background-color: #FF4500;
        }
    </style>
</head>

<body>
    <div class="box1">
        <div class="box"></div>
    </div>

    <script src="../../jQuery/lib/jquery-3.4.1.min.js" type="text/javascript" charset="utf-8"></script>
    <script type="text/javascript">
        var box = $('.box');
        var box1 = $('.box1');
        var box1X = box1.offset().left,
            box1Y = box1.offset().top,
            box1W = box1.width(),
            boX1H = box1.height(),
            boxW = box.width(),
            boxH = box.height();

        // 鼠标在 页面上 移动
        box.mouseenter(function() {
            window.onmousemove = function(e) {
                e = event || window.event;
                var distanceX = e.pageX - boxW / 2,
                    distanceY = e.pageY - boxH / 2;
                if (distanceX < box1X) {
                    distanceX = box1X;
                }
                if (distanceX > box1W + box1X - boxW) {
                    distanceX = box1W + box1X - boxW;
                }
                if (distanceY < box1Y) {
                    distanceY = box1Y;
                }
                if (distanceY > boX1H + box1Y - boxH) {
                    distanceY = boX1H + box1Y - boxH;
                }
                box[0].style.left = distanceX + 'px';
                box[0].style.top = distanceY + 'px';
            }
        })

        box1.mouseleave(function() {
            window.onmousemove = null;
        })
    </script>
</body>

</html>
```
### 缓动动画
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <script src="./my.js"></script>
    <title>Document</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        
        .box {
            position: relative;
            width: 200px;
            height: 200px;
            background-color: orange;
        }
    </style>
</head>

<body>
    <div class="box"></div>

    <button>点击跳到400px</button>
    <button>点击跳到800px</button>
    <script>
        var box = $('.box'),
            btns = $('button'),
            timer = null;
        btns[0].onclick = function() {
            slowly(box, 400);
        };
        btns[1].onclick = function() {
            slowly(box, 800);
        };

        function slowly(ele, target) {
            clearInterval(timer);
            timer = setInterval(function() {
                var step, start;
                start = ele.offsetLeft;
                step = (target - start) / 10;
                if (Math.abs(step) < 1) {
                    // step = step > 0 ? 1 : -1;
                    step = step > 0 ? Math.ceil(step) : Math.floor(step);
                }
                ele.style.left = start + step + 'px';
                if (start + step == target) {
                    clearInterval(timer);
                }
            }, 17)
        }
        // btns[0].onclick = function() {
        //     clearInterval(timer);
        //     timer = setInterval(function() {
        //         var cha = 400 - box.offsetLeft,
        //             count = cha > 0 ? 3 : -3;
        //         if (Math.abs(count) >= Math.abs(cha)) {
        //             clearInterval(timer);
        //             box.style.left = "400px";
        //         } else {
        //             box.style.left = box.offsetLeft + count + "px";
        //         }
        //     }, 17)
        // }
        // btns[1].onclick = function() {
        //     clearInterval(timer);
        //     var count = 0;
        //     timer = setInterval(function() {
        //         //步长
        //         count = 3;
        //         // 800 是终点  box.offsetLeft 是每次执行移动的起点
        //         // 终点 - 起点 = 距离
        //         var cha = 800 - box.offsetLeft;
        //         // 当 步长 count 大于 终点和起点的距离  直接到终点
        //         if (count >= cha) {
        //             clearInterval(timer);
        //             box.style.left = "800px";
        //         } else {
        //             box.style.left = box.offsetLeft + count + "px";
        //         }
        //     }, 17)
        // }
    </script>
</body>

</html>
```
### 轮播动画
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <link rel="stylesheet" href="./css/style.css">
    <script src="./my.js"></script>
    <style>
        * {
            margin: 0;
            padding: 0;
        }

        .box {
            position: relative;
            width: 532px;
            height: 200px;
            margin: 50px auto;
            border: 1px solid #FF0000;
            overflow: hidden;
        }

        ul {
            position: absolute;
            top: 0;
            left: 0;
            width: 600%;
            height: 100%;
            list-style: none;
        }

        li {
            float: left;
            width: 532px;
            height: 100%;
        }

        li img {
            width: 100%;
            height: 100%;
        }

        .arrow {
            width: 532px;
            margin: 0 auto;
            text-align: center;
        }

        .arrow button {
            width: 150px;
            line-height: 30px;
        }

        .arrow button:first-child {
            margin-right: 40px;
        }
        
        .box .dots {
            position: absolute;
            right: 20px;
            bottom: 20px;
            list-style: none;
            width: 105px;
            height: 9px;
            top: auto;
            left: auto;
        }
        
        .box .dots li {
            float: left;
            width: 7px;
            height: 7px;
            border-radius: 50%;
            border: 1px solid rgba(0, 0, 0, 0.1);
            margin-right: 12px;
            background: rgba(0, 0, 0, 0.3);
            cursor: pointer;
        }
        
        .box .dots li:hover {
            border-color: rgba(0, 0, 0, 0.3);
            background: white;
        }
        
        .box .dots .active {
            border-color: rgba(0, 0, 0, 0.3);
            background: white;
        }
    </style>
    <title>Document</title>
</head>

<body>
    <div class="box">
        <ul class="list">
            <li><img src="./img/m1.jpg" alt="sorry"></li>
            <li><img src="./img/m2.jpg" alt="sorry"></li>
            <li><img src="./img/m4.jpg" alt="sorry"></li>
            <li><img src="./img/m5.jpg" alt="sorry"></li>
            <li><img src="./img/m6.jpg" alt="sorry"></li>
            <li><img src="./img/m1.jpg" alt="sorry"></li>
        </ul>
        <ul class="dots">
            <li class="active"></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
        </ul>
    </div>
    <div class="arrow">
        <button>上一个</button>
        <button>下一个</button>
    </div>
    <script>
        var ele = $('.list');
        //一个li的宽度
        var w = ele.children[0].offsetWidth;
        var btns = $('button');
        //计数器
        var count = 0;
        //获取小圆点数组集合
        var dots = $('.dots').children;
        btns[1].onclick = function() {
            if (count === ele.children.length - 1) {
                //清零
                ele.style.left = 0;
                count = 0;
            }
            count++;
            slowly(ele, -count * w)

            // 清除激活小点的样式
            $('.active').className = "";
            if (count == ele.children.length - 1) {
                // 临界值 最后一张  第一个小点激活
                dots[0].className = "active";
            } else {
                dots[count].className = "active";
            }
        }
        btns[0].onclick = function() {
            if (count === 0) {
                ele.style.left = -(ele.children.length - 1) * w + 'px';
                count = 5;
            }
            count--;
            slowly(ele, -count * w);
            $('.active').className = "";
            dots[count].className = "active";
        }
        for (var i = 0; i < dots.length; i++) {
            dots[i].index = i;
            dots[i].onclick = function() {
                count = this.index;
                slowly(ele, -count * w);
                $('.active').className = '';
                this.className = "active";
            }
        }
    </script>
</body>

</html>
```
### 放大镜
```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8">
    <title>放大镜</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        
        .box,
        .box2 {
            position: relative;
            float: left;
            width: 400px;
            height: 400px;
            margin-top: 20px;
            margin-left: 50px;
            border: 20px solid red;
            overflow: hidden;
        }
        
        .box img {
            width: 100%;
            height: 100%;
            user-select: none;
        }
        
        .inner {
            position: absolute;
            top: 0;
            left: 0;
            width: 100px;
            height: 100px;
            background-color: #0000ff99;
            cursor: move;
        }
        
        .box2 {
            display: none;
        }
        
        .box2 img {
            width: 200%;
            height: 200%;
        }
    </style>
</head>

<body>
    <!-- ondragstart="return false;"  让 img 元素无法被选中拉扯 -->
    <div class="box">
        <img src="./img/1.jpg" alt="sorry" ondragstart="return false;">
        <div class="inner" ondragstart="return false;"></div>
    </div>
    <div class="box2">
        <img src="./img/1.jpg" alt="sorry" ondragstart="return false;">
    </div>

    <script src="./my.js" type="text/javascript" charset="utf-8"></script>
    <script type="text/javascript">
        var inner = $('.inner'),
            imgEle = $('.box2').children[0],
            box = $('.box'),
            box2 = $('.box2'),
            boxL = box.offsetLeft,
            boxT = box.offsetTop,
            boxW = box.offsetWidth,
            boxH = box.offsetHeight,
            innerW = inner.offsetWidth,
            innerH = inner.offsetHeight,
            // boW = box.scrollWidth,
            // boH = box.scrollHeight;
            border = box.clientLeft;

        // border = parseInt('box.borderWidth');

        console.log(boxL);
        box.onmouseenter = function() {
            box2.style.display = 'block';
        }
        box.onmouseleave = function() {
            box2.style.display = 'none';
        }
        inner.onmousedown = function(e) {
            var e = event || window.event,
                //获取原始鼠标相对于inner的位置+boxL/boxT
                originX = e.offsetX + boxL,
                originY = e.offsetY + boxT;
            // console.log(e.offsetX);==>鼠标相对于触发事件对象inner的left位置
            box.onmousemove = function(e) {
                e = event || window.event;
                //获取inner相对于父元素box的位置
                var distanceX = e.pageX - originX - border,
                    distanceY = e.pageY - originY - border;
                // console.log(e.pageX);==>鼠标相对于页面body的位置
                // console.log('鼠标相对于页面body的位置e.pageX==>' + e.pageX);
                // console.log('鼠标相对于inner的位置originX==>' + originX);
                if (distanceX < 0) {
                    distanceX = 0;
                }
                if (distanceX > boxW - innerW - border * 2) {
                    distanceX = boxW - innerW - border * 2;
                }
                if (distanceY < 0) {
                    distanceY = 0;
                }
                if (distanceY > boxH - innerH - border * 2) {
                    distanceY = boxH - innerH - border * 2;
                }
                inner.style.left = distanceX + 'px';
                inner.style.top = distanceY + 'px';

                // 放大的 img 反方向移动两倍的距离
                imgEle.style.marginLeft = -2 * distanceX + 'px';
                imgEle.style.marginTop = -2 * distanceY + 'px';
            }
        }
            // 鼠标抬起
        window.onmouseup = function() {
                // 清除move事件
                box.onmousemove = null;
            }
            // inner.onmouseleave = function() {
            //     box.onmousemove = null;
            // }
    </script>
</body>

</html>
```
### 事件委托
```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8">
    <title>事件委托</title>
</head>

<body>
    <ul>
        <li>li_1</li>
        <li>li_2</li>
        <li>li_3</li>
        <li>li_4</li>
        <li>li_5</li>
    </ul>

    <script src="./my.js" type="text/javascript" charset="utf-8"></script>
    <script type="text/javascript">
        var ul = $('ul'),
            liEl = document.createElement('li');
        liEl.innerText = 'li_6';
        ul.appendChild(liEl);
        // 事件有冒泡机制  从里到外 依次触发事件
        ul.onclick = function(e) {
            e = event || window.event;
            var target = e.target || e.srcElement;
            if (target.tagName === 'LI') {
                target.style.color = 'red';
            }
        }
    </script>
</body>

</html>
```
### 事件冒泡和阻止冒泡
```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8">
    <title>事件冒泡和阻止冒泡</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        
        html,
        body {
            width: 100%;
            height: 100%;
        }
        
        .box {
            position: fixed;
            top: 0;
            left: 0;
            display: none;
            width: 100%;
            height: 100%;
            padding-top: 150px;
            background-color: grey;
        }
        
        img {
            display: block;
            margin: 0 auto;
        }
        
        button {
            padding: 10px 20px;
        }
        /* .box{
				width: 300px;
				height: 300px;
				padding: 1px;
				margin: 30px auto;
				background-color: #FFA500;
			}
			.inner{
				width: 200px;
				height: 200px;
				padding: 1px;
				margin: 50px auto;
				background-color: #FF4500;
			}
			.red{
				width: 100px;
				height: 100px;
				margin: 50px auto;
				background-color: #00FFFF;
			} */
    </style>
</head>

<body>
    <button>显示遮罩层</button>
    <div class="box">
        <img src="./img/wx.jpg" alt="">
    </div>

    <!-- <div class="box">
			<div class="inner">
				<div class="red"></div>
			</div>
		</div> -->

    <script src="./my.js" type="text/javascript" charset="utf-8"></script>
    <script type="text/javascript">
        $("button").onclick = function() {
            $(".box").style.display = "block";
        }

        $(".box").onclick = function() {
            this.style.display = "none";
        }
        $("img").onclick = function(e) {
            e = event || window.event;
            e.stopPropagation ? e.stopPropagation() : e.cancelBubble = true;
        }

        // $(".red").onclick = function (e){
        // 	e = event || window.event;
        // 	console.log("red")
        // 	e.stopPropagation ? e.stopPropagation() : e.cancelBubble = true;
        // }
        // $(".inner").onclick = function (e){
        // 	e = event || window.event;
        // 	console.log("inner")
        // 	e.stopPropagation ? e.stopPropagation() : e.cancelBubble = true;
        // }
        // $(".box").onclick = function (){
        // 	console.log("box")
        // }
    </script>
</body>

</html>
```