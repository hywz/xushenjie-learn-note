## BOM-1
### BOM入门
+ `ECMAScript` 是 `javascript` 的核心，但是如果要在 `web` 中使用 `javascript`，那么 `BOM` (浏览器对象模型)才是真正的核心。BOM提供了很多对象，用于访问浏览器的功能，这些功能与任何网页内容无关。
+ `BOM` 的核心对象是 `window` ，它表示浏览器的一个实例。在浏览器中， `window` 对象有双重角色，它既是通过 `javascript` 访问浏览器窗口的一个接口，又是 `ECMAScript` 规定的 `Global` 对象。所有全局作用域中声明的变量、函数都会变成 `window` 对象的属性和方法。
### 三大家族之一`offset`家族
+ offsetWidth/offsetHeight   
    - 检测盒子宽高  人为设定的宽高 + padding + border
+ offsetLeft/offsetTop  
    - 检测盒子距离有定位的父盒子的左上距离,最终指向body
    - `offsetLeft` 从父亲的 `padding` 开始算,父亲的 `border` 不算。
+ offsetParent  获取到当前元素有定位的最近的父盒子,没有的话直到body
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <script src="./my.js"></script>
    <title>Document</title>
    <style type="text/css">
        * {
            margin: 0;
            padding: 0;
        }
        
        .box {
            width: 200px;
            height: 200px;
            margin: 50px;
            padding: 50px;
            background-color: orangered;
            /* position: relative; */
        }
        
        .inner {
            width: 100px;
            height: 100px;
            background-color: aqua;
        }
    </style>
</head>

<body>
    <div class="box">
        <div class="inner"></div>
    </div>
</body>

</html>
```
my.js如下:
```javascript
/**
 * 精简版 jQuery $
 * @param str	 字符串(elementTagName, .elementClassName,  #elementIdName)
 */
function $(str) {
    if (str[0] === ".") {
        return document.getElementsByClassName(str.slice(1))[0];
    } else if (str[0] === "#") {
        return document.getElementById(str.slice(1));
    } else {
        eleArr = document.getElementsByTagName(str);
        if (eleArr.length > 1) {
            return eleArr
        } else {
            return eleArr[0]
        }
    }
}
```
```javascript
var box = $('.box');
console.log(box.offsetWidth); //==>300
var inner = $('.inner');
console.log(inner.offsetLeft); //==>100
console.log(inner.offsetParent);
// box没有定位  返回 body元素;box 有定位,返回 box 元素
```
### offsetLeft与styleLeft的区别
+ `offsetTop/Left` 可以返回没有定位盒子的距离左侧的位置。而 `style.top/left` 不可以,只能获取行内样式,没有设置top/left 就返回 ""
+ `offsetTop/Left` 可以返回没有定位盒子的距离左侧的位置。而 `style.top/left` 不可以
+ `offsetTop/Left` 返回的是整数，而 `style.top/left` 返回的是字符串，除了数字外还带有单位：`px`
+ `offsetTop/Left` 只读，而 `style.top/left` 可读写。（只读是获取值，可写是赋值）

### 匀速动画
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
</body>

</html>
```
js部分
```javascript
var box = $('.box');
btns = $('button'),
    timer = null;
btns[0].onclick = function() {
    clearInterval(timer);
    timer = setInterval(function() {
        var cha = 400 - box.offsetLeft,
            count = cha > 0 ? 3 : -3;
        if (Math.abs(count) >= Math.abs(cha)) {
            clearInterval(timer);
            box.style.left = "400px";
        } else {
            box.style.left = box.offsetLeft + count + "px";
        }
    }, 17)
}
btns[1].onclick = function() {
    clearInterval(timer);
    var count = 0;
    timer = setInterval(function() {
        //步长
        count = 3;
        // 800 是终点  box.offsetLeft 是每次执行移动的起点
        // 终点 - 起点 = 距离
        var cha = 800 - box.offsetLeft;
        // 当 步长 count 大于 终点和起点的距离  直接到终点
        if (count >= cha) {
            clearInterval(timer);
            box.style.left = "800px";
        } else {
            box.style.left = box.offsetLeft + count + "px";
        }
    }, 17)
}
```
### 匀速动画优化
```javascript
var box = $('.box'),
    btns = $('button'),
    timer = null;
btns[0].onclick = function() {
    move(box, 400);
};
btns[1].onclick = function() {
    move(box, 800);
};

function move(ele, target) {
    var start, step, cha;
    clearInterval(timer);
    timer = setInterval(function() {
        start = ele.offsetLeft;
        cha = target - start;
        step = cha > 0 ? 6 : -6
        if (Math.abs(step) > Math.abs(cha)) {
            clearInterval(timer);
            ele.style.left = target + "px";
        } else {
            ele.style.left = start + step + "px";
        }
    }, 17)
}
```
### 闪现动画
```javascript
var box = $('.box'),
    btns = $('button');
btns[0].onclick = function() {
    box.style.left = "400px";
}
btns[1].onclick = function() {
    box.style.left = "800px";
}
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
</body>

</html>
```
style.css
```css
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

.list ul {
    position: absolute;
    top: 0;
    left: 0;
    width: 600%;
    height: 100%;
    list-style: none;
}

.list li {
    float: left;
    width: 532px;
    height: 100%;
}

.list li img {
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
```
js部分
```javascript
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
    move(ele, -count * w)

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
    move(ele, -count * w);
    $('.active').className = "";
    dots[count].className = "active";
}
for (var i = 0; i < dots.length; i++) {
    dots[i].index = i;
    dots[i].onclick = function() {
        count = this.index;
        move(ele, -count * w);
        $('.active').className = '';
        this.className = "active";
    }
}
```