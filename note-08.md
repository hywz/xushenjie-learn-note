### 练习
1. 确认被5或6整除
```javascript
var num = parseFloat(prompt('请输入一个数字')),
    str = '';
if (num%5==0&&num%6==0) {
    str = '这个数字同时能被5和6整除';
} else if (num%5==0&&num%6!==0) {
    str = '这个数字能被5整除但是不能被6整除';
} else if (num%5!==0&&num%6==0) {
    str = '这个数字能被6整除但是不能被5整除';
} else if (isNaN(num)) {
    str = '您输入的不是数字';
}
else{
    str = '这个数字既不能被5整除又不能被6整除';
}
alert(str);
```
2. 找出1~1000之中，所有能被5整除，或者被6整除的数字
```javascript
for (var i = 1; i <= 1000; i++) {
    if (i%5==0||i%6==0) {
        console.log(i);
    }
}
```
3. 用户输入一个数字，列出所有它能够整除的数字
```javascript
var num = parseFloat(prompt('请输入一个数字'));
for (var i = 1; i <=num; i++) {
    if (num%i==0) {
        console.log(i);
    }
}
if(isNaN(num)) {
        alert('您输入的不是数字');
    }
```
4. 不报7游戏,请在控制台输出1~60之间的所有“安全数”。比如： 1、2、3、4、5、6、8、9、10、11、12、13、15、16、18、19、20、22、23、24、25、26、29、30……
```javascript
for (var i = 1; i <= 60; i++) {
    if (i%7!==0&&i.toString().indexOf('7')==-1) {
        console.log(i);
    }
}
```
5. 水仙花数是一种特殊的三位数，它的特点就是，每个数位的立方和，等于它本身。100~999之内，只有4个水仙花数，请找出来。
```javascript
for (var i = 100; i <= 999; i++) {
    var a = parseInt(i%10),
        b = parseInt(i/10%10),
        c = parseInt(i/100);
    if (Math.pow(a,3)+Math.pow(b,3)+Math.pow(c,3)==i) {
        console.log(i);
    }
}
```
6. 求1~100的和
```javascript
for (var i = 1,result=0; i <= 100; i++) {
    result+=i;
}
console.log(result);
```
7. 计算13的阶乘
```javascript
for (var i = 1, result=1; i <= 12; i++) {
    result*=i;
}
console.log(result);
```
8. 用户输入一个数，输出因数的个数。
比如，用户输入48，此时输出1、2、3、4、6、8、12、16、24、48 .共10个数字。
用户输入21，此时输出1、3、7、21.共4个数字。
```javascript
var num = parseFloat(prompt('请输入一个数字'));
if(isNaN(num)) {
    alert('您输入的不是数字');
    }
for (var i = 1, result = 0; i <=num; i++) {
    if (num%i==0) {
        result++;
        }
    }
console.log(result);
```
9. 用户输入一个数字，弹出这个数字是否是质数
```javascript
var num = parseFloat(prompt('请输入一个数字'));
if(isNaN(num)) {
    alert('您输入的不是数字');
    }
for (var i = 1, result = 0; i <=num; i++) {
    if (num%i==0) {
        result++;
        }
    }
if(result==2){
    alert('是质数')
}else{
    alert('不是质数')
}
```


