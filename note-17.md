## jQuery-1
### 简单理解闭包
```javascript
// 在foo函数 外部 ,调用到了foo函数的内部变量
var a = 10;

function foo() {
    var a = 2;
    return function() {
        console.log(a);
    }
}
console.log(a); //10
var b = foo();
// b ==>  function (){
// console.log(a);
// }
b(); //2
```
### jQuery引入
+ 快速简单的操作dom元素
+ 封装JavaScript常用的功能代码
+ 用jQuery之前，先引入jQuery，然后，再去写我们的jQuery代码。
+ 如果使用了第三方jquery插件（日历、滚动、瀑布流等），必须先引入jquery，再引入该插件
+ $ 就是 jQuery ,jQuery简写就是$
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <script src="../lib/jquery-3.4.1.min.js"></script>
    <title>Document</title>
    <script>
        // window.onload=function(){
        //     alert('abc');
        // }
        $(document).ready(function() {
            alert('abc');
        })
    </script>
    <script>
        // 事件有个事件覆盖的问题，我们只能写一个
        // window.onload = function(){
        //     alert('edf');
        // }

        // jQuery不存在覆盖问题
        // $(document).ready(function() {
        //     alert('sda');
        // })
        // 简写
        // $(function() {
        //     alert('sda');
        // })
        //或者
        jQuery(function() {
                alert('sda')
            })
            // $(function () {});推荐
    </script>
</head>

<body>

</body>

</html>
```
### jQuery操作dom
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <script src="../lib/jquery-3.4.1.min.js"></script>
    <title>Document</title>
</head>

<body>
    <div class="d1">
        <div class="p1">
            不烦学院
        </div>
    </div>
    <div class="p1">
        天气很好
    </div>
    <script>
        // 获取事件源
        // var pEl = document.getElementsByClassName('p1')[0];
        // pEl.onclick = function(){
        //     this.style.color = 'red';
        // }
        var $pEl = $('.p1');
        // $pEl  jq对象
        console.log($pEl);
        $pEl.click(function() {
            // 不能使用this
            // this指向会发生变化
            // 在回调函数里边  慎用 this
            $pEl.css('color', 'red');
        })
    </script>
</body>

</html>
```
### 获取事件源-基本选择器
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <script src="../lib/jquery-3.4.1.min.js"></script>
    <title>Document</title>
</head>

<body>
    <!-- css选择器
    id
    class
    标签
    交集
    并集
    后代 -->
    <div id="d1" class="d1">
        <div class="p1">
            不烦学院
        </div>
    </div>
    <div class="d2">
        <div class="p1">
            不烦学院
        </div>
    </div>

    <div class="d3 active">
        <div class="box">
            我是box
            <div class="box2">

            </div>
        </div>
    </div>

    <h2>天气很好</h2>
    <h2>不烦学院</h2>
    <script>
        //通过标签选择器
        $('h2').css('color', 'red');
        //通过class选择器
        $('.p1').css('color', 'blue');
        //通过id选择器
        $('#d1').css('background-color', 'pink');
        //后代选择器
        $('.d3 .box').css('color', 'orange');
        //并集选择器
        $('.d2,.d3').css('background-color', 'black');
        //交集选择器
        $('.d3.active').css('background-color', 'skyblue');
    </script>
</body>

</html>
```
### 层级选择器
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <script src="../lib/jquery-3.4.1.min.js"></script>
    <title>Document</title>
    <style>
        .li3 {
            color: brown;
        }

        /* + 选择紧挨着的下一个元素 */
        .li3+li {
            color: aqua;
        }

        /* 后面的所有兄弟元素 */
        .li3~li {
            background-color: burlywood;
        }
        
        .d1 .box1 {
            width: 200px;
            height: 200px;
            background-color: red;
        }
        
        .d1 .box2 {
            width: 100px;
            height: 100px;
            background-color: green;
        }

        /* 子代选择器,直接孩子,不管孙子 */
        .d1>.box {
            width: 300px;
        }
    </style>
</head>

<body>
    <!-- 层级选择器 css当中也可以使用 -->
    <ul>
        <li>li_1</li>
        <li>li_2</li>
        <li class="li3">li_3</li>
        <li>li_4</li>
        <li>li_5</li>
    </ul>
    <div class="d1">
        <div class="box box1">
            我是box
            <div class="box box2">
                我是box2
            </div>
        </div>
    </div>
    <script>
        $('.li3+li').css('color', 'red');
        $('.li3~li').css('background-color', 'deeppink');
        $('.d1>.box').css('width', '800px');
    </script>

</body>

</html>
```
### 过滤选择器
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <script src="../lib/jquery-3.4.1.min.js"></script>
    <title>Document</title>
