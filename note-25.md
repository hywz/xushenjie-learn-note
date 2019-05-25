## BOM-4
### 柱状图排序
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
        
        .box {
            position: relative;
            width: 950px;
            height: 330px;
            margin: 20px auto;
            border: 1px solid red;
            list-style: none;
        }
        
        li {
            position: absolute;
            bottom: 0;
            width: 50px;
            /* height: 60px; */
            background-color: #16c116;
        }
        
        button {
            margin-left: 50px;
            width: 100px;
            height: 30px;
        }
        
        .active {
            background-color: brown;
        }
        
        .done {
            background-color: #008000;
        }
    </style>
</head>

<body>
    <ul class="box"></ul>
    <button>生成柱状图</button>
    <button>开始排序</button>
    <script>
        var box = $('.box'),
            btns = $('button'),
            timer = null;

        // 点击生成柱状图
        btns[0].onclick = function() {
            clearInterval(timer);
            // 字符串拼接 innerHTML 网页面中添加li
            var str = '',
                l = 0,
                // 高度去重
                hArr = [];
            for (let i = 0; i < 10; i++) {
                // 高度 [10-330]
                // h = Math.floor(Math.random() * 320) + 10;
                h = Math.floor(Math.random() * 32) * 10 + 10;
                if (hArr.indexOf(h) === -1) {
                    hArr.push(h);
                } else {
                    i--;
                }
            }
            for (let i = 0; i < hArr.length; i++) {
                // 左边距 left 值
                l = 40 + 90 * i;
                str += '<li style="left: ' + l + 'px;height: ' + hArr[i] + 'px"></li>';
            }
            box.innerHTML = str;
        }
        var lis = box.children;
        // 排序上线了
        btns[1].onclick = function() {
            // for(var j = 0; j < lis.length - 1; j ++){
            // 	for(var i = 0; i < lis.length - 1 - j; i ++){
            // 		if(lis[i].offsetHeight > lis[i+1].offsetHeight){
            // 			// parentNode.insertBefore(要插入的节点,参考节点)
            // 			lis[i].parentNode.insertBefore(lis[i+1],lis[i]);
            // 			var temp = lis[i+1].offsetLeft;
            // 			// lis[i+1].style.left = lis[i].offsetLeft + "px";
            // 			// lis[i].style.left = temp + "px";
            // 			// 添加动画
            // 			slowly(lis[i+1],lis[i].offsetLeft);
            // 			slowly(lis[i],temp);
            // 		}
            // 	}	
            // }
            var i = 0; // 内环 i	控制每一圈的下标
            var j = 0; // 外环 j	控制圈数
            clearInterval(timer);
            timer = setInterval(function() {
                // parentNode.insertBefore(要插入的节点,参考节点)
                if (lis[i].offsetHeight > lis[i + 1].offsetHeight) {
                    lis[i].parentNode.insertBefore(lis[i + 1], lis[i]);
                    var temp = lis[i + 1].offsetLeft;
                    // lis[i+1].style.left=lis[i].offsetLeft+'px';
                    // lis[i].style.left=temp+'px';
                    slow(lis[i + 1], lis[i].offsetLeft);
                    slow(lis[i], temp);
                }
                i++;
                if (i === lis.length - 1 - j) {
                    addClass(lis[i], 'done');
                    j++;
                    i = 0;
                }
                if (j === lis.length - 1) {
                    console.log('stop...')
                    clearInterval(timer);
                    //添加最后一个done类
                    addClass(lis[0], 'done');
                }
            }, 600)
        }

        function slow(ele, target) {
            var start, step;
            clearInterval(ele.timer);
            addClass(ele, "active");
            ele.timer = setInterval(function() {
                // 起点
                start = ele.offsetLeft;
                // 步长
                step = (target - start) / 10;
                // 判断步长临界值 (-1,1)
                if (Math.abs(step) < 1) {
                    // 细分区间 (-1,0)  (0,1)
                    step = step > 0 ? Math.ceil(step) : Math.floor(step);
                }
                // 判断终止条件
                if (start + step === target) {
                    removeClass(ele, "active");
                    clearInterval(ele.timer);
                }
                // 运动
                ele.style.left = start + step + "px";
            }, 17)
        }
    </script>
</body>

</html>
```
### 函数回顾
```js
//冒泡排序:
var arr = [5, 4, 3, 2];

