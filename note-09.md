## js基础-2
### Date对象
```javascript
var date = new Date();
console.log(date);
// js当中的内置对象 Date
//  创建了 构造函数(Date) 的实例对象

var xiaoming = {
    height: 172,
    weight: 60,
    say: function(){
        alert('你好!')
    }
}
console.log(xiaoming.height);
// xiaoming.say();	// 调用对象的say 方法
// 对象有属性 和方法
// 对象.xx 获取对象的属性  小狗的颜色 身高 体重
// 对象.xx()  调用对象的方法 小狗跑 小狗跳 (方法)

// date实例对象 有很多方法
var day = date.getDate();
console.log(day);
var month = date.getMonth()+1;
console.log(month);
var year = date.getFullYear();
console.log(year);
var hour = date.getHours();
var min = date.getMinutes();
var second = date.getSeconds();
//程序语言中 时间的最小单位为毫秒   1s = 1000 ms;
var mm = date.getMilliseconds();
var weekDay = date.getDay();
var dateStr = year+'年'+month+'月'+day+'日'+hour+'时'+min+'分'+second+'秒';
console.log(dateStr);

// 时间戳
var stamp = date.getTime();
console.log(stamp);
// 距离 1970年1月1日 0 时0 分  的 毫秒数
```
### Math对象
```javascript
console.log(Math);
// js当中的内置对象

// Math.ceil  天花板函数  ,向上取整
console.log(Math.ceil(2.1));//3
// 注意负数的使用
console.log(Math.ceil(-2.1));//-2

// Math.floor()  地板函数  向下取整
console.log(Math.floor(2.9));//2

console.log(Math.max(2,3,9));//9
console.log(Math.min(2,54,0));//0

// random()  范围 [0,1)
console.log(Math.random());

// 随机 0-99 范围
console.log(Math.floor(Math.random()*100));

// 随机 5-10 范围
console.log(Math.floor(Math.random()*6+5));
// Math.floor(Math.random()*数量 + min)

console.log(Math.pow(2,3));//2的3次方
console.log(Math.pow(2,9999999999999999999999999999999999999999999999999));
console.log(2/0);//Infinity

// Math.round()
console.log(Math.round(2.4)); // 2
console.log(Math.round(2.5)); // 3
console.log(Math.round(2.499999999999999999999999999)); // 3
console.log(2.999999999999999999999999999===3);
```
### 逻辑运算符
1. 与(且):&&  都真  才真
    - 条件表达式1 && 条件表达式2  两个都为 true  返回结果才是 true
2. 或:||	一个真 ,即为真
    - 条件表达式1 || 条件表达式2  只要有一个为 true  返回结果 就是 true
3. 非:!	取反
```javascript
console.log(true&&false);//false
console.log(true||false);//true
console.log(false || false); // false
console.log(!true); // false  取反

// 检测2在不在3和5之间
// console.log(3<2<5); 连比,错误写法
// 大于3 且小于5
console.log(2>3 && 2<5);

// 判断一个人是否能够考驾照，交通法规定18~70岁能够考驾照。
// 大于等于18 小于等于70
var age = parseInt(prompt('请用户输入年龄',18));
console.log(age);
alert(age>=18&&age<=70);

// 返回的并不一定是布尔值
var a5 = "Cat" && "Dog"; 
console.log(a5);   // Dog
var a6 = false && "Cat";    // false
var a7 = "Cat" && false;    // false
// 逻辑且   碰到假  就返回


var o5 = "Cat" || "Dog";    // Cat
var o6 = false || "Cat";    // Cat
var o7 = "Cat" || false;    // Cat
// 逻辑或  碰到真 就返回


var n1 = !true;  // false
var n2 = !false; // true
var n3 = !"Cat"; // false
```
### if语句
格式:
if(条件表达式){
    条件为真的时候做的事情
}else{
 	条件为假的时候做的事情
}
```javascript
var age = 17;
// ()隐式转换具有 Boolean()
if(''){
    alert('年龄符合');
}else{
    alert('年龄不符合');//==>执行
}
alert('么么哒');//不管符不符合,这句代码都会执行
// 条件表达式，要么是true、要么是false。 隐式转换
```
### 多分支if语句
1. 用户输入成绩，
如果成绩大于等于85，那么提示优秀；
否则如果成绩大于等于70，那么提示良好；
否则如果成绩60~69，那么提示及格；
否则，不及格.
```javascript
var cj = parseInt(prompt('请输入成绩'));
if (cj>=85) {
    alert('优秀');
}else if (cj>=70) {
    alert('良好');
}else if (cj>=60) {
    alert('及格');
}else{
    alert('不及格');
}
alert('么么哒!')
// 下一个楼层已经暗含之上的楼层都不满足。
```
2. 跳楼现象
```javascript
var a = 10;

if(a > 5){
    a = a + 3;
}else if(a == 13){
    a = a + 4;
}else if(a == 17){
    a = a + 5;
}else{
    a = a + 6;
}
console.log(a);//13
```
### if语句小知识
如果要做的事情，只有一句话，那么可以省略大括号（一般情况下，一定要把大括号写完整)
```javascript
var a =21;
if(a>20) alert('么么哒');
```
### if练习
过轻：低于18.5
正常：18.5-24.99999999
过重：25-27.9999999
肥胖：28-32
非常肥胖: 高于32
```javascript
var height = parseFloat(prompt('请输入身高,单位米')),
    weight = parseFloat(prompt('请输入体重,单位千克')),
    BMI = weight/Math.pow(height,2),
    str = '';
if (BMI>32) {
    str = '非常肥胖';
}else if (BMI>=28) {
    str = '肥胖';
}else if (BMI>=25) {
    str = '过重';
}else if (BMI>=18.5) {
    str = '正常';
}else{
    str = '过轻';
}
alert(str);
```
### if练习嵌套
一个加油站为了鼓励车主多加油，所以加的多有优惠。
92号汽油，每升6元；如果大于等于20升，那么每升5.9；
95号汽油，每升7元；如果大于等于30升，那么每升6.95
编写JS程序，用户输入自己的汽油编号，然后输入自己加多少升，弹出价格。
```javascript
var type = prompt('请输入汽油编号92或95','92'),
    count = parseFloat(prompt('请输入加多少升'))
    totalPrice = 0,
    price = 0;
if (type==='92') {
    if (count>=20) {
        price = 5.9;
    }else{
        price = 6;
    }
}else{
    if (count>=30) {
        price = 6.95;
    }else{
        price = 7;
    }
}
totalPrice=count*price;
alert('您一共加了'+count+'升'+type+'号汽油,一共'+totalPrice+'元.');
```
### 三元运算符
表达式?如果表达式结果为true执行这里的代码:如果表达式结果为false执行冒号后面的代码;
三元运算符可以理解为if..else的另外一种写法。
```javascript
var a = 3>2?1+1:1+2;
console.log(a);
```
### for循环
```javascript
// 在控制台输出 0-100
for (var i = 0; i <= 100; i++) {
    console.log(i);
}
// 声明了 循环变量 i = 0
// 判断是否符合循环条件 ,不符合 循环结束
// 符合的 话 走 {}
// 执行 循环变量 + 步长
console.log(i);//101

// for(var i = 1 ; i > 0 ; i++){
//     console.log(i);
//     死循环	
// }

for(var i = 3 ; i < 20 ; i = i + 2){
    if(i % 3 == 2){
        i = i + 1;
    }else{
        i = i + 2;
    }
    console.log(i);
}
// 5 9 12 15 18 
```


