## jQuery-2
### css设置
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
        .box {
            width: 100px;
            height: 100px;
            background-color: red;
            font-size: 20px;
        }
    </style>
</head>

<body>
    <div class="box">
        不凡学院
    </div>
    <script>
        //设置样式
        $('.box').css('width', '200px');
        $('.box').css('fontSize', '30px');
        //获取样式
        console.log($('.box').css('height'));
        //设置多个样式
        $('.box').css({
            width: '300px',
            height: '400px',
            backgroundColor: 'green'
        })
    </script>

</body>

</html>
```

### attr属性
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
        .box {
            width: 100px;
            height: 100px;
            background-color: red;
            font-size: 12px;
        }
    </style>
</head>

<body>
    <div class="box active">
        不凡学院
    </div>
</body>
</html>
```
1. 获取属性
    ```javascript
    console.log($('.box').attr('class')); 
    // getAttribute()
    ```
2. 设置属性
    ```javascript
    $('.box').attr('class', 'danger'); //setAttribute()覆盖之前
    ```
3. 移除属性
    ```javascript
    $('div').removeAttr('class');
    $('div').click(function() {
            if ($('div').attr('title')) {
                $('div').removeAttr('title');
            } else {
                $('div').attr('title', '天气很好');
            }
        })
    ```
### 取值设置
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
        .box {
            width: 100px;
            height: 100px;
            background-color: red;
            font-size: 12px;
        }
    </style>
</head>

<body>
    <div class="box active">
        不凡学院
    </div>
    <ul>
        <li>li_1</li>
        <li>li_2</li>
        <li>li_3</li>
        <li>li_4</li>
        <li>li_5</li>
        <li>li_6</li>
        <li>li_7</li>
        <li>li_8</li>
        <li>li_9</li>
        <li>li_10</li>
    </ul>
    <input type="text">
    <div class="btn1">获取表单内容</div>
    <div class="btn2">设置表单内容</div>
    <script>
        //获取文本内容
        alert($('.box').text());
        console.log($('.box').text())
        $('.box').text('天气很好');
        $('.box').text('天气很好'); //覆盖之前
        //获取
        alert($('ul').html());
        //设值
        $('ul').html('<p>今天天气好</p>'); //覆盖之前
        $('.btn1').click(function() {
            alert($('input').val());
        })
        $('.btn2').click(function() {
            $('input').val('呵呵呵');
        })
    </script>
</body>

</html>
```
### dom查找
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
        .box {
            width: 100px;
            height: 100px;
            background-color: red;
            font-size: 12px;
        }
    </style>
</head>

<body>
    <ul>
        <li>li_1</li>
        <li class="li2">li_2</li>
        <li>li_3</li>
        <li class="li4">li_4</li>
        <li class="li5">li_5</li>
        <li class="li6">li_6</li>
        <li>li_7</li>
        <li>li_8</li>
        <li class="li9">li_9</li>
        <li>li_10</li>
    </ul>
    <div class="w-box">
        <div class="box">
            <div class="inner-box">

            </div>
        </div>
    </div>

    <script>
        console.log($('.li5').siblings()); //所有兄弟
        //后面的兄弟节点
        console.log($('.li5').next()); //下一个兄弟
        console.log($('.li5').nextAll()); //后面的所有兄弟
        // 后面的所有兄弟  直到li9 这个节点结束 (不包括结束节点)
        console.log($('.li5').nextUntil($('.li9')));
        // 前边的  prev() / prevAll() /prevUntil()
        console.log($('.li5').prev());
        console.log($('.li5').prevAll());
        console.log($('.li5').prevUntil($('.li2')));

        // parent() 父亲节点  /parents()
        console.log($('.inner-box').parent());
        console.log($('.inner-box').parents());
        // 不包括结束节点
        console.log($('.inner-box').parentsUntil($('body')));
    </script>
</body>

</html>
```
### 节点操作
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
        .box {
            width: 100px;
            height: 100px;
            background-color: red;
            font-size: 12px;
        }
    </style>
</head>

