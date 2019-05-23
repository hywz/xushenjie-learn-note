## BOM-4
### 三大家族之三`Client` 家族
+ `clientWidth` `clientHeight`
    - 检测盒子的宽高 clientHeight/W 盒子 自身宽高 + padding 内容溢出不算
    - offsetHeight/W 盒子 自身宽高+ padding + border
    - scrollHeight/W 内容宽高 + padding
    - document.documentElement.clientWidth/clientHeight  获取浏览器可视区域的宽高		没有兼容问题
    - window.innerWidth/innerHeight		IE <= 8 不支持			表示获取 window 可视区域的内部大小
    - window.outerWidth/outerHeight		IE <= 8 不支持			表示整个浏览器窗体的大小
+ `clientTop` `clientLeft`只读
    - 表示内容区域的左上角相对于整个元素左上角的位置   实际上就是 border 的宽度
    - 内容区域:内容+padding		padding 之外就剩 border
    - 一个元素顶部和左侧边框(border)的宽度
### 获取元素的样式
+ 行内样式 可以通过 `ele.style.styleName` 获取
+ 内联样式和外联样式可以通过以下两种方式获取:
    1. `window.getComputedStyle(element, [pseudoElt]).styleName`
        + 返回的是一个字符串,`window`可省略
        + 仅用于谷歌和火狐等标准浏览器
        + `element` 用于获取计算样式的元素。
        + `pseudoElt` 指定一个要匹配的伪元素的字符串。必须对普通元素省略（或`null`）,一般都写成 `null`.  如果要获取伪元素的样式,则写上要获取的伪元素的名字,例如:
        +   ```html
        
            <style>
                h3::after {
            content: "hello world!";
                }
            </style>
            <h3>带有伪元素</h3>
            <script>
                var h3 = document.getElementsByTagName('h3'), 
                result = getComputedStyle(h3, '::after').content;
                console.log(result); // ==>"hello world!"
            </script>
            
            ```
    2. `element.currentStyle.styleName` 仅用于 IE 
    3. 兼容写法:
    ```js
    /**
    * 获取任意元素的css样式
    **/
    function getStyle(ele,styleName){
        if(ele.currentStyle){
            return ele.currentStyle[styleName];
        }else{
            return window.getComputedStyle(ele,null)[styleName];
        }
    }

    ```
    **取对象的属性  如果该属性是变量,那么需要用[]的形式获取**
    ```js
    var abc = "name";
    var user = {
        name:'张三',
        age:20
    }
    console.log(user[abc]);
    console.log(user.name)
    ```
### client家族
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <script src="../my.js"></script>
    <title>Document</title>
    <style type="text/css">
        * {
            margin: 0;
            padding: 0;
        }
        
        .box {
            width: 200px;
            height: 200px;
            padding: 20px 30px;
            border-width: 12px 9px 9px 30px;
            border-style: solid;
            border-color: red;
            /* border: 9px solid red; */
            overflow: auto;
        }
        /* .inner {
            width: 400px;
            height: 400px;
            background-color: #0000FF;
        } */
    </style>
</head>

<body>
    <div class="box">
    </div>
    <script>
        var box = $('.box');
        // 检测盒子的宽高 clientHeight/W 盒子 自身宽高 + padding 内容溢出不算
        console.log('clientWidth==>' + box.clientWidth); //==>200+30+30=260
        console.log('clientHeight==>' + box.clientHeight); //==>200+20+20=240
        // 表示内容区域的左上角相对于整个元素左上角的位置   实际上就是 border 的宽度
        console.log('clientLeft==>' + box.clientLeft); //==>30
        console.log('clientTop==>' + box.clientTop); //==>12
    </script>
</body>

</html>
```
### 获取元素样式
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
        
        .box::before {
            position: absolute;
            display: block;
            bottom: -6px;
            left: -1px;
            width: 102px;
            height: 1px;
            background-color: blue;
            text-align: center;
            content: 'hello world!';
        }
        
        .box {
            position: relative;
            width: 100px;
            height: 100px;
            margin: 50px auto;
            background-color: orange;
            border: 1px solid red;
        }
    </style>
</head>

<body>
    <div class="box">

    </div>
    <script>
        var box = $('.box');
        var result = getComputedStyle(box, '::before').content;
        console.log(result); //==>"hello world!"

        console.log(getStyle(box, 'height')); //==>100px


        // 兼容写法
        // 获取样式的元素   要获取的样式名字
        function getStyle(ele, styleName) {
            if (window.getComputedStyle) {
                return window.getComputedStyle(ele, null)[styleName];
            } else {
                return ele.currentStyle[styleName];
            }
        }
    </script>
</body>

</html>
```
### 多样式的动画封装
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
            position: absolute;
            width: 100px;
            height: 100px;
            background-color: red;
        }
        
        .operate {
            position: absolute;
            top: 200px;
            right: 0;
        }
        
        button {
            padding: 10px 20px;
        }
    </style>
</head>

