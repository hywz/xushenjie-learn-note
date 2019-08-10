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
+ 不止js变量,css类名等也不要用绝对性词汇

## git补充

### git基本命令
+ git add .  添加文件到暂存区
+ git commit -m'xx'  把文件添加到存储区
  + 如果忘记打 -m 会进入vim编辑模式,输入:wq 退出
+ git push  远程推送
+ git status  查看文件保存状态
+ git checkout XXX.html  把文件单独检出(慎用)

### .gitignore
+ 忽略文件,每一个项目都有

### 分支
+ git branch XX 创建分支(在当前的代码上克隆了一份代码备用)
+ git branch  查看所有分支,有*前缀的为当前代码所在分支
+ git checkout XX 切换到XX分支
+ git merge xx 在当前分支删除其他分支

### github
+ git remote add origin https://github.com/....  跟远程仓库建立连接
+ git remote -v 查看远程源
+ git push -u origin master 建立连接后的首次推送,推送的主分支
+ git push 默认推送
+ git push origin XXX  在当前分支推送到远程分支
+ git reset --hard safdasdfdf 时光机
+ git log  查看提交过的日期使用时光机(每次git commit -m'备注信息'后都会有提交记录)

### clone
+ git clone https://github.com/..... dev-home
+ git pull 将远程仓库最新内容拉下来合并

### ssh
+ ssh-keygen -t rsa -C "youremail@example.com"  创建sshkey,下一步一步步...
+ C:\Users\Administrator\.ssh  ==> id_rsa.pub
+ github添加公钥:https://github.com/settings/keys

## 本地的gitblit服务器
+ https://192.160.0.200:8443/