<body>
    <div class="box">
        不凡学院
    </div>
    <ul>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
    </ul>
    <script>
        //创建节点
        var $spanNode = $('<span>我是一个span元素</span>'),
            $liNode = $('<li>我是一个li元素</li>');

        // $('.box').html($spanNode);
        // $('.box').html($liNode);覆盖之前
        //从后追加节点,在元素的最后一个子元素后面追加元素
        $('.box').append($spanNode);
        // 如果是页面中存在的元素，那么调用append()后，
        // 会把这个元素放到相应的目标元素里面去；但是，原来的这个元素，就不存在了。
        $('li').append($spanNode);
        // 如果是给多个目标追加元素，
        // 那么方法的内部会复制多份这个元素，然后追加到多个目标里面去。
        $('.box').append($spanNode);
        //$(selector).appendTo(node);==>把$(selector)追加到node中去
        $liNode.appendTo($('.box'));

        //从前追加节点
        // 在元素的第一个子元素前面追加内容或节点
        $('.box').prepend($spanNode);

        // 在被选元素之后，作为兄弟元素插入内容或节点
        $('.box').after($liNode);

        //在被选元素之前，作为兄弟元素插入内容或节点
        $('.box').before($spanNode);
    </script>
</body>

</html>
```
### 节点操作清空复制
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
        .box {
            width: 100px;
            height: 100px;
            background-color: red;
            font-size: 12px;
        }
    </style>
    </head>

    <body>
    <div class="box">
        不凡学院
        <li></li>
    </div>

    <div class="box2">
        不凡学院
        <li></li>
    </div>


    <div class="box3">
        不凡学院
        <li></li>
    </div>

    <div class="box4">
        不凡学院
        <li></li>
    </div>
    </body>

    </html>
    ```
1. 清空选中节点的所有子节点(包括内容和节点)
    ```javascript
    $('.box').empty(); // 清空选中节点的所有子节点(包括内容和节点)
    $('.box2').html(''); //同上
    $('.box3').remove(); //清空包括自己
    ```
2. 复制节点
    ```javascript
    console.log($('.box4').clone());
    $('body').append($('.box4').clone());
    ```
### 表单
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
    <input type="checkbox" name="" id="" class="like">
    <input type="radio" name="" id="" class="sex">
    <div class="btn1"> 获取选中状态</div>
    <script>
        // 获取表单当中  单选框   和 多选框的状态
        $('.btn1').click(function() {
            console.log($('.like').prop('checked')); //ture/false
            console.log($('.sex').prop('type')); //radio
        })
    </script>
    </body>

    </html>
    ```
### 表格案例
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
        .btn1 {
            border: 1px solid black;
            margin-top: 10px;
            width: 100px;
        }
        
        .btn2 {
            border: 1px solid black;
            margin-top: 10px;
            width: 100px;
        }
    </style>
</head>

<body>
    <table border="1" cellpadding="10">
        <tr>
            <th>序号</th>
            <th>姓名</th>
            <th>年龄</th>
            <th>性别</th>
        </tr>
        <!-- <tr><td>1</td><td>张三</td><td>27</td><td>男</td></tr> -->
    </table>
    <div class="btn1">追加一条数据</div>
    <div class="btn2">删除一条数据</div>
    <script>
        var users = [{
            name: '张三',
            age: 27,
            sex: '男'
        }, {
            name: '李四',
            age: 28,
            sex: '男'
        }, {
            name: '小红',
            age: 18,
            sex: '女'
        }];

        var newUsers = [{
            name: '王五',
            age: 26,
            sex: '男'
        }, {
            name: '赵六',
            age: 22,
            sex: '男'
        }, {
            name: '小花',
            age: 20,
            sex: '女'
        }];
        addTr($('table'), users);

        function addTr($el, arr) {
            for (let i = 0; i < arr.length; i++) {
                var str = '';
                str = '<tr><td>' + (i + 1) + '</td><td>' + arr[i].name + '</td><td>' + arr[i].age + '</td><td>' + arr[i].sex + '</td></tr>'
                $el.append(str);
            }
        }
        var arr = newUsers.slice();
        $('.btn1').click(function() {
            if (newUsers.length > 0) {
                var user = newUsers.shift();
                var str = '<tr><td>' + (users.length + arr.length - newUsers.length) + '</td><td>' + user.name + '</td><td>' + user.age + '</td><td>' + user.sex + '</td></tr>';
                $('table').append(str);
            } else {
                alert('没有新用户了!')
            }
        })
        $('.btn2').click(function() {
            if ($('tr').length > 1) {
                var tr = $('table tr:last-child')
                tr.remove();

            } else {
                alert('没有数据了!')
            }
        })
    </script>
</body>

</html>
```
### 动画
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
        .box {
            display: none;
            width: 100px;
            height: 100px;
            background-color: red;
            font-size: 12px;
        }
    </style>
