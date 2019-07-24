## 代码规范
### class命名问题
+ 避免出现类似`a1`,`a2`等没有语义化的类名，可用`arrLeft`,`arrRight`等语义化的类名代替。
### 选择器使用
+ `getElementsByClassName`等几乎不再用，存在IE兼容问题，可用`document.querySelector`/ `document.querySelectorAll`代替；
+ 考虑到代码的健壮性和可移植性，选择器尽量精确匹配内容，如可用`document.querySelector('.banner .arrLeft')`代替`document.querySelector('.arrLeft')`。
### 注释
+ 必要的逻辑加注释；
+ 变量声明，一般都需要添加注释。
### 变量声明
+ 语义化声明变量，可用`bannerImgWidth`代替`width`;
+ 绝对性词汇、关键词（with height top red green blue left var等）不能做变量。
+ 变量声明需赋值，初始化，避免未定义。
### 模块化
+ 避免出现裸奔的代码，如for循环直接不应放在顶级作用域中，可用函数封装。
### 分号不要省略