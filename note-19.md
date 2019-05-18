## jQuery-3
### 表格
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
        .btn {
            border: 1px solid black;
            margin-top: 10px;
            width: 100px;
        }
        
        button {
            display: block;
            margin-top: 10px;
        }
        
        .mask {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, .5);
        }
        
        .mask .form {
            width: 600px;
            height: 400px;
            margin: 100px auto;
            background-color: #fff;
            overflow: hidden;
        }
        
        .form .form-item {
            width: 400px;
            margin: 50px auto;
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
            <th>操作</th>
        </tr>
        <!-- <tr>
            <td>1</td>
            <td>张三</td>
            <td>27</td>
            <td>男</td>
            <td><button class="remove">删除</button><button class="edit">编辑</button></td>

        </tr> -->
    </table>
    <div class="btn btn1">追加一条数据</div>
    <div class="btn btn2">删除一条数据</div>
    <div class="btn addBtn">新增数据</div>
    <div class="mask">
        <div class="form">
            <div class="form-item">
                姓名: <input class="username" type="text">
            </div>
            <div class="form-item">
                年龄: <input class="age" type="text">
            </div>
            <div class="form-item">
                性别: 男:<input class="sex" type="radio" name="sex" value="1"> 女: <input class="sex" type="radio" name="sex" value="0">
            </div>
            <button class="save">确定</button>
            <button class="cancel">取消</button>
        </div>
    </div>
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
            sex: 'nv'
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
                str = '<tr><td>' + (i + 1) + '</td><td>' + arr[i].name + '</td><td>' + arr[i].age + '</td><td>' + arr[i].sex + '</td></td><td><button class="remove" onclick="del(this)">删除</button><button class="edit" onclick="edit(this)">编辑</button></td></tr>'
                $el.append(str);
            }
        }
        var arr = newUsers.slice();
        $('.btn1').click(function() {
            if (newUsers.length > 0) {
                var user = newUsers.shift(),
                    num = users.length + arr.length - newUsers.length,
                    str = '<tr><td>' + num + '</td><td>' + user.name + '</td><td>' + user.age + '</td><td>' + user.sex + '</td></td><td><button class="remove" onclick="del(this)">删除</button><button class="edit" onclick="edit(this)">编辑</button></td></tr>';
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
        var isEdit = false,
            $tempNodes = null;
        $('.addBtn').click(function() {
            $('.mask').fadeIn('slow');
            isEdit = false;
        })

        function edit(obj) {
            isEdit = true;
            $('.mask').fadeIn('slow');
            //填充信息
            $tempNodes = $(obj).parent().parent().children();
            $('.username').val($tempNodes.eq(1).text());
            $('.age').val($tempNodes.eq(2).text());
            $tempNodes.eq(3).text() == '男' ? $('.sex').eq(0).prop('checked', true) : $('.sex').eq(1).prop('checked', true);
        }
        $('.save').click(function() {
            var username = $('.username').val(),
                age = $('.age').val(),
                sex = $('.sex:checked').val(),
                user = {
                    name: username,
                    age: age,
                    sex: sex == 1 ? '男' : '女'
                }
            if (isEdit) {
                $tempNodes.eq(1).text(user.name);
                $tempNodes.eq(2).text(user.age);
                $tempNodes.eq(3).text(user.sex);
            } else {
                var str = '<tr><td></td><td>' + user.name + '</td><td>' + user.age + '</td><td>' + user.sex + '</td><td><button class="remove" onclick="del(this)">删除</button><button class="edit" onclick="edit(this)">编辑</button></td></tr>';
                $('table').append(str);
            }
            cancel();
        })
        $('.cancel').click(function() {
            cancel();
        })

        function cancel() {
            // 关闭弹窗
            // 清空表单
            $('.username').val('');
            $('.age').val('');
            $('.sex').prop('checked', false);
            $('.mask').fadeOut('slow');
        }

        function del(obj) {
            $(obj).parent().parent().remove();
        }
    </script>
</body>

</html>
```
### on方式绑定事件
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
        }
    </style>
</head>

<body>
    <div class="box">

    </div>
    <button>解绑事件</button>
    <script>
        $('.box').on('mouseenter', function() {
            alert('祝你好运!')
        })
        $('button').click(function() {
            $('.box').off('mouseenter')
        })
    </script>
</body>

</html>
```
### 事件委托
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
        <li>li_1</li>
        <li>li_2</li>
        <li>li_3</li>
        <li class="li4">li_4</li>
    </ul>
    <div class="btn1">生成li</div>
</body>

</html>
```
```javascript
 $('.btn1').click(function() {
    var str = '<li>我是后生成的li</li>'
    $('ul').append(str);
})
$('li').click(function() {
    alert($(this).text());
})
// 后生成的li 并没有添加上点击事件 
```
+ 事件委托
    ```javascript
    $('ul').on('click', 'li', function() {
        alert($(this).text());
    })
    ```
+ 利用event实现
    ```javascript
        $('ul').click(function(event) {
        // 实际点击的是谁  event.target
        alert($(event.target).text());
    })
    ```
### 事件触发
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
        }
    </style>
</head>

<body>
    <div class="box">

    </div>
    <button>触发box点击事件</button>
    <script>
        $('.box').click(function() {
            alert('祝你好运!');
        })
        $('button').click(function() {
            $('.box').trigger('click');
            // $('.box').triggerHandler('click');
        })
    </script>
</body>

</html>
```
### 事件对象
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
        }
        
        .inner-box {
            width: 50px;
            height: 50px;
            background-color: green;
        }
    </style>
</head>

<body>
    <div class="box">
        <div class="inner-box">

        </div>
    </div>
    <button>触发box点击事件</button>

    <input type="text">
    <p class="text"></p>
    <script>
        $('.box').click(function(event) {
                console.log('我是外部盒子');
                console.log(event);
                console.log('this', this);
                // currentTarget   this  指向一样 事件绑定的对象
                // target  实际触发的对象
                console.log('target', event.target);
                console.log('currnTarget', event.currentTarget);
            })
            //按键问题
        $('input').keyup(function(event) {
            // keycode 获取点击的 按键  回车==>13
            console.log(event.keyCode);
            $('p').text($(this).val());
            if (event.keyCode == 13) {
                $('p').css('background-color', 'red');
            }
        })
    </script>
</body>

</html>
```
### 表单控件
+ 表单提供信息录入的能力
	1. 用户名
	2. 密码
	3. 性别: 单选
	4. 爱好: 多选
	5. 上传头像: file
	6. 工作经验: 
        无
        1~2
        3~5
	7. 个人介绍
	8. 按钮 
+ 表单必须写到form中
    - action 用于设置提交请求的地址
    - get是表单的默认提交方式 
    1. 地址栏显示提交内容
    2. 不安全
    3. 提交的内容容量有限
    4. 有缓存
+ post提交
    1. 数据在请求体保存
    2. 相对安全
    3. 容量无限
    4. 没有缓存
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
    <form action="http://www.baidu.com" method="get">
        <!-- 提交地址 -->
        <fieldset>
            <legend>基本信息</legend>
            <!-- 单行输入框 -->
            <!-- 任何标签都有id属性,id在当前页面不能重复 -->
            <!-- 表单特有属性: name
			用于标识当前表单作用,用于向后台传递数据 -->
            <!-- 如果需要用表单给后台提交数据 必须有name属性 -->
            <!-- 可以设置默认值 但是会被重新输入的内容覆盖 -->

            身份证: <input type="hidden" name="idCard" value="41011111111"><br>
            <!-- readonly 只读 -->
            学号: <input type="text" name="userid" readonly value="1001011"><br>
            <!-- disabled 表单不可用 -->
            学号: <input type="text" name="userid2" disabled value="1001011"><br> 用户名: <input id="username1" name="username" type="text" value="张三"> <br>
            <!-- 密码输入框 -->
            密码: <input type="password" name="password" value="123"> <br> 性别:
            <!-- name属性用于给表单(单选/多选)分组
					在单选分组内 会出现互斥 -->
            <!-- checked 默认选中 -->
            <label>
					男:<input name="sex" checked type="radio" value="0"> 
			</label>
            <label>
					女:<input name="sex" type="radio" value="1"> <br>
			</label>
        </fieldset>
        <fieldset>
            <legend>补充信息</legend>
            爱好:
            <!-- 虽然不需要互斥 但是一组多选应该也加上相同的name属性 -->
            <!-- 这里会有数据词典 -->
            篮球: <input name="like" checked type="checkbox" value="001"> 足球: <input name="like" type="checkbox" value="002"> 乒乓球: <input name="like" checked type="checkbox" value="003"><br>
            <!-- 上传组件 实现的是表现,实际还需要代码配合完成 -->
            头像: <input name="avatar" type="file"> <br> 工作经验:
            <!-- 下拉框 -->
            <select name="exp">
					<option value="-1">无</option>
					<option selected value="1">1~3</option>
					<option value="2">3~5</option>
                </select><br>
            <!-- exp=1 -->
            城市:
            <select name="city">
					<option value="100">北京</option>
					<option value="200">上海</option>
					<option value="500">河南</option>
				</select><br> 个人介绍:
            <!-- 多行文本 -->
            <textarea name="desc" cols="30" rows="10"></textarea>
            <br>
        </fieldset>
        <!-- 提交按钮 -->
        <!-- disabled 一般在表单的按钮中使用 -->
        <input type="submit" value="提交">
        <input type="reset" value="重置">
        <!-- 提交后url表示 -->
        <!-- 汉语在url会被转码 
		 -->
        <!-- url 的表示形式为:  action?key=value&key=value&key=value  -->
        <!-- https://www.baidu.com/?username=%E5%BC%A0%E4%B8%89&password=1234&sex=0&like=001&like=003&avatar=&exp=1&city=200&desc=1234 -->
    </form>
</body>

</html>
```
### 阻止冒泡默认
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
            width: 200px;
            height: 200px;
            background-color: red;
        }
        
        .inner-box {
            width: 100px;
            height: 100px;
            background-color: green;
        }
    </style>
</head>

<body>
    <div class="box">
        <div class="inner-box"></div>
    </div>
    <script>
        $('.box').click(function() {
            alert('我是外部盒子');
        })
        $('.inner-box').click(function(event) {
            alert('我是内部盒子');
            //阻止冒泡
            event.stopPropagation();
            //阻止默认事件
            event.preventDefault();
        })
    </script>
</body>

</html>
```
### 链式编程
+ 链式编程原理：return this;  调用”任何”一个方法都是返回了对象本身
+ 通常情况下，只有设置操作的时候才能把链式编程延续下去。因为获取操作的时候，会返回获取到的相应的值，无法返回 this。
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
            width: 200px;
            height: 200px;
            background-color: red;
        }
        
        .inner-box {
            width: 100px;
            height: 100px;
            background-color: green;
        }
    </style>
</head>

<body>
    <div class="box">
        我是外部盒子
        <div class="inner-box">我是内部盒子</div>
    </div>
    <script>
        $('.inner-box').click(function() {
            // $(this).css('width', '80px').css('font-size', '40px');
            $(this).css('width', '80px').css('font-size', '40px').parent().css('width', '500px').end().css('background-color', 'black');
            // 结束当前链最近的一次过滤操作，并且返回匹配元素之前的状态。
        })
    </script>
</body>

</html>
```
### 隐式迭代
+ 隐式迭代的意思是：在方法的内部会为匹配到的所有元素进行循环遍历，执行相应的方法,而不用我们再进行循环，简化我们的操作，方便我们调用。
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
        }
    </style>
