## ajax请求
### 与原生模板差异
+ 优点：异步请求，用户交互体验较好，将一些后端的工作移到前端，减少服务器与带宽的负担，常用于后台管理。
+ 缺点：不利于seo优化。（原生模板常用于前台展示）
### 原生ajax
+ get请求
```js
var xhr=new XMLHttpRequest();
xhr.open('get',url);
xhr.onreadystatechange=function(){
	if (xhr.readyState==4&&xhr.status==200) {
		var res=JSON.parse(xhr.responseText);
		success(res)
	}
}
xhr.send(null)
```
+ post请求
```js
var xhr=new XMLHttpRequest();
xhr.open('post',userSaveUrl);
xhr.onreadystatechange=function(){
	if (xhr.readyState==4&&xhr.status==200) {
		var res=JSON.parse(xhr.responseText);
		success(res)
	}
}
xhr.setRequestHeader("Content-type","application/x-www-form-urlencoded");
xhr.send('parm')
```
### ajax封装
```js
function ajax(options){
    var xhr=new XMLHttpRequest(),
        url=options.url,
        params=options.params;
    if (options.type.toLowerCase()=='get') {
        params=params==''?'':('?'+params);
        xhr.open('get',url+params);
        xhr.send(null)
    }else{
        xhr.open('post',url);
        xhr.setRequestHeader("Content-type","application/x-www-form-urlencoded");
        xhr.send(params)
    }
    xhr.onreadystatechange=function(){
      if (xhr.readyState==4&&xhr.status==200) {
        options.success(JSON.parse(xhr.responseText))
      }
    }
}
```
## PC端响应式适配
+ PC端不必用原始比例rem来写,还按原始像素px即可,在移动端进行响应式适配时,针对大小不同的设备单独进行布局适配.