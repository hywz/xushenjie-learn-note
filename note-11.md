## js基础-3
### switch语句
```javascript
var fruit = prompt('你喜欢吃什么水果?')
switch(fruit){
    case '苹果':
        alert('我也喜欢!');
        break;
    case '香蕉':
        alert('我更喜欢!');
        break;
    case '菠萝':
        alert('很酸滴!');
        break;
    default:
        alert('我没吃过!');
        break;
}
```
### while语句
```javascript
var num = 0;
while (num <= 10) {
    console.log(num);
    num++;
}
```
### do...while语句
+ do...while语句在执行时，会先执行循环体：
循环体执行完毕以后，再对while后的条件表达式进行判断：如果结果为true，则继续执行循环体，执行完毕继续判断以此类推，如果结果为false，则终止循环。

+ 与while区别:
    - 功能类似
    - while是先判断后执行，而do...while是先执行后判断。
    - 即使条件不满足，do...while可以保证循环体至少执行一次，而while不能
```javascript
var num = 0;
do{
    num++;
    console.log(num);
}while(num<=0)
```
### break和continue语句
1. 	break使用:
+ 从1-99中找到一个能(+5+7)能被33整除的数.(在找到第一个满足的条件收 没必要进行额外的运算 这时候就可以终止循环)
```javascript
for (var i = 1; i <= 99; i++) {
    if ((i + 12) % 33 == 0) {
        console.log(i);
        break; // 结束整个循环
    }
} 
```
+ for循环嵌套,break只能退出当前的这个for循环
```javascript
for (var i = 0; i < 20; i++) {
    console.log(i);
    for (var j = 0; j < 10; j++) {
        console.log(j);
        if (j === 5) {
            break;
        }
    }
}
```
2. continue使用
    需求:找到0-100中所有能被3整除或者能被7整除的数
```javascript
for (var i = 0; i <= 100; i++) {
    if (i % 3 === 0) {
        console.log(i + '能被3整除');
        // 既然能被3整除,就已经满足需求了,就没有必要对它 判断能不能被7整除
        continue;
        // 跳出当次循环,不影响之后的循环
    }

    if (i % 7 === 0) {
        console.log(i + '能被7整除');
    }
}
```
### 数组
+ 如何定义数组
    - new Array
    ```javascript
    var arr = new Array;
    ```
    - 字面量
    ```javascript
	var arr2 = [2,3,5,'str',true,[2,3]];
	// 通常数组表示的都是某一类数据的集合
    ```
+ 下标的概念
    - 数组中的每一个元素都有它对应的下标，下标从0开始。通过下标，我们能够查找，修改数组当中的元素
    - 通过下标查找元素
    ```javascript
	var nameArr = ['张三','李四','王五'];
	console.log('数组里边下表为0的元素===>'+nameArr[0]);
	console.log('数组里边下表为1的元素===>'+nameArr[1]);
	console.log('数组里边下表为2的元素===>'+nameArr[2]);
    ```
    - 通过下标修改元素
    ```javascript
	nameArr[0] = '赵六';
	console.log(nameArr);
    ```
    - 添加元素 ,给空数组追加元素
    ```javascript
	nameArr[3] = '张三';
	console.log(nameArr);
	console.log(nameArr[3]);
    ```
+ length属性  数组里边元素的个数
    ```javascript
	console.log(nameArr.length);
	var arr3 =[];
	console.log(arr3.length); // 空数组长度为0
    ```
### 遍历数组
```javascript
		var age = [29,23,24,12,26,27];
		// 最后一个元素的下标  arr.length-1
		// for循环遍历数组,就是查找到里边所有的元素 ,筛选出需要的
		for (var i = 0; i < age.length; i++) {
			if(age[i]>25){
				console.log('打印下标为'+i+'的元素'+age[i]);
			}
		}

		// for in 也可以 实现数组的遍历
		for(var key in age){
			// key 是 数组 age 的下标
			console.log(key);
			console.log(age[key]);
		}
```
### 数组方法
1. 合并数组 xx.concat()  并不会影响原数组
    ```javascript
    var arr1 = ['张三','王五'];
    var arr2 = ['赵六','李四'];
    // newArr 接受 合并之后的数组
    var  newArr = arr1.concat(arr2);
    console.log(newArr);
    console.log(arr1);
    console.log(arr2);
    ```
2. 字符串 ===> 数组
    ```javascript
    //arr.split('分隔符','指定生成数组的长度')
    var email = 'abc@163.com;cc@126.com;frg@qq.com';
    var emailArr = email.split(';')
    console.log(emailArr);
    ```
3. 数组===> 字符串
    ```javascript
    //arr.join('连接字符串') 参数不写,默认用逗号链接
    var arr = ['张三','李四','王五'];
    var arrStr = arr.join('-');
    console.log(arrStr);
    ```
4. 添加元素
    ```javascript
    //push()从数组最后推入一个元素  改变了原数组 返回新数组的长度
    var nameArr = ['张三','李四','王五'];
    var a = nameArr.push('赵六');
    //返回新数组的长度
    console.log(a);
    console.log(nameArr);

    // unshift()  从前边插入元素 改变了原数组 返回新数组的长度
    var b = nameArr.unshift('小白');
    console.log(b);
    console.log(nameArr);
    ```