</head>

<body>
    <div class="box">
        我是盒子1
    </div>
    <div class="box">
        我是盒子2
    </div>
    <div class="btn">获取</div>
    <script>
        $('.btn').click(function() {
                console.log($('.box').text());
            })
            // 打印了 两段内容,存在隐式迭代
    </script>
</body>

</html>
```
### each方法
+ 大部分情况下是不需要使用each方法的，因为jQuery的隐式迭代特性
+ 如果要对每个元素做不同的处理，这时候就用到了each方法
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
    <script>
        $('li').each(function(index, ele) {
            // ele  当前正在遍历的 dom对象
            // index 当前正在便利的dom对象   的下标
            console.log('index==>', index);
            console.log('ele==>', ele);
            if (index > 3) {
                ele.onclick = function() {
                    alert('点击事件');
                }
            }
        })
    </script>
</body>

</html>
```
### 五角星
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
        
        .star {
            color: orange;
            margin-left: 10px;
            font-size: 30px;
        }
    </style>
</head>

<body>
    <div class="box">
        <span class="star">☆</span>
        <span class="star">☆</span>
        <span class="star">☆</span>
        <span class="star">☆</span>
        <span class="star">☆</span>
    </div>
    <script>
        $('.star').mouseenter(function() {
            $(this).text('★').prevAll().text('★');
        })
        $('.star').mouseleave(function() {
            $(this).text('☆');
        })
        $('.box').mouseleave(function() {
            $('.star').text('☆');
        })
    </script>
