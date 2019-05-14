## DOM基础-1
### DOM节点
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <script>
        window.onload = function() {
            //根据id获取,id唯一
            var pEl = document.getElementById('p1');
            console.log(pEl);
            //根据class类名
            var boxEl = document.getElementsByClassName('box')[0];
            console.log(boxEl);
            //根据标签名
            var h1El = document.getElementsByTagName('h1')[0];
            console.log(h1El);
        }
    </script>
</head>

<body>
    <h1>不凡学院</h1>
    <p id="p1">今天天气真热</p>
    <div class="box">盒子</div>
</body>

</html>
```
### 获取父节点
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
            width: 300px;
            height: 300px;
            background-color: red;
            display: flex;
            justify-content: center;
            align-items: center;
            left: 50%;
            top: 50%;
            transform: translate(-50%, -50%);
            position: absolute;
        }
        
        .inner-box {
            width: 100px;
            height: 100px;
            background-color: skyblue;
        }
    </style>
</head>

<body>
    <div class="box">
        <div class="inner-box">

        </div>
    </div>
    <script>
        var innerBox = document.getElementsByClassName('inner-box')[0];
        //获取父节点
        var box = innerBox.parentNode;
        console.log(box);

        //点击盒子,修改父盒子的背景色
        innerBox.onclick = function() {
            box.style.backgroundColor = 'blue';
            //background-color  在js 当中 需要改成 驼峰命名 backgroundColor
        }
    </script>
</body>

</html>
```
### 弹出/关闭二维码
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
            position: fixed;
            right: 50px;
            bottom: 100px;
            width: 100px;
            height: 100px;
            background-color: #996655;
            display: flex;
            justify-content: center;
            align-items: center;
        }
        
        .mask {
            display: none;
            position: fixed;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, .9);
            z-index: 5;
        }
        
        img {
            position: absolute;
            left: 50%;
            top: 50%;
            transform: translate(-50%, -50%);
            width: 100px;
        }
    </style>
</head>

<body>
    <div class="box">
        弹出二维码
    </div>
    <div class="mask">
        <img src="img/wx.jpg" alt="">
    </div>
    <script>
        var box = document.getElementsByClassName('box')[0],
            maskEl = document.getElementsByClassName('mask')[0]
        box.onclick = function() {
            maskEl.style.display = 'block';
            this.style.display = 'none';
            // 有new 指向实例对象
            // 没有的话,指向调用
        }
        maskEl.onclick = function() {
            this.style.display = 'none';
            box.style.display = 'flex';
        }
    </script>
</body>

</html>
```
### 兄弟节点
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
        <li class="li1"></li>
        <li class="li2"></li>
        <!-- 注释 -->
        <li class="li3"></li>
        <li class="li4"></li>
    </ul>
    <script>
        var li2 = document.getElementsByClassName('li2')[0];
        // var li2 = document.getElementsByTagName('li')[2];

        // 获取li2 的下一个兄弟节点  nextSibling  包括 文本节点 换行,空格,注释
        console.log(li2.nextSibling); //嫡出
        // nextElementSibling 下一个元素节点(标签)
        console.log(li2.nextElementSibling); //庶出
        //在 ie 678 里边 nextSibling  IE678中指下一个元素节点 (（标签、注释）)
        //兼容写法
        var nextEl = li2.nextElementSibling || li2.nextSibling;

        // 上一个 兄弟节点 
        // previousSibling
        // previousElementSibling
        var preEl = li2.previousElementSibling || li2.previousSibling;
        console.log(preEl);
    </script>
</body>

</html>
```
### 单个孩子节点
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
        <li class="li1"></li>
        <li class="li2"></li>
        <!-- 注释 -->
        <li class="li3"></li>
        <li class="li4"></li>
    </ul>
    <script>
        var ulEl = document.getElementsByTagName('ul')[0];
        console.log(ulEl.firstChild); //文本节点
        console.log(ulEl.firstElementChild); //==><li class="li1"></li>

        console.log(ulEl.lastChild); //文本节点
        console.log(ulEl.lastElementChild); //==><li class="li4"></li>

        //兼容写法
        console.log(ulEl.firstElementChild || ulEl.firstChild);
    </script>
</body>

</html>
```
### 所有孩子节点
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
        <li class="li1"></li>
        <li class="li2"></li>
        <!-- 注释 -->
        <li class="li3"></li>
        <li class="li4"></li>
    </ul>
    <script>
        var ulEl = document.getElementsByTagName('ul')[0];
        // 所有孩子节点  childNodes 嫡出  包括文本 注释
        // children 庶出 不考虑 ie5678
        console.log(ulEl.childNodes); //包括文本注释
        console.log(ulEl.children); // 所有元素节点

        var myChildren = ulEl.childNodes;
        // nodeType    1 标签节点
        //             3 文本节点
        //             8 注释节点
        var childrenArr = [];
        for (let i = 0; i < myChildren.length; i++) {
            if (myChildren[i].nodeType === 1) {
                childrenArr.push(myChildren[i]);
            }
        }
        console.log(childrenArr);
    </script>
</body>

</html>
```
### 求除了自己以外的兄弟节点
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
        <li class="li1"></li>
        <li class="li2"></li>
        <!-- 注释 -->
        <li class="li3"></li>
        <li class="li4"></li>
    </ul>
