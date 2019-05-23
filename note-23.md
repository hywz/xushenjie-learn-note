## BOM-3
### 三大家族之二`Scroll` 家族
+ `scrollWidth` 和 `scrollHeight`
    - 检测盒子的宽高  内容高度 + padding。（调用者：节点元素。属性。）
    - 盒子内容的宽高。（如果有内容超出了，显示内容的宽/高度）
+ `scrollTop` , `scrollLeft`	可读写的
    - 被浏览器或父类遮挡的头部和左边部分。
    - 可以获取或设置一个元素的内容垂直滚动的像素数。element.scrollTop/Left = XXX
+ 获取页面卷入高度的浏览器兼容问题：
    - 各浏览器下 scrollTop/Left的差异
        -  IE6/7/8：
            - 对于没有 doctype 声明的页面里可以使用document.body.scrollTop 来获取 scrollTop高度 ；
            - 对于有 doctype 声明的页面则可以使用document.documentElement.scrollTop； 
        - Safari: 
            - safari 比较特别，有自己获取scrollTop的函数 ： window.pageYOffset ；
        - Firefox: 火狐等等相对标准些的浏览器就省心多了，直接用 document.documentElement.scrollTop ；
    - 兼容写法：`var scrollTop = document.documentElement.scrollTop || window.pageYOffset || document.body.scrollTop`
+  `onscroll` 事件
    - 解释：当元素的滚动条滚动时触发的事件。
    - 用法即：`element.onscroll=function(){};`
**需要注意的是,设置此事件的元素一定要有滚动条**
+ 关于`window.scroll()`,`window.scrollBy()`,`window.scrollTo()`
    - `window.scroll(x,y)`是让window滚动条滚动到那个x,y坐标。//x是水平坐标，y是垂直坐标。
    - `window.scrollBy(-x,-y)`是让window滚动条相对滚动到某个坐标，- 10即相对向左/向上滚动10像素。
    - `window.scrollTo(x,y)`和`window.scroll(x,y)`一样。
### scroll家族
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <script src="../my.js"></script>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        
        body {
            width: 3000px;
            height: 3000px;
        }
        
        .box {
            width: 200px;
            height: 200px;
            /* margin-top: 3000px; */
            background-color: red;
            overflow: auto;
        }
        
        .inner {
            width: 400px;
            height: 400px;
            background-color: #800080;
        }
    </style>
    <title>Document</title>
</head>

<body>
    <div class="box">
        <div class="inner"></div>
    </div>
</body>

</html>
```
js部分如下:
```javascript
var box = $('.box');
// scrollWidth/Height 值  内容溢出时 值 = 内容宽/高 + padding
// 内容未溢出 值 = 盒子宽高 + padding
var boxSw = box.scrollWidth,
    boxSh = box.scrollHeight;
// offsetWidth/Height 值
var boxOw = box.offsetWidth,
    boxOh = box.offsetHeight;

console.log("box的offset值====>", "宽:" + boxOw, "高" + boxOh); //==>200 200
console.log("box的scroll值====>", "宽:" + boxSw, "高" + boxSh); //==>400 400

// `scrollTop` , `scrollLeft`	可读写的

// > 被浏览器或父类遮挡的头部和左边部分。
// > 可以获取或设置一个元素的内容垂直滚动的像素数。

window.onclick = function() {
    var scrollTop = document.documentElement.scrollTop || window.pageYOffset || document.body.scrollTop;
    var scrollLeft = document.documentElement.scrollLeft || window.pageXOffset || document.body.scrollLeft;
    console.log("上===>" + scrollTop, "左===>" + scrollLeft);
}
box.onclick = function() {
    console.log(box.scrollTop, box.scrollLeft);
}
window.onclick = function() {
    var scrollTop = sct(),
        scrollLeft = scl();
    console.log("上===>" + scrollTop, "左===>" + scrollLeft);
}

// 封装函数获取被页面卷入的高度
function sct() {
    return document.documentElement.scrollTop || window.pageYOffset || document.body.scrollTop;
}
// 封装函数获取被页面卷入的左边距
function scl() {
    return document.documentElement.scrollLeft || window.pageXOffset || document.body.scrollLeft;
}
```
### 固定导航栏
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <script src="../my.js"></script>
    <title>Document</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        
        .nav {
            position: fixed;
            top: 50px;
            left: 100px;
            width: 450px;
            border: 3px solid black;
        }
        
        .nav div {
            float: left;
            width: 150px;
            height: 40px;
        }
        
        .nav div:first-child {
            background-color: #a01313;
        }
        
        .nav div:nth-child(2) {
            background-color: #673ab7;
        }
        
        .nav div:last-child {
            background-color: #788404;
        }
        
        .header {
            height: 1500px;
            background-color: #a01313;
        }
        
        .container {
            height: 1500px;
            background-color: #673ab7;
        }
        
        .footer {
            height: 1500px;
            background-color: #788404;
        }
    </style>
</head>

<body>
    <div class="nav">
        <div></div>
        <div></div>
        <div></div>
    </div>
    <div class="header"></div>
    <div class="container"></div>
    <div class="footer"></div>
</body>

</html>
```
js部分如下:
```javascript
var nav = $('.nav'),
    header = $('.header'),
    footer = $('.footer'),
    container = $('.container');

// 1. 获取到相应元素距离 body 顶部的距离
nav.children[0].onclick = function() {
    var h = header.offsetTop;
    slow(h);
}
nav.children[1].onclick = function() {
    var h = container.offsetTop;
    slow(h);
}
nav.children[2].onclick = function() {
        var h = footer.offsetTop;
        slow(h);
    }
// 2. 封装函数让window滚动到相应位置
var timer = null;

function slow(target) {
    var start, step;
    clearInterval(timer);
    timer = setInterval(function() {
        start = sct();
        step = (target - start) / 10;
        // 判断step的临界值
        if (Math.abs(step) < 1) {
            // step === 0 这个情况未处理  不要直接写 1/-1
            step = step > 0 ? Math.ceil(step) : Math.floor(step);
        }
        // 停止条件
        if (start + step == target) {
            clearInterval(timer);
        }
        // 页面滚动
        window.scroll(0, start + step)
    }, 17)
}
```
### 滚动改变导航栏
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <script src="../my.js"></script>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        
        body {
            height: 2000px;
        }
        
        .header {
            position: fixed;
            top: 0;
            width: 100%;
            height: 300px;
            background-color: #000;
        }
    </style>
    <title>Document</title>