<body>
    <div class="box"></div>

    <div class="operate">
        <button>宽度变300px,高度变300px,top变 50px,left 100px</button>
        <button>还原</button>
    </div>
    <script src="../my.js"></script>
    <script>
        var box = $('.box');
        var btns = $('button');

        // 需求变多,执行过程极其类似,   用 for 解决  [Array , Object]
        // 起点和终点只要知道,便可执行 for 解决需求   起点 ===> 样式名   终点 ===>  设置 ====>  写成对象的形式
        btns[0].onclick = function() {
            // 声明终点值
            var target = {
                width: 300,
                height: 300,
                top: 50,
                left: 100,
                opacity: .2,
                zIndex: 6
            }
            mulStyle(box, target);
        }
        btns[1].onclick = function() {
            // 声明终点值
            var target = {
                width: 100,
                height: 100,
                top: 0,
                left: 0,
                opacity: 1,
                zIndex: 0
            }
            mulStyle(box, target);
        }

        function mulStyle(ele, target) {
            clearInterval(ele.timer);
            ele.timer = setInterval(function() {
                // 怎样知道都到了终点  给状态 status
                var status = true; // 表示都完成了
                for (var i in target) {
                    // 判断是否是层级
                    if (i === 'zIndex') {
                        ele.style.zIndex = target[i];
                        continue;
                    }
                    // 判断样式是否是透明度
                    if (i === 'opacity') {
                        // 获取起点值*10或100变为整数,最终结果/10或100
                        var start = parseInt(getStyle(ele, i) * 10);
                        // 获取终点值*10或100变为整数
                        var tar = target[i] * 10;
                    } else {
                        // 获取起点值
                        var start = parseInt(getStyle(ele, i));
                        // 获取终点值
                        var tar = target[i];
                    }
                    // 步长
                    var step = (tar - start) / 10;
                    // 步长临界值
                    if (Math.abs(step) < 1) {
                        step = step > 0 ? Math.ceil(step) : Math.floor(step);
                    }
                    // 判断是否到终点,改变status值
                    if (start + step !== tar) {
                        status = false;
                    }
                    // 开始动画
                    // if (i === 'opacity') {
                    //     ele.style[i] = (start + step) / 100;
                    // } else {
                    //     ele.style[i] = start + step + 'px';
                    // }
                    ele.style[i] = i === 'opacity' ? ele.style[i] = (start + step) / 10 : ele.style[i] = start + step + 'px';
                }
                // 判断是否都到了终点
                if (status) {
                    console.log('stop...');
                    clearInterval(ele.timer);
                }
            }, 17)
        }
    </script>
</body>

</html>
```
### 旋转木马
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
        
        ul,
        ol {
            list-style: none;
        }
        
        .swiper {
            position: relative;
            width: 1200px;
            margin: 10px auto;
        }
        
        .swiper ul {
            height: 500px;
        }
        
        li {
            position: absolute;
            /* left: 100px;
				top: 0; */
        }
        
        .swiper li img {
            width: 100%;
        }
        
        .arr {
            position: absolute;
            top: 50%;
            left: 0;
            margin-top: -35px;
            display: block;
            width: 30px;
            height: 70px;
            font-size: 20px;
            color: #fff;
            text-align: center;
            line-height: 70px;
            background-color: rgba(0, 0, 0, .7);
            z-index: 999;
            text-decoration: none;
        }
        
        .arr.arr-r {
            left: auto;
            right: 0;
        }
        
        ul li.li_1 {
            width: 400px;
            top: 70px;
            left: 50px;
            opacity: .2;
            z-index: 2;
        }
        
        ul li.li_2 {
            width: 600px;
            top: 120px;
            left: 0px;
            opacity: .8;
            z-index: 3;
        }
        
        ul li.li_3 {
            width: 800px;
            top: 100px;
            left: 200px;
            opacity: 1;
            z-index: 4;
        }
        
        ul li.li_4 {
            width: 600px;
            top: 120px;
            left: 600px;
            opacity: .8;
            z-index: 3;
        }
        
        ul li.li_5 {
            width: 400px;
            top: 70px;
            left: 750px;
            opacity: .2;
            z-index: 2;
        }
    </style>
</head>

<body>
    <div class="swiper">
        <ul class="pro">
            <li class="li_1">
                <a href="#"><img src="img/m1.jpg" alt="" /></a>
            </li>
            <li class="li_2">
                <a href="#"><img src="img/m2.jpg" alt="" /></a>
            </li>
            <li class="li_3">
                <a href="#"><img src="img/m3.jpg" alt="" /></a>
            </li>
            <li class="li_4">
                <a href="#"><img src="img/m4.jpg" alt="" /></a>
            </li>
            <li class="li_5">
                <a href="#"><img src="img/m5.jpg" alt="" /></a>
            </li>
        </ul>
        <a href="javascript:;" class="arr arr-l">
                &lt;</a>
        <a href="javascript:;" class="arr arr-r">&gt;</a>
    </div>
    <script>
        var arrL = $('.arr-l'),
            arrR = $('.arr-r'),
            lis = $('.pro').children,
            arr = [{ //  0
                width: 400,
                top: 70,
                left: 50,
                opacity: .2,
                zIndex: 2
            }, { // 1
                width: 600,
                top: 120,
                left: 0,
                opacity: .8,
                zIndex: 3
            }, { // 2
                width: 800,
                top: 100,
                left: 200,
                opacity: 1,
                zIndex: 4
            }, { // 3
                width: 600,
                top: 120,
                left: 600,
                opacity: .8,
                zIndex: 3
            }, { //4
                width: 400,
                top: 70,
                left: 750,
                opacity: .2,
                zIndex: 2
            }];
        arrL.onclick = function() {
            arr.unshift(arr.pop());
            for (let i = 0; i < lis.length; i++) {
                mulStyle(lis[i], arr[i]);
            }
        }
        arrR.onclick = function() {
            // arr.push(arr[0]);
            // arr.shift();
            arr.push(arr.shift());
            for (let i = 0; i < lis.length; i++) {
                mulStyle(lis[i], arr[i]);
            }
        }
    </script>
</body>

</html>
```