</body>

</html>
```
1. 遍历所有li节点,去掉 他自己
```javascript
var li2 = document.getElementsByClassName('li2')[0];
console.log(getSiblings(li2));

function getSiblings(el) {
    var siblings = [],
        pNode = el.parentNode,
        children = pNode.children;
    for (let i = 0; i < children.length; i++) {
        //兼容IE8
        if (children[i].nodeType === 1) {
            if (children[i] !== el) {
                siblings.push(children[i]);
            }
        }

    }
    return siblings;
}
```
2. 找到 前边的所有兄弟节点,找到后边的所有兄弟及节点,合并
```javascript
function getPrevSiblings(el) {
    var rs = [];
    pNode = el.parentNode,
        children = pNode.children;
    for (let i = 0; i < children.length; i++) {
        if (children[i].nodeType === 1) {
            if (children[i] !== el) {
                rs.push(children[i]);
            } else {
                break;
            }
        }

    }
    return rs;
}
console.log(getPrevSiblings(li2));
// 获取后边的所有兄弟节点
// 1. 倒着遍历
// 2. lock 上锁
function getNextSiblings(el) {
    var rs = [];
    pNode = el.parentNode,
        // 所有孩子节点
        children = pNode.children,
        lock = false;
    for (let i = 0; i < children.length; i++) {
        if (children[i] == el) {
            lock = true;
            continue;
        }
        if (lock) {
            if (children[i].nodeType === 1) {
                rs.push(children[i]);
            }
        }
    }
    return rs;
}

function getNextSiblings2(el) {
    var nextArr = getNextSiblings(el),
        preArr = getPrevSiblings(el),
        rs = [];
    rs = preArr.concat(nextArr);
    return rs;
}
console.log(getNextSiblings2(li2));
```
### 节点的操作
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
    <!-- curd 增删改查 -->
    <!-- c create
    u update
    r read
    d delete -->
    <div class="box">
        <h1>不烦学院</h1>
    </div>
    <button>删除img</button>
    <button>克隆box</button>

    <script>
        var boxEl = document.getElementsByClassName('box')[0],
            btn1 = document.getElementsByTagName('button')[0],
            btn2 = document.getElementsByTagName('button')[1],
            //创建节点
            pEl = document.createElement('p'),
            imgEl = document.createElement('img');
        pEl.innerText = '天气真热';
        imgEl.src = 'img/钢铁侠.jpg';
        // 不插入节点 ,是不会在页面当中显示的
        // 父节点.appendChild();
        // 父节点.insertBefore(要插入的节点，参考节点)；
        boxEl.appendChild(pEl);
        // boxEl.appendChild(pEl);
        // 同一个 节点 不能重复插入
        boxEl.insertBefore(imgEl, pEl);
        // 如果参考节点为null，那么他将在节点最后插入一个节点。

        // 删除节点  父节点.removeChild（子节点）。
        btn1.onclick = function() {
                boxEl.removeChild(imgEl);
            }
            // 不知道父级的情况下，可以这么写：node.parentNode.removeChild(node)

        // 复制节点 oldNode.cloneNode（true） 
        // 参数 true，深层复制，如果是false，只复制节点本身。
        btn2.onclick = function() {
            var cloneNode = boxEl.cloneNode(true);
            var scriptEl = document.getElementsByTagName('script')[0];
            // document.body.appendChild(cloneNode);
            document.body.insertBefore(cloneNode, scriptEl);
        }
    </script>
</body>

</html>
```
### 节点属性操作
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        .danger {
            color: maroon;
        }
    </style>
</head>

<body>
    <h1 class="title h1 danger" id="title1">不凡学院</h1>
    <h2 class="h2">前端开发</h2>
    <button class="btn">删除danger样式</button>
    <script>
        var h1 = document.getElementById('title1'),
            h2 = document.getElementsByClassName('h2')[0],
            btn = document.getElementsByClassName('btn')[0];
        h2.onclick = function() {
            // h2.style.color = 'maroon';
            // 但是 我们很少在 js 当中设置css样式
            // 通常使用class控制样式的变化
            // 重新设class
            h2.setAttribute('class', 'danger');
        }
        h1.onclick = function() {
            //获取类名
            console.log(h1.getAttribute('class')); //==>title h1 danger
            console.log(h1.getAttribute('id')); //==>title1
        }
        btn.onclick = function() {
            //删除
            h1.removeAttribute('class');
        }
    </script>
</body>

