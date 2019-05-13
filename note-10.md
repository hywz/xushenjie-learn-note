### 练习
1. 求圆的周长和面积
```javascript
function foo(r){
    function C(r){
        return 2*Math.PI*r
    }
    function S(r){
        return Math.PI*Math.pow(r,2)
    }
    console.log('周长为'+C(r));
    console.log('面积为'+S(r));
}
foo(5);
```
2. 求2个数中的最大值，求3个数中的最大值
```javascript
// 方法一:
function max2(a,b){
    console.log('最大值为'+Math.max(a,b));
}
function max3(a,b,c){
    console.log('最大值为'+Math.max(a,b,c));
}
max2(6,9);
max3(2,45,3);

// 方法二:
var arr=[23,45,54]
function foo(arr){
    for (var i = 1; i < arr.length; i++) {
        for (var j = 0; j < arr.length-i; j++) {
            if (arr[j]>arr[j+1]) {
                var temp = arr[j];
                arr[j] = arr[j+1];
                arr[j+1] = temp;
            }
        }
    }
    console.log('最大值为'+Math.max(arr[arr.length-1]));	
}
foo(arr);
```
3. 求一组数中的最大值和最小值
```javascript
        var arr = [23, 45, 56, 3, 54, 6, 5, 75, 34]
// 方法一:
function foo1(arr) {
    for (var i = 1; i < arr.length; i++) {
        for (var j = 0; j < arr.length - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                var temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
    console.log('最大值为' + Math.max(arr[arr.length - 1]) + ",最小值为" + Math.min(arr[0]));
}
// 方法二:
function foo2(arr) {
    console.log('最大值为' + Math.max.apply(null, arr) + ",最小值为" + Math.min.apply(null, arr));
}
foo1(arr);
foo2(arr);
```
4. 翻转数组，返回一个新数组
```javascript
var arr = [23,34,65,345]
// 方法一:
function reverse(arr){
    console.log(arr.reverse());
}

// 方法二:
function reverse(arr){
    for (var i = 0; i < arr.length/2; i++) {
        var temp = arr[i];
        arr[i] = arr[arr.length-1-i];
        arr[arr.length-1-i] = temp;
    }
    console.log(arr)
}
reverse(arr);
```
5. 对数组排序，从小到大
```javascript
function sort(arr){
    for (var i = 1; i < arr.length; i++) {
        for (var j = 0; j < arr.length-i; j++) {
            if (arr[j]>arr[j+1]) {
                var temp = arr[j];
                arr[j] = arr[j+1];
                arr[j+1] = temp;
            }
        }
    }
    console.log(arr);
}
var arr = [23,34,677,45,23432,454,3]
sort(arr);//==>[3, 23, 34, 45, 454, 677, 23432]
```
6. 求阶乘
```javascript
function factorial(num){
    var result =1;
    for (var i = 1; i <= num; i++) {	
        result*=i;
    }
    console.log(result);
}
factorial(5);
```
7. 求1!+2!+3!+....+n!
```javascript
function sum(num){
    var sum = 0;
    for (var i = 1; i <= num; i++) {
        var jc = 1
        for (var j = 1; j <=i ; j++) {
            jc*=j;
        }
        sum+=jc;
    }
    console.log(sum);
}
sum(5);
```
8. 确认是否是质数
```javascript
function foo(num){
    var result = 0
    for (var i = 1; i <= num; i++) {
        if (num%i==0) {
            result++;
        }
    }
    if (result>2) {
        console.log('不是质数')
    }else{
        console.log('是质数')
    }
}
foo(1);
```
9. 乘法运算表
```javascript
function foo() {
    for (var i = 1; i <= 9; i++) {
        var result = '';
        for (var j = 1; j <= i; j++) {
            result += i + '*' + j + '=' + i * j + ' ';
        }
        console.log(result);
    }
}
foo();
// 1*1=1 
// 2*1=2 2*2=4 
// 3*1=3 3*2=6 3*3=9 
// 4*1=4 4*2=8 4*3=12 4*4=16 
// 5*1=5 5*2=10 5*3=15 5*4=20 5*5=25 
// 6*1=6 6*2=12 6*3=18 6*4=24 6*5=30 6*6=36 
// 7*1=7 7*2=14 7*3=21 7*4=28 7*5=35 7*6=42 7*7=49 
// 8*1=8 8*2=16 8*3=24 8*4=32 8*5=40 8*6=48 8*7=56 8*8=64 
// 9*1=9 9*2=18 9*3=27 9*4=36 9*5=45 9*6=54 9*7=63 9*8=72 9*9=81 
```