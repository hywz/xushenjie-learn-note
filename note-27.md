## 轮播
### 用了最近学的vue的理念以数据驱动方式写了原生js轮播
+ HTML如下
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <link rel="stylesheet" href="./lib/icon/arr/iconfont.css">
    <link rel="stylesheet" href="./lib/style.css">
    <title>轮播</title>
</head>
<body>
    <div class="banner">
        <div class="img"></div>
        <ul class="dots"></ul>
        <span class="iconfont icon-left" onclick="change('left')"></span>
        <span class="iconfont icon-right" onclick="change('right')"></span>
    </div>
    <script>
        var img=document.querySelector('.banner .img'),
            dots=document.querySelector('.banner .dots'),
            num=1; //图片地址数据=>./lib/img/${num}.jpg
        init();//初始化页面
        //左右点击跳转
        function change(val){
            if (val=='left') {
                num--;
                if (num==0) {
                    num=5
                }
            }else{
                num++;
                if (num==6) {
                    num=1
                }
            }
            //添加css3动画类名，动画持续.4s
            img.classList.add(val);
            init();
            //初始化之后删除动画类名
            setTimeout(()=>img.classList.remove(val),400)
        }
        //分页器点击跳转
        function go(val){
            //添加动画类名
            if (num<val+1) {
                img.classList.add('right')
            }else if(num>val+1){
                img.classList.add('left')
            }
            //图片地址切换
            num=val+1;
            init();
            //初始化之后删除动画类名
            setTimeout(()=>img.classList.remove('left','right'),400)
        }
        //初始化
        function init(){
            
            var strImg=`<img src="./lib/img/${num}.jpg">`, //图片地址动态生成
                strDot=''; //分页器动态生成，active类名由图片地址数据num驱动添加
            for (let i = 0; i < 5; i++) {
                strDot+=`<li class='${i==num-1?'active':''}' onclick=go(${i})></li>`
            }
            img.innerHTML=strImg;
            dots.innerHTML=strDot;
        }
    </script>
</body>
</html>
```
+ style.cssr如下
```css
*{
    margin: 0;
    padding: 0;
}
ul {
    list-style: none;
}
.banner{
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%,-50%);
    overflow: hidden;
}
.banner img{
    width: 100%;
}

.iconfont{
    position:absolute;
    font-size: 50px;
    color:rgba(255, 255, 255, 0.5)
}
.iconfont:hover{
    color:cyan
}
.iconfont.icon-left{
    left:0;
    top:50%;
    transform: translateY(-50%)
}
.iconfont.icon-right{
    right:0;
    top:50%;
    transform: translateY(-50%)
}
.dots{
    position: absolute;
    bottom: 15px;
    left: 50%;
    transform: translate(-50%,0)
}
.dots li{
    float: left;
    width: 7px;
    height: 7px;
    border-radius: 50%;
    background: rgba(255, 255, 255, 0.5);
    border: 1px solid rgba(0, 0, 0, 0.1);
    cursor: pointer;
    margin-right: 12px;
}
.dots li:last-child{
    margin-right: 0;
}
.dots li:hover{
    border-color: rgba(0, 0, 0, 0.3);
    background: cyan;
}
.dots li.active{
    border-color: rgba(0, 0, 0, 0.3);
    background: cyan;
}
.banner .right{
    animation: right .4s ease;  
}
.banner .left{
    animation: left .4s ease;  
}
@keyframes left{
    from{
        transform: translate(-100%)
    }
    to{
        transform: translate(0)
    }
}
@keyframes right{
    from{
        transform: translate(100%)
    }
    to{
        transform: translate(0)
    }
}
```
