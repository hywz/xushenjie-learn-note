## js基础-4
### 数组中的最大值和最小值
```javascript
var arr = [23,3,43,65,34,66,2];
function max(arr){
    var maxIndex = 0;
    for (var i = 1; i < arr.length; i++) {
        if (arr[maxIndex]<arr[i]) {
            maxIndex = i;
        }
    }
    return arr[maxIndex];
}
console.log(max(arr));
function min(arr){
    var minIndex = 0;
    for (var i = 1; i < arr.length; i++) {
        if (arr[minIndex]>arr[i]) {
            minIndex = i;
        }
    }
    return arr[minIndex];
}
console.log(min(arr));
```
### 阶乘递归
```javascript
<script>
    function getFactorial(num){
        if (num===1) {
            return 1;
        }
        return getFactorial(num-1)*num;
    }
    console.log(getFactorial(5));
</script>
```
### 立即执行函数
```javascript
// 1.具名函数
function foo (){

}
//2.匿名函数 表达式
var bar = function (){

}
bar();
//3.自执行函数
(function(){
    alert('hello world!')
})();
```
### 基本数据类型作为参数
```javascript
var num = 1;
function add(num){
    num = num+1;
    return num
}
// 基本数据类型作为参数传递的时候,会在函数内部创建这个数据的副本,做的操作,并不会影响原理数据
console.log(add(num)); // 2
console.log(num); // 1
```
### 复杂数据类型作为参数
```javascript
var arr =[1,2];
var n = 3;
function add (arr,n) {
    arr.push(n);
}
add(arr,n);
console.log(arr); // ==>[1,2,3] arr被修改了
// 会影响外部的参数,因为归根结底原数据被修改了
```
### 不死神兔
+ 求斐波那契(宇宙的真理！)数列Fibonacci中的第n个数是多少?
有一对兔子，从出生起后第3个月起每个月都生一对兔子，小兔子     长到第三个月后每个月又生一对兔子,假如兔子都不死，问第二十个月的兔子对数为多少？ 不死神兔1 1 2 3 5 8 13 21... 
```javascript
function fb(n){
    if (n===1||n===2) {
        return 1;
    }
    return fb(n-1)+fb(n-2);
}
console.log(fb(20));
```
### 求一年当中的第几天
+ 输入某年某月某日，判断这一天是这一年的第几天？（闰年）
（四年一闰，百年不闰，四百年再闰）
只有在闰年的时候366天  在2月29天多一天
其余的时间2月都是28
1. 是否是闰年
2. 每个月多少天
3. Date提供了一个构造函数 可以接受一个yyyy-MM-dd HH:mm:ss类型的字符串 可以转换为date对象
```javascript
var totelDay = 0,
    date = new Date('2015-02-28'),
    year = date.getFullYear(),
    month = date.getMonth() + 1,
    day = date.getDate(),
    monthArr = [31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31];
for (var i = 0; i < month - 1; i++) {
    totelDay += monthArr[i]; //加上前几个月的天数和
}
totelDay += day;
if (isRun && month > 2) {
    totelDay++;
}
console.log(totelDay);

function isRun(year) {
    if ((year % 4 === 0 && year % 100 !== 0) || year % 400 == 0) {
        return true;
    }
    return false;
}
```