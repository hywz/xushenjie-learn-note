## DOM基础-2
### 相册走廊的优化
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
            left: 50%;
            transform: translateX(-50%);
            position: absolute;
            list-style: none;
        }
        
        .img-item {
            float: left;
        }
        
        .img-item img {
            width: 100px;
        }
        
        .img-item.active {
            border: 1px solid skyblue;
        }
    </style>
</head>

<body>
    <img src="img/m1.jpg" alt="">

    <ul>
        <li class="img-item active">
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
    <script src="js/util.js"></script>
    <script>
        var imgEl = document.getElementsByTagName('img')[0],
            lis = document.getElementsByClassName('img-item');
        for (var i = 0; i < lis.length; i++) {
            lis[i].onclick = function() {
                // 获取imgUrl
                // 这个地方不能用lis[i],只能用this
                var imgUrl = this.children[0].src;
                // console.log(imgUrl);
                imgEl.src = imgUrl;
                // 排他思想 先全删除
                for (var j = 0; j < lis.length; j++) {
                    delClass(lis[j], 'active')
                        // 去掉所用li的  active
                }
                // 给当前惦记的li 添加active
                addClass(this, 'active');
            }
        }
    </script>
</body>

</html>
```
### 封装添加删除class类名
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
            color: red;
        }
        
        .strong {
            font-weight: bolder;
        }
    </style>
</head>

<body>
    <p id="p2" class="strong danger">不烦学院</p>
    <p id="p1">欢迎来到不凡学院</p>
    <button class="btn1">添加danger</button>
    <button class="btn2">添加strong</button>
    <button class="btn3">删除danger</button>
    <script src="js/util.js"></script>
    <script>
        var btn1 = document.getElementsByClassName('btn1')[0],
            btn2 = document.getElementsByClassName('btn2')[0],
            btn3 = document.getElementsByClassName('btn3')[0],
            p1 = document.getElementById('p1');
        btn1.onclick = function() {
            addClass(p1, 'danger');
        }
        btn2.onclick = function() {
            addClass(p1, 'strong');
        }
        btn3.onclick = function() {
            delClass(p1, 'danger');
        }
    </script>
</body>

</html>
```
until.js如下
```javascript
function addClass(el, className) {
    var oldClassStr = '';
    // 给表添加属性 添加之前应该先合并之前的class
    //假如有class属性
    // 0 '' null  undefined false  ==> 在if()语句中都是false
    if (el.getAttribute('class')) {
        oldClassStr = el.getAttribute('class');
        var oldClassArr = oldClassStr.split(' ');
        if (oldClassArr.indexOf(className) == -1) {
            oldClassStr += ' ';
        } else { return; }
    }
    //追加
    oldClassStr += className;
    el.setAttribute('class', oldClassStr);
}

function delClass(el, className) {
    var oldClassStr = el.getAttribute('class'),
        oldClassArr = oldClassStr.split(' '),
        index = oldClassArr.indexOf(className);
    if (index !== -1) {
        //如果类名中存在className,则删除
        oldClassArr.splice(index, 1);
        oldClassStr = oldClassArr.join(' ');
        el.setAttribute('class', oldClassStr);
    }
}
```