function bubble(arr) {
    for (let i = 0; i < arr.length - 1; i++) {
        for (let j = 0; j < arr.length - 1 - i; j++) {
            if (arr[j] > arr[j + 1]) {
                var temp = arr[j + 1];
                arr[j + 1] = arr[j];
                arr[j] = temp;
            }

        }
        return arr;
    }
}
// console.log(bubble(arr));

//选择排序:
function select(arr) {
    for (let i = 0; i < arr.length - 1; i++) {
        var minIndex = i;
        for (let j = i + 1; j < arr.length; j++) {
            minIndex = arr[minIndex] > arr[j] ? j : minIndex;
        }
        var temp = arr[i];
        arr[i] = arr[minIndex];
        arr[minIndex] = temp;
    }
    return arr;
}
// console.log(select(arr));

//添加类名:
function addClass(ele) {
    var old = ele.getAttribute('class');
    if (old) {
        for (let i = 1; i < arguments.length; i++) {
            if (old.indexOf(arguments[i]) === -1) {
                old += ' ' + arguments[i];
            }
        }
        ele.setAttribute('class', old);
    } else {
        var str = '';
        for (let i = 1; i < arguments.length; i++) {
            str += arguments[i] + ' ';
        }
        str = str.slice(0, atr.length - 1);
        ele.setAttribute('class', str);
    }
}

//删除类名:
function delClass(ele) {
    var old = ele.getAttribute('class');
    if (old) {
        var oldArr = old.split(' ');
        for (let i = 1; i < arguments.length; i++) {
            if (oldArr.indexOf(arguments[i]) !== -1) {
                oldArr.splice(oldArr.indexOf(arguments[i]), 1)
            }
        }
        ele.setAttribute('class', oldArr.join(' '));
    }
}

//缓动动画
function slowly(ele, target) {
    var start, step;
    clearInterval(ele.timer);
    ele.timer = setInterval(function() {
        start = ele.offsetLeft;
        step = (target - start) / 10;
        if (Math.abs(step) < 1) {
            step = step > 0 ? Math.ceil(step) : Math.floor(step);
        }
        if (start + step == target) {
            clearInterval(ele.timer);
        }
        ele.style.left = start + step + 'px';
    }, 17)
}

//多样式缓动动画 参数target为一个包含了多种样式键值的对象
function mulStyle(ele, target) {
    var start, step, t;
    clearInterval(ele.timer);
    ele.timer = setInterval(function() {
        var status = true;
        for (const i in target) {
            if (i === 'zIndex') {
                ele.style[i] = target[i];
                continue;
            }
            if (i === 'opacity') {
                start = parseInt(getStyle(ele, i) * 100);
                t = target[i] * 100;
            } else {
                start = parseInt(getStyle(ele, i));
                t = target[i];
            }
            step = (t - start) / 10;
            if (Math.abs(step) < 1) {
                step = step > 0 ? Math.ceil(step) : Math.floor(step);
            }
            if (i === 'opacity') {
                ele.style[i] = (start + step) / 100;
            }
            ele.style[i] = start + step + 'px';
            if (start + step !== t) {
                status = false;
            }
        }
        if (status) {
            clearInterval(ele.timer);
        }
    }, 17)
}

//获取样式值
function getStyle(ele, styleName) {
    if (ele.currentStyle) {
        return ele.currentStyle[styleName];
    } else {
        return window.getComputedStyle(ele, null)[styleName];
    }
}

//阶乘
function jc(num) {
    if (num === 1) {
        return 1;
    }
    // return num*jc(num-1);
    return num * arguments.callee(num - 1);
}
console.log(jc(3));

//斐波那契函数
function fb(num) {
    if (num === 1 || num === 2) {
        return 1;
    }
    // return fb(num-1)+fb(num-2);
    return arguments.callee(num - 1) + arguments.callee(num - 2);
}
console.log(fb(5));
```
### 自动轮播
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
        var timer = null;
        autoPlay();

        function autoPlay() {
            timer = setInterval(function() {
                btns[1].onclick();
            }, 1000)
        }
        ele.onmouseenter = function() {
            clearInterval(timer);
            // 放上 停止
        }
        ele.onmouseleave = function() {
            autoPlay();
            // 离开执行
        }
    </script>
</body>

</html>
```