</head>

<body>
    <ul>
        <li>li-1</li>
        <li>li-2</li>
        <li>li-3</li>
        <li>li-4</li>
        <li class="li5">li-5</li>
        <li>li-6</li>
        <li>li-7</li>
        <li>li-8</li>
        <li>li-9</li>
        <li>li-10</li>
    </ul>
    <script>
        $('li:eq(1)').css('background', 'red');
        $('li:eq(0)').css('background', 'red');
        //选择序号大于index的元素
        $('li:gt(5)').css('background', 'red');
        //选择序号小于index的元素
        $('li:lt(5)').css('background', 'blue');
        //index为奇数
        $('li:odd').css('background', 'orange');
        //为偶数
        $('li:even').css('background', 'red');
        //第一个元素
        $('li:first').css('background', 'pink');
        //最后一个元素
        $('li:last').css('background', 'pink');
    </script>
</body>

</html>
```
### 属性选择器
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <script src="../lib/jquery-3.4.1.min.js"></script>
    <title>Document</title>
</head>

<body>
    <p class="p1" title="我是标题">不烦学院</p>
    <p title="我是标a题h">不烦学院</p>

    <p>天气很好</p>
    <script>
        $('p[title]').css('color', 'red');
        $('p[title="我是标题"]').css('color', 'blue');
        $('p[title!="我是标题"]').css('color', 'blue');
        $('p[title^="我是标题"]').css('color', 'red');
        $('p[title$="h"]').css('color', 'orange');
        $('p[title*="a"]').css('color', 'red');
        $('p[class][title="我是标题"]').css('color', 'blue');
    </script>
</body>

</html>
```
### 筛选(关系查找)
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <script src="../lib/jquery-3.4.1.min.js"></script>
    <title>Document</title>
</head>

<body>
    <ul>
        <li>li-1</li>
        <li>li-2</li>
        <li>li-3</li>
        <li class="li3">li-4</li>
        <li>li-5</li>
        <li>li-6</li>
        <li>li-7</li>
        <li>li-8</li>
        <li>li-9</li>
        <li>li-10</li>
    </ul>
    <div class="box">
        <div class="d1">
            我是d1
            <div class="d2">
                我是d2
            </div>
        </div>
        <p class="p1">
            我是p1
        </p>
    </div>
    <script>
        // 查找指定元素的所有后代元素（子子孙孙） find(selector)
        $('.box').find('*').css('color', 'red'); //所有后代元素
        $('.box').find('div').css('color', 'blue'); //所有标签为div的后代元素

        // 查找指定元素的直接子元素（亲儿子元素） children()
        $('.box').children().css('color', 'orange'); //所有直接子元素
        $('.box').children('p').css('color', 'blue'); //所有标签为p的直接子元素

        // 查找所有兄弟元素（不包括自己）
        $('.li3').siblings().css('color', 'red');

        // 查找父元素（亲的） parent()
        $('.d2').parent().css('width', '200px');
        //查找元素第index个元素,初始值为0
        $('li').eq(5).css('color', 'green');
    </script>
</body>

</html>
```
### 变色
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <script src="../lib/jquery-3.4.1.min.js"></script>
    <title>Document</title>
    <style>
        ul {
            list-style: none;
        }
        
        ul li {
            width: 200px;
            height: 50px;
            background-color: pink;
            margin-top: 10px;
        }
        
        ul li a {
            display: block;
            width: 50px;
            height: 30px;
            background-color: orange;
        }
    </style>
</head>

<body>
    <ul>
        <li><a href="#">li_1</a></li>
        <li><a href="#">li_1</a></li>
        <li><a href="#">li_4</a></li>
        <li><a href="#">li_3</a></li>
        <li><a href="#">li_2</a></li>
        <li><a href="#">li_1</a></li>
    </ul>
    <script>
        var colorBefore = '';
        //鼠标进入
        $('li').mouseenter(function() {
                //获取之前的颜色
                colorBefore = $(this).css('background-color');
                //this指的是当前dom元素对象
                // this.style.backgroundColor = 'red';
                //jq对象采用css()设置样式
                //将dom元素对象转换为jq对象
                $(this).css('background-color', 'red');
            })
            //鼠标离开
        $('li').mouseleave(function() {
            $('li').css('background-color', colorBefore);
        })

        // mouseover 和 mouseenter  区别
        // 在li的后代元素当中 来回进入 离开 会不断触发事件
        // $('li').mouseover(function() {
        //     // 获取之前的颜色
        //     console.log(1);
        //     colorBefore = $(this).css('background-color');
        //     // this指的是当前dom元素对象
        //     // this.style.backgroundColor = 'red';
        //     // jq对象采用.css()设置样式
        //     // 将dom元素对象 转换为 jq对象 
        //     $(this).css('background-color', 'red');
        // });
        // // 鼠标离开
        // $('li').mouseout(function() {
        //     $(this).css('background-color', colorBefore);
        // })
    </script>
</body>

</html>
```
### DOM对象和jQ对象的转换
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <script src="../lib/jquery-3.4.1.min.js"></script>
    <title>Document</title>