</head>

<body>
    <div class="box">
        不凡学院
    </div>
    <div class="btn1">隐藏</div>
    <div class="btn2">显示</div>
    <div class="btn3">滑入</div>
    <div class="btn4">滑出</div>
    <div class="btn5">划入划出切换</div>
    <div class="btn6">淡入</div>
    <div class="btn7">淡出</div>
    <div class="btn8">淡入淡出切换</div>
    <div class="btn9">fadeTo</div>

    <script>
        //         作用：让匹配的元素展示出来
        // 	$(xx).show(2000)
        // 	$(xx).show()		slow：600ms、normal：400ms、fast：200ms
        // 	$(xx).show(2000,function(){});
        // 	$(xx).show()
        $('.btn1').click(function() {
            $('.box').hide(2000);
        })
        $('.btn2').click(function() {
            // $('.box').show(2000);
            // $('.box').show('slow');
            // $('.box').show('normal');
            // $('.box').show('fast');
            $('.box').show(2000, function() {
                $('.box').css({
                    width: '200px',
                    height: '200px',
                    backgroundColor: 'green'
                })
            });
        })
        $('.btn3').click(function() {
            $('.box').slideDown(2000);
        })
        $('.btn4').click(function() {
            $('.box').slideUp(2000);
        })
        $('.btn5').click(function() {
            $('.box').slideToggle(2000);
        })
        $('.btn6').click(function() {
            $('.box').fadeIn(2000);
        })
        $('.btn7').click(function() {
            $('.box').fadeOut(2000);
        })
        $('.btn8').click(function() {
            $('.box').fadeToggle(2000);
        })
        $('.btn9').click(function() {
                $('.box').fadeTo(2000, .2);
            }) // 改变透明度到某个值
    </script>
</body>

</html>
```
### 自定义动画
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
        .box {
            position: absolute;
            top: 200px;
            width: 100px;
            height: 100px;
            background-color: red;
            font-size: 12px;
        }
        
        .btn {
            width: 50px;
            height: 80px;
            background-color: green;
            font-size: 24px;
        }
    </style>
</head>

<body>
    <div class="box">
        不凡学院
    </div>
    <div class="btn">停止动画</div>
</body>

</html>
```
+ $(selector).animate(styles,speed,easing,callback)
    - 第一个参数表示：要执行动画的CSS属性（必选）
    - 第二个参数表示：执行动画时长（可选）
    - 第三个参数: 可选。规定在不同的动画点中设置动画速度的 easing 函数,内置的有  swing  linear
    - 第四个参数表示：动画执行完后立即执行的回调函数（可选）
```javascript
$('.box').click(function() {
    $('.box').animate({
        width: '200px',
        height: '200px',
        fontSize: '50px',
        left: '1000px',
        top: '100px'
    }, 2000, 'swing', function() {
        // $('.box').animate({
        //     left: '100px',
        //     top: 0,
        //     fontSize: '20px'
        // }, 1000)
    })
    $('.box').animate({
        left: '100px',
        top: 0,
        fontSize: '20px'
    }, 1000)
})
//  box的 第一个动画 执行完,才会执行第二个
//  stop(stopAll,goToEnd);
// stopAll  是否全部停止，默认false 停止队列中所有的动画
// goToEnd  是否将停止的动画  默认 false 停止在当前动画的最后一个状态              
$('.btn').click(function() {
    $('.box').stop(true, true);
})
```
### bom相关
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
        * {
            margin: 0;
            padding: 0;
        }
        
        .box {
            width: 100px;
            height: 100px;
            border: 10px solid green;
            padding: 20px;
            margin: 30px;
            /* background-color: red; */
            font-size: 12px;
        }
        
        .inner-box {
            position: absolute;
            left: 50px;
            top: 40px;
            background-color: red;
        }
        
        .main {
            height: 1200px;
            background-color: pink;
        }
        
        .top {
            position: fixed;
            right: 10px;
            bottom: 100px;
            width: 40px;
            height: 20px;
        }
    </style>