</body>

</html>
```
### 多库共存
+ $.noConflict();让jQuery释放对$的控制权，让其他库能够使用$符号，达到多库共存的目的。
+ 此后，只能使用jQuery来调用jQuery提供的方法
### 插件
1. 全局jQuery函数扩展方法:
    + $.pluginName = function() {};

2. jQuery对象扩展方法 fn=prototype  原型
    - $.fn. pluginName = function() {};

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <script src="../lib/jquery-3.4.1.min.js"></script>
    <script src="../lib/temp.js"></script>
    <title>Document</title>
</head>

<body>
    <div class="box">
        我是外部盒子
    </div>
    <div class="btn">修改字体颜色</div>
    <script>
        $('.btn').click(function() {
            $.changeColor($('.box'));
        })
        $('.box').changeBgcolor();
    </script>
</body>

</html>
```
temp.js内容:
```javascript
$.changeColor = function($el) {
    $el.css('color', 'red');
}
$.fn.changeBgcolor = function() {
    this[0].style.backgroundColor = 'red';
}
```
### jq-color
利用插件jquery.color.js使背景颜色加入动画
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <script src="../lib/jquery-3.4.1.min.js"></script>
    <script src="../lib/jquery.color.js"></script>
    <title>Document</title>
    <style>
        .box {
            width: 200px;
            height: 200px;
            background-color: red;
        }
    </style>
</head>

<body>
    <div class="box">

    </div>
    <div class="btn">动画开始</div>
    <script>
        $('.btn').click(function() {
            $('.box').animate({
                width: 300,
                height: 300,
                backgroundColor: 'green'
            }, 'slow')
        })
    </script>
</body>

</html>
```
### 灯箱
利用light-box插件达到灯箱效果
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <link rel="stylesheet" href="../dist/css/lightbox.min.css">
    <script src="../lib/jquery-3.4.1.min.js"></script>
    <script src="../dist/js/lightbox.min.js"></script>
    <title>Document</title>
    <style>
        img {
            width: 200px;
        }
    </style>
</head>

<body>
    <a href="img/m1.jpg" data-lightbox="roadtrip">
        <img src="img/m1.jpg" alt="">
    </a>
    <a href="img/m2.jpg" data-lightbox="roadtrip">
        <img src="img/m2.jpg" alt="">
    </a>
    <script>
        lightbox.option({
            'resizeDuration': 200,
            'wrapAround': true
        })
    </script>
</body>

</html>
```