</head>

<body>
    <div class="box">
        <div class="inner-box">

        </div>
    </div>
    <div class="box">

    </div>
    <script>
        var boxEl = document.getElementsByClassName('box')[0];
        var $boxEl = $('.box');
        console.log(boxEl);
        console.log($boxEl);

        //jQuery对象转换为dom对象
        console.log($boxEl[0]);
        console.log($boxEl[1]);
        console.log($boxEl.get(1));

        //dom转换为jQuery对象
        console.log($(boxEl));
    </script>
</body>

</html>
```
### 练习
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <script src="js/data.js"></script>
    <script src="../lib/jquery-3.4.1.min.js"></script>
    <title>Document</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        
        .box {
            width: 300px;
            height: 250px;
            position: absolute;
            left: 50%;
            top: 50%;
            transform: translate(-50%, -50%);
            border-bottom: 1px solid pink;
            cursor: pointer;
        }
        
        ul {
            list-style: none;
            float: left;
            height: 100%;
            display: flex;
            flex-direction: column;
        }
        
        ul li {
            flex: 1;
            border: 1px solid pink;
            border-bottom: 0;
            font-size: 12px;
            display: flex;
            justify-content: center;
            align-items: center;
            width: 48px;
            background: url(img/lili.jpg);
        }
        
        ul li:hover {
            background: url(img/abg.gif);
        }
        
        .center {
            float: left;
        }
        
        .center img {
            border-top: 1px solid pink;
        }
    </style>
</head>

<body>
    <div class="box">
        <ul class="l">
            <!-- <li class="left">你好啊</li> -->
        </ul>
        <div class="center">
            <img src="img/冬裙.jpg" alt="">
        </div>
        <ul class="r">
            <!-- <li class="right">你好啊</li> -->
        </ul>
    </div>
    <script>
        initPro($('.l'), data[0]);
        initPro($('.r'), data[1]);
        img($('.left'), data[0]);
        img($('.right'), data[1]);

        function initPro($el, arr) {
            var str = '';
            for (let i = 0; i < arr.length; i++) {
                str += '<li id="li-' + i + '" class="left">' + arr[i].title + '</li>';
            }
            $el[0].innerHTML = str;
        }

        function img($el, arr) {
            $el.mouseenter(function() {
                var index = this.id.split('-')[1];
                $('img')[0].src = arr[index].img;
            })
        }
    </script>
</body>

</html>
```
data.js
```javascript
data = [
    [{
        title: '女靴',
        img: 'img/女靴.jpg'
    },
    {
        title: '雪地靴',
        img: 'img/雪地靴.jpg'
    },
    {
        title: '冬裙',
        img: 'img/冬裙.jpg'
    },
    {
        title: '呢大衣',
        img: 'img/呢大衣.jpg'
    },
    {
        title: '毛衣',
        img: 'img/毛衣.jpg'
    },
    {
        title: '棉服',
        img: 'img/棉服.jpg'
    },
    {
        title: '女裤',
        img: 'img/女裤.jpg'
    },
    {
        title: '羽绒服',
        img: 'img/羽绒服.jpg'
    },
    {
        title: '牛仔裤',
        img: 'img/牛仔裤.jpg'
    }],
    [{
        title: '女包',
        img: 'img/女包.jpg'
    },
    {
        title: '男包',
        img: 'img/男包.jpg'
    },
    {
        title: '登山鞋',
        img: 'img/登山鞋.jpg'
    },
    {
        title: '皮带',
        img: 'img/皮带.jpg'
    },
    {
        title: '围巾',
        img: 'img/围巾.jpg'
    },
    {
        title: '皮衣',
        img: 'img/皮衣.jpg'
    },
    {
        title: '男毛衣',
        img: 'img/男毛衣.jpg'
    },
    {
        title: '男棉衣',
        img: 'img/男棉衣.jpg'
    },
    {
        title: '男靴',
        img: 'img/男靴.jpg'
    }]
]
```