5. 删除元素
    ```javascript
    //删除前边的 第一个元素  shift()
    var arr4 = ['张三','李四','王五'];
    var c = arr4.shift();
    console.log(c) // 删除数组的第一个元素 
    console.log(arr4);//==>['李四','王五']

    // 删除 数组 最后一个元素  pop()
    var d = arr4.pop();// 删除数组最后一个元素
    console.log(arr4);//==>'王五'
    console.log(d);//==>['张三','李四']
    ```
### 求数组的平均值
```javascript
var arr = [32,41,1,40,12,5],
    sum = 0;
// 计算数组元素的和,获取数组元素个数,求平均值

for (var i = 0; i < arr.length; i++) {
    sum+=arr[i];
}
var avg = sum/arr.length;
console.log(avg);
```
### 冒泡排序
```javascript
var arr = [4,3,1,40,2,99];
for (var i = 1; i < arr.length; i++) {
    for (var j = 0; j < arr.length-i; j++) {
        if (arr[j]>arr[j+1]) {
            var temp = arr[j+1];
            arr[j+1] = arr[j];
            arr[j] = temp;
        }
    }
}
console.log(arr);
```
### 选择排序
```javascript
var arr = [41,32,1,40,12,5];
for (var i = 0; i < arr.length-1; i++) {
    var minIndex = i;
    for (var j = i+1; j < arr.length; j++) {
        if (arr[minIndex]>arr[j]) {
            minIndex = j;
        }
    }
    var temp = arr[i];
    arr[i] = arr[minIndex];
    arr[minIndex] = temp;
}
console.log(arr);
```
### 函数
```javascript
foo();
// 声明函数  通过关键字 function
// 函数就是 一种封装(常用功能封装) 想用的时候 拿来调用就行
// 函数 不调用 是不会执行的
function foo () {
    alert('我是一个foo函数')
}
// 函数的调用

// 匿名函数表达式
// sing();
var sing = function () {
    alert('Hi,你好!');
}
sing();
```
### 函数的参数
```javascript
// 封装一个函数,求两个数的和
// 参数 就是  函和外界的 一个桥梁
//  形参  x , y, 并参与实际运算,仅仅是为了 给 实参占位置 
//  实参  8, 9 ,真正参与运算
var a = 8;
var b = 9;

function add(x, y, z) {
    console.log(x + y + z);
}
add(a, b);

// 形参个数 和  实参个数 不一致
// 形参 比实参 数量多  计算错误
// 实参 比 形参多,  多出的实参不参与函数运算
// 通常情况下.要保证 实参和形参个数一致
```
### 函数的返回值
1. 函数程序运行后的结果外部需要使用的时候，我们不能拿到，需要通过return返回。
2. 函数使用return语句后，这个函数会在执行完 return 语句之后停止并立即退出，也就是说return后面的所有其他代码都不会再执行。
3. 函数里面可以没有return。
```javascript
var a = 8;
var b = 9;
function add (x,y){
    var sum = x + y;
    // 把 sum 丢出去
    alert('执行了');
    return sum;
    
}
var rs = add(a,b);
// 函数体外  拿不到  函数体内 声明的变量
console.log(rs)
```
### 函数封装案例
```javascript
var arr1 = [1,4,24,12,50];
var arr2 = [3,55,67,87,2];
var newArr = selectSort(arr1),
    newArr1 = selectSort(arr2);
console.log(newArr);
console.log(newArr1);
function selectSort (arr){
    for (var i = 0; i < arr.length-1; i++) {
        var minIndex = i;
        for (var j = i+1; j < arr.length; j++) {
            if (arr[minIndex]>arr[j]) {
                minIndex = j;
            }
        }
        var temp = arr[i];
        arr[i] = arr[minIndex];
        arr[minIndex] = temp;
    }
    return arr;
}
```
### 变量的作用域
```javascript
var a = 123;
var say = function () {
    alert('123');
    var d = 20;
    c = 20; // 全局变量  但是不能这样写
    console.log(a);
}
say();
console.log(window);
// 全局变量 在页面的任意的部分都可以访问的到。
console.log(a);
console.log(d);
// 在函数体内部的 声明的变量
// 如果一个变量在函数体内部声明，则该变量的作用域为整个函数体，在函数体外不可引用该变量。
```
### 作用域上下级关系
```javascript
function foo() {
    var x = 1;
    function bar() {
        var y = x + 1; // bar可以访问foo的变量x!
        var z = 100;
    }
    var z = y + 1; // ReferenceError! foo不可以访问bar的变量y!
    function ins(){
        x++; // ins 可以访问foo的变量x
        y++; // 不可以访问 bar的变量y
        var  z = 1000;
    }
    // 注意 bar 和 ins 中声明的 变量z 是相互独立的,互不影响
}
var a = 150;
function abc (){
    var a =100;
    console.log(window.a);
}
abc();
```
### 变量和函数提升
```javascript
// 使用var关键字声明的变量（ 比如 var a = 1），会在所有的代码执行之前被声明（但是不会赋值）
// 变量声明 提升
console.log(a); // undefined
var a = 20;
// 执行过程
// var a;
// console.log(a);
// a = 20;

// console.log(b);
b = 2; // 全局变量 声明变量 要用 var 关键字
console.log(b);


foo();
// 通过 function 关键字 声明的函数会声明提升(提升到所有代码执行之前)
function foo (){
    alert('我是foo函数')
}

// 在函数作用域也有声明提前的特性 
```

