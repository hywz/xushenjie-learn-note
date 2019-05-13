## js基础-1
### js引入
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <script type="text/javascript" src="text.js"></script>
    <!-- 外部引入方式 -->
</head>

<body>
    <script>
        // 内部书写
        // 单行注释Ctrl+/
        /*	多行注释
        	Ctrl+shift+/*/
        prompt('您多大年纪啦?');

        document.write('<h1>你好</h1>');
    </script>
</body>

</html>
```
### 变量
```javascript
// 声明变量 var 关键词
// 每一句代码结束,分号结尾
var age;
var a,
	b,
	c;
age = 18;
// 将18赋值给变量age  
console.log(age);
var d = 21;
// 声明变量d并赋值20;

// 注意的是 ,变量需要先声明,才能使用
console.log(q); //报错

// 变量名 命名规则
// 字母 数字 _ $ 
// 不能以数字开头
// 严格区分大小写
// 不能使用关键字,保留字
// 驼峰命名
// 见名知意
var $ = 123;
var _ads =232;
var dsadsadas ="徐";
```
### 数据类型
1. 基本数据类型
+ Number 类型
    - 整数和浮点数（小数）
+ String 类型 (字符串)
+ boolean布朗类型 (布尔值)
    - true
    - false
+ undefined 类型 
    - 只有一个值: undefined
    - 当一个变量声明了,但是没有被赋值,他就是undefined
+ null
    - 指向一个空对象
```javaScript
var str = "hello 'wo'rld!";
console.log(str);
// 字符串需要使用引号引起来，使用双引号或单引号都可以，但是不要混着用。
// 引号不能嵌套：双引号里不能再放双引号，单引号里不能再放单引号。
//但是单引号里可以嵌套双引号,或者双引号里嵌套单引号.
var age = 234;
console.log(age);
// 无穷大
//正无穷大:Infinity
//负无穷大:-Infinity
//NaN:一个特殊的数字,表示Not a Number,非数值.
console.log('a'/3);  //==>NaN
console.log('a'*'b') //==>NaN 按理说，字符串相乘是没有结果的，但如果你非要让JS去算，它就一定会给你一个结果,结果是NaN.

//isNaN()任何不能被转换为数值的值，都会让这个函数返回 true。
console.log(isNaN(123));//==>false
console.log(isNaN('ASD'))//==>true
console.log(isNaN(NaN));//==>ture

var c;
console.log(c)//==>undefined
// 声明但是未被赋值

console.log(typeof null)//==>object
```
2. 复杂数据类型(引用数据类型)
+ 数组 array
```javascript
var arr = [1,'str',4,true,[1,23,4]];
```
+ 对象 object
    - key:value 形式
```javascript
var obj = {
	name: '张三',
    age:28,
	sex:'男',
	like:['篮球','足球','乒乓球']
	child:{
		name:'zhang',
		age:2,
		sex:'nv'
 	}
}
```
+ 函数 function
```javascript
function foo(){

}
```
### 判断数据类型
```javascript
var age = 23,
	sex = true,
	like = ['篮球','足球'],
	child = {
		name:'张',
		age: 2
	}
function foo(argument) {
	// body...
}
//typeof 可以判断数据类型
console.log(typeof age);//==>number
console.log(typeof sex);//==>boolean
console.log(typeof like); //==>object
console.log(typeof child); // ==>object
console.log(typeof foo); // ==>function
```
### 数据类型的转换
1. 转换为 string 类型
+ number==> string + 拼接的作用
```javascript
console.log(123+'');//==>'123'
console.log(null+'');//==>'null'
console.log(undefined+'');//==>'undefined'
console.log(true.toString())//==>'true'
console.log(true)
```
2. 转换为 number 类型
+ Number()
```javascript
console.log(Number(null));//==>0
console.log(Number(undefined));//==>NaN
console.log(Number(true));//==>1
console.log(Number(false));//==>0
console.log(Number('sd2'));//==>NaN
console.log(Number('23'));//==>23
console.log(Number('23.23'));//==>23.23
console.log(Number('-123'));//==>-123
console.log(Number(' 123'));//==>123
console.log(Number('1 23'));//==>NaN
console.log(Number('123 '));//==>123
console.log(Number(''));//==>0
// parseInt() 转换为整数
// 转换规则：从第一个非空白字符（空格、换行、tab）开始转换，直到遇到一个非数字字符为止。
console.log(parseInt(''));//==>NaN
console.log(parseInt('12.9'));//==>12 向下取整
console.log(parseInt('12jhflk6'));//==>12
console.log(parseInt('jk5214'));//==>NaN

// parseFloat() 转换成浮点数
// 从第一个非空白字符（空格、换行、tab）开始转换，直到遇到一个非数字字符为止
// 遇到的第一个小数点有效，第二个小数点就无效了
console.log(parseFloat('12.3'));//==>12.3
console.log(parseFloat('12..3'));//==>12
console.log(parseFloat('a12.3'));//==>NaN
```
### 比较运算符
+ `>` 大于
+ `<` 小于
+ `>=` 大于等于
+ `<=` 小于等于
+ `==` 等于 (只比较数值,不比较类型.比较之前会进行类型统一)
+ `===` 严格相等 类型和数值都要相等才可
+ 语法 表达式1 运算符 表达式2
如果关系成立值为 true,否则值为 false
```javascript
console.log('123'==123);//==>ture 存在隐式转换 先把字符串变成number 123,再比较
console.log('123'===123);//==>false 先比较数据类型,不一致 ,false,  类型一致 再比较数值
console.log(123>'32');//==>true
console.log(0>'true');//==>false
console.log('sds'>'abc');//==>true
console.log('a'>'c');//==>false
console.log(5>=5);//==>true
```
### 算术运算符
```javascript
var a = 5;
var b = 3;
var c = 'hello';
var d = 'world';
var e = '7';
console.log(a+b);//==>8
console.log(a-b);//==>2
console.log(a*b);//==>15
console.log(a/b);//==1.666666...
console.log(a%b); // 2

// + 除了加法运算意外,还有拼接字符串的功能
console.log(c+d);//==>;'helloworld'
console.log(a+c);//==>'5world'
console.log(a+e),//==>'57'
console.log(c-d); //==>NaN
console.log(a-e); //==>-2
console.log(a/e); //==>0.7142857142857143
console.log(a*e); //==>35
console.log(a%e); //==>5
```
### 带操作的赋值运算符
```javascript
var a = 10; // 10
var b = a + 10; // 20
console.log(b);//==>20

a = a + 10;
a = 30;
console.log(a);//==>30

var c = 20;
// c = c + 1;
c += 1;
console.log(c);//==>21

c++;
console.log(c);//==>22

// c = c -1;
// c -= 1;
c --;
console.log(c);//==>21

var d = 10;
// 不管是 d++ 还是 ++d 都实显现了+1
// ++d 返回值是 +1之后的 11
// d++ 返回值是 +1之前的 10
// var fd = ++d;
var bd = d++;
console.log(bd);//==>10
```




