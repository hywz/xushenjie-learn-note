## js补充
### 轮播回顾
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
        
        ul {
            list-style: none;
        }
        
        a {
            text-decoration: none;
        }
        
        .banner {
            position: relative;
            width: 1226px;
            height: 460px;
            margin: 100px auto;
        }
        
        .banner img {
            width: 1226px;
            height: 460px;
        }
        
        .banner .arr {
            position: absolute;
            top: 50%;
            left: 224px;
            width: 40px;
            height: 70px;
            margin-top: -35px;
            font-size: 24px;
            line-height: 70px;
            text-align: center;
            background-color: rgba(0, 0, 0, .3);
        }
        
        .banner .arr.arr-r {
            left: auto;
            right: 0;
        }
        
        .banner .dots {
            position: absolute;
            right: 20px;
            bottom: 20px;
        }
        
        .dots .dot-item {
            float: left;
            width: 10px;
            height: 10px;
            margin-left: 10px;
            border-radius: 50%;
            border: 1px solid red;
        }
        
        .dots .dot-item a {
            display: block;
            width: 100%;
            height: 100%;
        }
        
        .dots .dot-item.active a {
            background-color: red;
        }
    </style>
</head>

<body>
    <div class="banner">
        <img src="img/m1.jpg" alt="">
        <!-- 取消a标签的点击跳转 -->
        <!-- js添加事件 -->
        <!-- 1. 在script 里边 获取事件源  然后添加 -->
        <!-- 2.在html标签当中添加 -->
        <a href="javascript:;" class="arr arr-l" onclick="swipeImg(false)">
        </a>
        <a href="javascript:;" class="arr arr-r" onclick="swipeImg(true)">&gt;</a>
        <ul class="dots">
            <!-- <li class="dot-item active"><a href="javascipt:;"></a></li> -->
        </ul>
    </div>
    <!-- 引入工具库 -->
    <script src="js/util.js"></script>
    <script>
        var imgArr = ['m1.jpg', 'm2.jpg', 'm3.jpg', 'm4.jpg', 'm5.jpg', 'm6.jpg'];
        var imgEl = document.getElementsByTagName('img')[0];
        var ulEl = document.getElementsByClassName('dots')[0];
        initDots(ulEl, imgArr);
        var dotChildren = ulEl.children;
        var count = 0;
        /**
         * @params isRight 是否点击的是右边按钮  boolean
         **/
        function swipeImg(isRight) {
            if (isRight) {
                count++;
                if (count === imgArr.length) {
                    count = 0;
                }
            } else {
                count--;
                if (count === -1) {
                    count = imgArr.length - 1;
                }
            }
            console.log(count)
            go(count);
            // imgEl.src = 'img/' + imgArr[count];
            // // 小圆点样式跟着改变
            // // 排他
            // for (var i = 0; i < dotChildren.length; i++) {
            //     delClass(dotChildren[i],'active');
            // }
            // addClass(dotChildren[count],'active');
        }

        function initDots(el, arr) {
            var str = '';
            for (var i = 0; i < arr.length; i++) {
                str += '<li class="dot-item' + (i === 0 ? ' active' : '') + '"><a href="javascipt:;" onclick="go(' + i + ')"></a></li>';
            }
            el.innerHTML = str;
        }
        // onclick="go('+i+')"
        function go(num) {
            // 给计数器赋值
            count = num;
            imgEl.src = 'img/' + imgArr[num];
            for (var i = 0; i < dotChildren.length; i++) {
                delClass(dotChildren[i], 'active');
            }
            addClass(dotChildren[num], 'active');
        }
        // 给 小圆点(分页器) 循环绑定事件
        // for (var i = 0; i < dotChildren.length; i++) {
        //     dotChildren[i].index = i;
        //     // 点击的 小圆点的下标
        //     dotChildren[i].onclick = function(){
        //         // imgEl.src = 'img/' + imgArr[i]; 
        //         // 获取下标 i ?   
        //         console.log(this.index);
        //         // dotChildren伪数组,具有length属性,但是不具有数组的方法
        //         var index = this.index;
        //         imgEl.src = 'img/' + imgArr[index];
        //         for (var j = 0; j < dotChildren.length; j++) {
        //             delClass(dotChildren[j],'active');
        //         }
        //         addClass(dotChildren[index],'active');
        //     }    
        // }
    </script>
</body>

</html>
```
### arguments对象
```javascript
function add(x, y) {
    console.log(arguments);
    console.log(arguments[0]); //==>3
    // arguments 是一个伪数组 
    console.log(typeof arguments); //==>object
    console.log(arguments instanceof Array); //==>false
    // instanceof 用于判断  是不是某个构造函数的实例对象 
    // 可以判断 是不是数组,是不是函数    
    return x + y;
}
add(3, 7, 5)
```
### callee
```javascript
function add(x, y) {
    console.log(arguments);
    console.log(arguments.callee);
    //返回的是正在执行的函数本身。 也是在函数体内使用。 
    //在使用函数递归调用时推荐使用arguments.callee代替函数名本身。 
    return x + y;
}
add(2, 3);
//递归
function fb(num) {
    if (num == 1 || num == 2) {
        return 1;
    }
    return arguments.callee(num - 1) + arguments.callee(num - 2);
}
console.log(fb(3));
```
### 立即执行函数
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
    <ul>
        <li class="li-item">li</li>
        <li class="li-item">li</li>
        <li class="li-item">li</li>
        <li class="li-item">li</li>
        <li class="li-item">li</li>
        <li class="li-item">li</li>
        <li class="li-item">li</li>
    </ul>
</body>

</html>
```
1. 具名函数
```javascript
function foo() {

}
foo();
```
2. 匿名函数表达式
```javascript
var a = function() {

}
a();
```
3. 立即执行函数(自执行函数)
```javascript
//传参
(function(n) {
    console.log(n)
})(6);
// 函数传参 可以是任意的数据类型 可以是其他函数

//循环绑定事件 获取当前的 i
var lis = document.getElementsByClassName('li-item');
for (var i = 0; i < lis.length; i++) {
    lis[i].onclick = (function(n) {
            // 这里涉及"闭包" 简单点来说 就是在函数外部可以调用函数内部的变量
            return function() {
                console.log(n);
            }
        })(i)
        //用自执行函数解决
}
```
### addEventListener
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        .box {
            width: 100px;
            height: 100px;
            background: #000;
        }
        
        .inner-box {
            width: 50px;
            height: 50px;
            background-color: red;
        }
    </style>