</html>
```
### 内容操作
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
    <input type="text">
    <button>给input 添加value</button>
    <hr>
    <p class="p1"></p>
    <button class="btn2">给p标签添加text||innerText</button>
    <button class="btn3">给p标签添加text||textContent</button>
    <hr>
    <div class="box">
        <img src="img/fbb.jpg" alt="">
    </div>
    <button class="btn4">给box插入html || innerHTML</button>
    <script>
        var input = document.getElementsByTagName('input')[0],
            btn = document.getElementsByTagName('button')[0],
            p1 = document.getElementsByClassName('p1')[0],
            btn2 = document.getElementsByClassName('btn2')[0],
            btn3 = document.getElementsByClassName('btn3')[0],
            btn4 = document.getElementsByClassName('btn4')[0],
            box = document.getElementsByClassName('box')[0],
            text = '今天天气不错',
            htmlStr = '<h1>hello world!<h1>';
        btn.onclick = function() {
            input.value = Math.floor(Math.random() * 10);
        }
        btn2.onclick = function() {
            p1.innerText = htmlStr;
            // p1.innerText = text;==>覆盖之前
            // innerText 插入文本内容，标签和样式会被当做文本内容处理。
            // 每一次innerHTML/innerText 会覆盖之前的
        }
        btn3.onclick = function() {
            p1.textContent = htmlStr;
        }
        btn4.onclick = function() {
            // box.innerText = text;
            box.innerHTML = htmlStr;
            // 每一次innerHTML/innerText 会覆盖之前的
        }
    </script>
</body>

</html>
```
### 切换图片
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
    <img src="img/fbb.jpg" alt="">
    <script>
        var imgUrl = ['m1.jpg', 'm2.jpg', 'm3.jpg', 'm4.jpg'],
            img = document.getElementsByTagName('img')[0];
        img.onclick = function() {
            img.src = 'img/' + imgUrl[Math.floor(Math.random() * 4)];
        }
    </script>
</body>

</html>
```
### 相册走廊
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
            width: 100%;
        }
        
        ul {
            margin: 0 auto;
            width: 400px;
            list-style: none;
        }
        
        .img-item {
            float: left;
        }
        
        .img-item img {
            width: 100px;
        }
    </style>
</head>

<body>
    <img src="img/m1.jpg" alt="">

    <ul>
        <li class="img-item">
            <img src="img/m1.jpg" alt="">
        </li>
        <li class="img-item">
            <img src="img/m2.jpg" alt="">
        </li>
        <li class="img-item">
            <img src="img/m3.jpg" alt="">
        </li>
        <li class="img-item">
            <img src="img/m4.jpg" alt="">
        </li>
    </ul>
    <script>
        var imgEl = document.getElementsByTagName('img')[0],
            lis = document.getElementsByClassName('img-item');
        console.log(lis);
        for (var i = 0; i < lis.length; i++) {
            lis[i].onclick = function() {
                // 获取imgUrl
                // 这个地方不能用lis[i],只能用this
                var imgUrl = this.children[0].src;
                console.log(imgUrl);
                imgEl.src = imgUrl;
                console.log(i); //==>4
            }
        }
        //let声明
        // for (let i = 0; i < lis.length; i++) {
        //     lis[i].onclick = function() {
        //         // 获取imgUrl
        //         // 这个地方能用lis[i],也能用this
        //         var imgUrl = lis[i].children[0].src;
        //         console.log(imgUrl);
        //         imgEl.src = imgUrl;
        //         console.log(i); //==>0/1/2/3
        //     }
        // }
    </script>
</body>

</html>
```
### banner切换
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
        
        .banner {
            position: relative;
            width: 100%;
        }
        
        .banner .ban {
            width: 100%;
        }
        /*小圆点*/
        
        .banner .dots {
            /* width: 150px;
            height: 14px; */
            left: 50%;
            transform: translateX(-50%);
            position: absolute;
            bottom: 16px;
        }
        
        .banner .dot {
            float: left;
            width: 8px;
            height: 8px;
            border-radius: 50%;
            border: 3px solid transparent;
            margin-right: 16px;
            background: white;
            -webkit-background-clip: content-box;
            -moz-background-clip: content-box;
            background-clip: content-box;
            cursor: pointer;
        }
        
        .banner .dots .dot-items {
            list-style: none;
        }
        
        .banner .dot:hover {
            border-color: white;
            background: #668aca;
        }
        
        .banner .dots .active {
            border-color: white;
            background: #668aca;
        }
    </style>
</head>

<body>
    <div class="banner">
        <!-- 图片 -->
        <img src="img/m1.jpg" alt="" class="ban">
        <!-- 小圆点 -->
        <div class="dots">
            <ul class="dot-items">
                <li class="dot active"></li>
                <li class="dot"></li>
                <li class="dot"></li>
                <li class="dot"></li>
                <li class="dot"></li>
            </ul>
        </div>
    </div>
    <script>
        var imgUrl = ['m1.jpg', 'm2.jpg', 'm3.jpg', 'm4.jpg', 'm5.jpg'],
            img = document.getElementsByTagName('img')[0],
            lis = document.getElementsByClassName('dot');
        for (let i = 0; i < lis.length; i++) {
            lis[i].onclick = function() {
                img.src = 'img/' + imgUrl[i];
                console.log(i);
            }
        }
    </script>
</body>

</html>
```