</head>

<body>
    <div class="header"></div>
    <script>
        var header = $('.header');
        var high = header.offsetHeight;
        // console.log(high);
        // 高度变化,改变透明度
        // opacity 	1 - 0
        // 高度变化  0-300		存在一个比例
        // 300-h === 1-opacity
        // 300-height/300 === 50-变化高度/50

        window.onscroll = function() {
            // 获取当前滚动高度
            var h = sct();
            //当量=300,原始透明度1,最终透明度0,原始高度h,最终高度0.
            if (h <= high) {
                // 计算当前透明度和高度
                header.style.opacity = opacity - h / high;
                header.style.height = high - h + 'px';
            } else {
                header.style.opacity = 0;
                header.style.height = 0;
            }
            //当量=150,原始透明度1,最终透明度0,原始高度h,最终高度0.
            // if (h <= 150) {
            //     // 计算当前透明度和高度
            //     //当前透明度=原始透明度opacity-当前滚动高度h*(原透明opacity-最终透明值0)/当量
            //     header.style.opacity = opacity - h * 1 / 150;
            //     //当前高度=原始高度high-当前滚动高度h*(原始高度high-最终高度0)/当量
            //     header.style.height = high - h * high / 150 + 'px';
            // } else {
            //     header.style.opacity = 0;
            //     header.style.height = 0;
            // }
        }

        // 原生js来获取DOM元素的CSS样式
        function getStyle(ele) {
            var style = null;
            if (window.getComputedStyle) {
                style = window.getComputedStyle(ele, null);
            } else {
                style = ele.currentStyle;
                //兼容IE
            }
            return style;
        }
    </script>
</body>

</html>
```
### 广告跟随
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <script src="../my.js"></script>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        
        body {
            height: 2000px;
        }
        
        .advance {
            position: absolute;
            top: 50%;
            right: 60px;
            width: 40px;
            height: 100px;
            padding: 40px 20px;
            color: #fff;
            background-color: crimson;
        }
    </style>
    <title>Document</title>
</head>

<body>
    <div class="advance">这是一条小广告</div>
    <script>
        var adv = $('.advance');
        // 1. 获取广告在页面未滚动时的原始高度 offsetTop
        var originY = adv.offsetTop;
        var timer = null;
        window.onscroll = function() {
            // 获取页面卷入高度  获取的值可能不是整数,变成整数
            // var h = parseInt(sct());
            var h = sct();
            // console.log(h);
            var start, target, step;
            clearInterval(timer);
            timer = setInterval(function() {
                start = adv.offsetTop;
                //目标值===>页面卷入高度 + 原始高度
                target = h + originY;
                step = (target - start) / 10;
                //判断临界值
                if (Math.abs(step) < 1) {
                    step = step > 0 ? Math.ceil(step) : Math.floor(step);
                }
                adv.style.top = start + step + 'px';
                if (start + step == target) {
                    console.log('stop...');
                    clearInterval(timer);
                }
            }, 17)
        }
    </script>
</body>

</html>
```
### 回到顶部
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <script src="../my.js"></script>
    <title>Document</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        
        body {
            height: 2600px;
        }
        
        .back {
            position: fixed;
            top: 50%;
            right: 150px;
            width: 30px;
            height: 105px;
            display: none;
            padding-top: 5px;
            text-align: center;
            line-height: 24px;
            cursor: pointer;
            -webkit-user-select: none;
            border: 1px solid red;
            background-color: skyblue;
        }
    </style>
</head>

<body>
    <div class="back">回到顶部</div>
    <script>
        var back = $('.back');
        window.onscroll = function() {
            var h = sct();
            if (h >= 500) {
                back.style.display = 'block';
            } else {
                back.style.display = 'none';
            }
        }
        back.onclick = function() {
            var timer = setInterval(function() {
                var start = sct(),
                    step = -start / 10;
                if (step > -1) {
                    step = Math.floor(step);
                }
                window.scroll(0, start + step);
                if (start + step == 0) {
                    clearInterval(timer)
                }
            }, 17)
        }
    </script>
</body>

</html>
```