</head>

<body>
    <div class="box">
        不凡学院
        <div class="inner-box">
            我是内部盒子
        </div>
    </div>
    <div class="main">

    </div>
    <div class="top">
        回到顶部
    </div>
</body>

</html>
```
1. 高度和宽度操作
    ```javascript
    console.log($('.box').height()); //100盒子高度 ,不包括 padding  border
    $('.box').height(200); //设置高度

    console.log($('.box').width()); // 100 盒子宽度 ,不包括 padding  border
    $('.box').width(200);
    ```
2. offset() 获取或设置元素相对于文档的位置
    ```javascript
    console.log('box相对于文档的位置 left', $('.box').offset().left); //30
    console.log('box相对于文档的位置 top', $('.box').offset().top); //30
    $('.box').offset({
        left: 60,
        top: 60
    })
    console.log('inner-box相对于文档的位置 left', $('.inner-box').offset().left); //120
    ```
3. position() 获取相对于其最近的具有定位的父元素的位置。
    ```javascript
    // 注意：只能获取，不能设置。
    console.log('innerbox position位置 left', $('.inner-box').position().left);
    console.log('innerbox position位置 top', $('.inner-box').position().top);
    ```
4. scrollTop() 获取或者设置元素垂直方向滚动的位置
    ```javascript
    $(selector).scrollTop();
    $(selector).scrollTop(100);
    ```
5. scrollLeft() 作用：获取或者设置元素水平方向滚动的位置
    ```javascript
    $(selector).scrollLeft();
    $(selector).scrollLeft(100);
    ```
6. 设置回到顶部
    ```javascript
    $('.top').click(function() {
        console.log($(document.documentElement).scrollTop());
        $(document.documentElement).animate({
            scrollTop: 0
        })
    })
    ```
### 手风琴特效
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
        * {
            margin: 0;
            padding: 0;
        }
        
        ul {
            width: 1200px;
            height: 400px;
            overflow: hidden;
            list-style: none;
            margin: 100px auto;
        }
        
        li {
            float: left;
            width: 200px;
        }
    </style>
</head>

<body>
    <ul>
        <li>
            <img src="img/m1.jpg" alt="">
        </li>
        <li>
            <img src="img/m2.jpg" alt="">
        </li>
        <li>
            <img src="img/m3.jpg" alt="">
        </li>
        <li>
            <img src="img/m4.jpg" alt="">
        </li>
        <li>
            <img src="img/m5.jpg" alt="">
        </li>
        <li>
            <img src="img/m6.jpg" alt="">
        </li>
    </ul>
    <script>
        var currentLi = null;
        var timer = null;
        $('li').mouseenter(function() {
            // 这里边 this  指向当前的dom元素
            var self = this;
            clearTimeout(timer);
            // 延迟 hover  ,停留200ms  才会触发 动画
            // 每进入一张新的图片,都会清掉之前的timer
            timer = setTimeout(function() {
                currentLi = self;
                // 这里边 this指向会发生变化
                $(self).siblings().animate({
                    width: '100px'
                });
                $(self).animate({
                    width: '700px'
                })
            }, 200)
        })
        $('ul').mouseleave(function() {
            // 这里边 this  指向当前的dom元素
            clearTimeout(timer);
            $(currentLi).animate({
                width: '200px'
            })
            $(currentLi).siblings().animate({
                width: '200px'
            })
        })
    </script>
</body>

</html>
```