</head>

<body>
    <div class="box">
        <div class="inner-box">

        </div>
    </div>
</body>

</html>
```
1. boxEL.onclick=function(){}
```javascript
boxEl.onclick = function() {
        alert('123');
    }
    // 会覆盖之前的
boxEl.onclick = function() {
        alert('345');
    }
```
2. 在 html 标签属性中添加事件 onclick=go();
3. addEventListener
```javascript
boxEl.addEventListener('click', function() {
        alert('我是外部box');
    }, false)
    // 可以注册多个事件
    boxEl.addEventListener('click', function() {
        alert('edf');
    })
```
+ 第一个参数: 字符串 事件类型  不带"on"
+ 第二个参数: 函数 (要执行的程序)
+ 第三个参数: false/true 是否捕获执行 默认false   
```javascript
innerBox.addEventListener('click', function(event) {
        alert('我是inner-box');
        // 阻止冒泡!
        event.stopPropagation();
    })
```
+ 从里到外:   冒泡
+ 从外到里:   捕获
+ 点击innerbox 只执行 innerbox的事件..(阻止冒泡)
### 移除绑定
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        .box {
            width: 100px;
            height: 100px;
            background: #000;
        }
        
        .inner-box {
            width: 50px;
            height: 50px;
            background-color: red;
        }
    </style>
</head>

<body>
    <div class="box">
        <div class="inner-box">

        </div>
    </div>
    <button>删除事件</button>
    <script>
        var boxEl = document.getElementsByClassName('box')[0];
        var innerBox = document.getElementsByClassName('inner-box')[0];
        var btn = document.getElementsByTagName('button')[0];
        boxEl.onclick = function() {
            alert('123');
        }
        boxEl.onclick = null; //移除绑定

        innerBox.addEventListener('click', foo, true); //捕获
        innerBox.addEventListener('click', foo); //冒泡
        //点击按钮时,删除事件
        btn.onclick = function() {
            innerBox.removeEventListener('click', foo); //冒泡
            // innerBox.removeEventListener('click', foo, true); //捕获
        }

        //删除时,捕获和冒泡必须是一致的
        function foo() {
            alert('我是内部盒子');
        }
    </script>
</body>

</html>
```
### 定时器
1. 延迟执行
```javascript
// 3000ms之后执行
setTimeout(function() {
    console.log('abc');
}, 3000);
//或者如下:
// setTimeout(foo,3000);
// function foo(){
//     alert('abc');
// }
```
2. 循环执行
```javascript
// 每隔1000ms 执行一次
var timer = setInterval(function() {
    console.log('循环执行')
}, 1000)
setTimeout(function() {
    clearInterval(timer); //清除循环定时器
}, 5000)
clearTimeout(); //清除延迟定时器的
```
### 定时器例子
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        .ads {
            width: 100px;
            height: 100px;
            background-color: red;
        }
    </style>
</head>

<body>
    <div class="ads">

    </div>
</body>

</html>
```
5秒之后关闭广告
```javascript
var ads = document.getElementsByClassName('ads')[0];
setTimeout(function() {
    ads.style.display = 'none'
}, 5000)
```
### 倒计时
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
    <p>距离<span></span>还有:</p>
    <p class="stamp"></p>
    <script>
        var spanEl = document.getElementsByTagName('span')[0];
        var stampEl = document.getElementsByClassName('stamp')[0];
        var oldTimeStr = '2019-06-13 21:00';
        spanEl.innerText = oldTimeStr;
        var oldTime = new Date(oldTimeStr);
        console.log(oldTime);

        setInterval(function() {
            var nowTime = new Date();
            // 计算时间差
            // 获取时间戳
            var stamp = oldTime.getTime() - nowTime.getTime();
            console.log(stamp);
            // 将毫秒换算成 几时几分几秒
            var DAY_MS = 24 * 60 * 60 * 1000,
                HOUR_MS = 60 * 60 * 1000,
                MIN_MS = 60 * 1000,
                S_MS = 1000,
                day = Math.floor(stamp / DAY_MS),
                hour = Math.floor(stamp % DAY_MS / HOUR_MS),
                min = Math.floor(stamp % HOUR_MS / MIN_MS),
                s = Math.floor(stamp % MIN_MS / S_MS),
                stampStr = '' + wrap(day) + '天' + wrap(hour) + '时' + wrap(min) + '分' + wrap(s) + '秒'
            stampEl.innerText = stampStr;
        }, 1000)

        function wrap(n) {
            return n >= 10 ? n : '0' + n;
        }
    </script>
</body>

</html>
```