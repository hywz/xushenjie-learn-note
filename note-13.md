## js基础-5
### 对象
1. 属性(特征) 方法(行为/动态)
2. 封装 信息
3. 对象属性值 任意的数据类型, 属性值是函数,我们称之为对象的方法
```javascript
var obj = {
        name: '张三',
        age: 20,
        say: function() {
            alert('我是谁?')
        },
        child: {
            name: '小明',
            age: 3
        }
    }
// 调用对象的方法
obj.say();
// 获取对象属性
obj.name;
```
### 创建对象
1. 通过 顶级对象Object new
```javascript
var obj = new Object;
// 创建了一个空对象

// 为obj 追加 name属性
obj.name = '张三';
obj.age = 20;
// 修改name属性
obj.name = '李四';
// 为obj 追加方法
obj.say = function() {
    alert('我是李四')
};
console.log(obj);
```
2. 字面量创建
```javascript
var obj1 = {
    name: '张三',
    age: '20',
    say: function() {
        alert('我是张三')
    },
    child: {
        name: '小明',
        age: 3
    }
};
// 为obj1 追加属性和方法
// 在创建的时候,直接指定对象中的属性和方法。
```
3. 自定义构造函数
```javascript
function Person() {
    // this是一个指针
    // 构造函数当中的this指向 new出来的实例对象  面试常考
    this.name = '张三';
    this.age = 20;
    this.child = {
        name: '小明',
        age: 3
    };
    this.say = function() {
        alert(this.name)
    }
}
var obj3 = new Person;
console.log(obj3);
obj3.say();
console.log(obj3);
// 如果不通过new实例对象,那么this指向调用者!!!
// 谁调用this就指向谁
window.Person(); //Person
// window对象调用了 person函数,那么 其中的this就指向 window
console.log(window);
```
### JSON对象
```javascript
var obj = {
    a: 'Hello',
    b: 'World'
};
//这是一个对象
var json = '{"a":"hello","b":"world"}';
//这是一个 JSON 字符串，本质是一个字符串,可以进行网络传输

var movieJson = {
        "title": "西虹市首富",
        "directors": "闫非",
        "year": "2018",
    }
    // 这是一个json对象,依然是对象 ,不能进行网络传输

var objStr = '{a: "Hello", b: "World"}';
console.log(obj.a);//==>Hello
var jsonObj = JSON.parse(json);
// 需要把json 字符串 转换为 JSON对象
// 只有json 字符串能转换为JSon对象
// var obj1 = JSON.parse(objStr); // 报错
// console.log(obj1);
console.log(jsonObj.a);//==>hello

// 向后台传输数据,需要把对象转换为json字符串
var movieStr = JSON.stringify(movieJson);
console.log(movieStr);//==>'{"title":"西虹市首富","directors":"闫非","year":"2018"}'
// 也可以把 普通对象 转换为 json字符串
var str = JSON.stringify(obj);
console.log(str);//==>'{"a":"Hello","b":"World"}'
```
### 对象的遍历
```javascript
//for in 用于对象(json对象也可以)的遍历
var movieJson = {
    "title": "西虹市首富",
    "directors": "闫非",
    "year": "2018"
}
for (var key in movieJson) {
    console.log(key);//==>title 西虹市首富 directors
    // key是变量 需要用 obj[key]的形式获取对象属性值
    console.log(movieJson[key]);//==>闫非 year 2018
    // /xx.xx 这种形式 只能取原来具有的属性
    //非常重要! xx.abc  abc是变量,就必须通过  xx[abc] 形式取值
}
```
### 对象遍历案例
```javascript
// console.log(movies);
// 打印所有电影名字
// 获取所有电影信息
var subjects = movies.subjects;
// console.log(subjects);
for (var i = 0; i < subjects.length; i++) {
    // subjects[i]  是 每一部电影信息
    // 打印电影信息
    var dir = subjects[i].directors,
        dirName = '';
    for (let j = 0; j < dir.length; j++) {
        dirName += dir[j].name + '/';
    }
    dirName = dirName.substr(0, dirName.length - 1);
    console.log('电影名字:' + subjects[i].title + ',导演:' + dirName);
     打印  '电影名字:西红柿首富,导演:闫飞/彭大魔'
}
//movies对象
var movies = {
	"count": 20,
	"start": 0,
	"total": 27,
	"subjects": [{
		"rating": {
			"max": 10,
			"average": 6.7,
			"stars": "35",
			"min": 0
		},
		"genres": ["喜剧"],
		"title": "西虹市首富",
		"casts": [{
			"alt": "https://movie.douban.com/celebrity/1325700/",
			"avatars": {
				"small": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1356510694.28.webp",
				"large": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1356510694.28.webp",
				"medium": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1356510694.28.webp"
			},
			"name": "沈腾",
			"id": "1325700"
		}, {
			"alt": "https://movie.douban.com/celebrity/1341903/",
			"avatars": {
				"small": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1446281965.79.webp",
				"large": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1446281965.79.webp",
				"medium": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1446281965.79.webp"
			},
			"name": "宋芸桦",
			"id": "1341903"
		}, {
			"alt": "https://movie.douban.com/celebrity/1322777/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1413261818.41.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1413261818.41.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1413261818.41.webp"
			},
			"name": "张一鸣",
			"id": "1322777"
		}],
		"collect_count": 228674,
		"original_title": "西虹市首富",
		"subtype": "movie",
		"directors": [{
			"alt": "https://movie.douban.com/celebrity/1350410/",
			"avatars": {
				"small": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1437030925.47.webp",
				"large": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1437030925.47.webp",
				"medium": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1437030925.47.webp"
			},
			"name": "闫非",
			"id": "1350410"
		}, {
			"alt": "https://movie.douban.com/celebrity/1350409/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1437031053.5.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1437031053.5.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1437031053.5.webp"
			},
			"name": "彭大魔",
			"id": "1350409"
		}],
		"year": "2018",
		"images": {
			"small": "http://img3.doubanio.com/view/photo/s_ratio_poster/public/p2529206747.webp",
			"large": "http://img3.doubanio.com/view/photo/s_ratio_poster/public/p2529206747.webp",
			"medium": "http://img3.doubanio.com/view/photo/s_ratio_poster/public/p2529206747.webp"
		},
		"alt": "https://movie.douban.com/subject/27605698/",
		"id": "27605698"
	}, {
		"rating": {
			"max": 10,
			"average": 7.4,
			"stars": "40",
			"min": 0
		},
		"genres": ["动画", "奇幻"],
		"title": "风语咒",
		"casts": [{
			"alt": "https://movie.douban.com/celebrity/1329887/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1370588849.4.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1370588849.4.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1370588849.4.webp"
			},
			"name": "路知行",
			"id": "1329887"
		}, {
			"alt": "https://movie.douban.com/celebrity/1340811/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1478049229.21.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1478049229.21.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1478049229.21.webp"
			},
			"name": "阎萌萌",
			"id": "1340811"
		}, {
			"alt": "https://movie.douban.com/celebrity/1390805/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1522323624.45.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1522323624.45.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1522323624.45.webp"
			},
			"name": "褚珺",
			"id": "1390805"
		}],
		"collect_count": 5552,
		"original_title": "风语咒",
		"subtype": "movie",
		"directors": [{
			"alt": "https://movie.douban.com/celebrity/1364166/",
			"avatars": {
				"small": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1501141090.9.webp",
				"large": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1501141090.9.webp",
				"medium": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1501141090.9.webp"
			},
			"name": "刘阔",
			"id": "1364166"
		}],
		"year": "2018",
		"images": {
			"small": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2528298441.webp",
			"large": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2528298441.webp",
			"medium": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2528298441.webp"
		},
		"alt": "https://movie.douban.com/subject/30146756/",
		"id": "30146756"
	}, {
		"rating": {
			"max": 10,
			"average": 8.8,
			"stars": "45",
			"min": 0
		},
		"genres": ["剧情", "犯罪", "家庭"],
		"title": "小偷家族",
		"casts": [{
			"alt": "https://movie.douban.com/celebrity/1042693/",
			"avatars": {
				"small": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p19077.webp",
				"large": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p19077.webp",
				"medium": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p19077.webp"
			},
			"name": "中川雅也",
			"id": "1042693"
		}, {
			"alt": "https://movie.douban.com/celebrity/1274350/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1442220877.34.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1442220877.34.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1442220877.34.webp"
			},
			"name": "安藤樱",
			"id": "1274350"
		}, {
			"alt": "https://movie.douban.com/celebrity/1320978/",
			"avatars": {
				"small": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1428591465.76.webp",
				"large": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1428591465.76.webp",
				"medium": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1428591465.76.webp"
			},
			"name": "松冈茉优",
			"id": "1320978"
		}],
		"collect_count": 34038,
		"original_title": "万引き家族",
		"subtype": "movie",
		"directors": [{
			"alt": "https://movie.douban.com/celebrity/1274351/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1363134033.35.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1363134033.35.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1363134033.35.webp"
			},
			"name": "是枝裕和",
			"id": "1274351"
		}],
		"year": "2018",
		"images": {
			"small": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2529394955.webp",
			"large": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2529394955.webp",
			"medium": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2529394955.webp"
		},
		"alt": "https://movie.douban.com/subject/27622447/",
		"id": "27622447"
	}, {
		"rating": {
			"max": 10,
			"average": 6.9,
			"stars": "35",
			"min": 0
		},
		"genres": ["喜剧", "动作", "犯罪"],
		"title": "的士速递5",
		"casts": [{
			"alt": "https://movie.douban.com/celebrity/1350461/",
			"avatars": {
				"small": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1439837122.18.webp",
				"large": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1439837122.18.webp",
				"medium": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1439837122.18.webp"
			},
			"name": "弗兰克·盖思堂彼得",
			"id": "1350461"
		}, {
			"alt": "https://movie.douban.com/celebrity/1338536/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1508296892.32.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1508296892.32.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1508296892.32.webp"
			},
			"name": "马利克·班泽拉",
			"id": "1338536"
		}, {
			"alt": "https://movie.douban.com/celebrity/1340833/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1424004495.1.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1424004495.1.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1424004495.1.webp"
			},
			"name": "伯纳尔·法西",
			"id": "1340833"
		}],
		"collect_count": 535,
		"original_title": "Taxi 5",
		"subtype": "movie",
		"directors": [{
			"alt": "https://movie.douban.com/celebrity/1350461/",
			"avatars": {
				"small": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1439837122.18.webp",
				"large": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1439837122.18.webp",
				"medium": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1439837122.18.webp"
			},
			"name": "弗兰克·盖思堂彼得",
			"id": "1350461"
		}],
		"year": "2018",
		"images": {
			"small": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2529136453.webp",
			"large": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2529136453.webp",
			"medium": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2529136453.webp"
		},
		"alt": "https://movie.douban.com/subject/27615564/",
		"id": "27615564"
	}, {
		"rating": {
			"max": 10,
			"average": 0,
			"stars": "00",
			"min": 0
		},
		"genres": ["喜剧", "动作", "犯罪"],
		"title": "解码游戏",
		"casts": [{
			"alt": "https://movie.douban.com/celebrity/1275667/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1519976356.71.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1519976356.71.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1519976356.71.webp"
			},
			"name": "韩庚",
			"id": "1275667"
		}, {
			"alt": "https://movie.douban.com/celebrity/1274684/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1372773609.01.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1372773609.01.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1372773609.01.webp"
			},
			"name": "凤小岳",
			"id": "1274684"
		}, {
			"alt": "https://movie.douban.com/celebrity/1314374/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1439792310.44.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1439792310.44.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1439792310.44.webp"
			},
			"name": "李媛",
			"id": "1314374"
		}],
		"collect_count": 81,
		"original_title": "解码游戏",
		"subtype": "movie",
		"directors": [{
			"alt": "https://movie.douban.com/celebrity/1388759/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1521528597.3.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1521528597.3.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1521528597.3.webp"
			},
			"name": "李海龙",
			"id": "1388759"
		}],
		"year": "2018",
		"images": {
			"small": "http://img3.doubanio.com/view/photo/s_ratio_poster/public/p2523515546.webp",
			"large": "http://img3.doubanio.com/view/photo/s_ratio_poster/public/p2523515546.webp",
			"medium": "http://img3.doubanio.com/view/photo/s_ratio_poster/public/p2523515546.webp"
		},
		"alt": "https://movie.douban.com/subject/26767512/",
		"id": "26767512"
	}, {
		"rating": {
			"max": 10,
			"average": 6.6,
			"stars": "35",
			"min": 0
		},
		"genres": ["动作", "悬疑", "古装"],
		"title": "狄仁杰之四大天王",
		"casts": [{
			"alt": "https://movie.douban.com/celebrity/1274608/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p49483.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p49483.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p49483.webp"
			},
			"name": "赵又廷",
			"id": "1274608"
		}, {
			"alt": "https://movie.douban.com/celebrity/1275721/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p36925.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p36925.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p36925.webp"
			},
			"name": "冯绍峰",
			"id": "1275721"
		}, {
			"alt": "https://movie.douban.com/celebrity/1314535/",
			"avatars": {
				"small": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1399987210.67.webp",
				"large": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1399987210.67.webp",
				"medium": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1399987210.67.webp"
			},
			"name": "林更新",
			"id": "1314535"
		}],
		"collect_count": 91903,
		"original_title": "狄仁杰之四大天王",
		"subtype": "movie",
		"directors": [{
			"alt": "https://movie.douban.com/celebrity/1007152/",
			"avatars": {
				"small": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1393840734.39.webp",
				"large": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1393840734.39.webp",
				"medium": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1393840734.39.webp"
			},
			"name": "徐克",
			"id": "1007152"
		}],
		"year": "2018",
		"images": {
			"small": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2526405034.webp",
			"large": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2526405034.webp",
			"medium": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2526405034.webp"
		},
		"alt": "https://movie.douban.com/subject/25882296/",
		"id": "25882296"
	}, {
		"rating": {
			"max": 10,
			"average": 0,
			"stars": "00",
			"min": 0
		},
		"genres": ["动画"],
		"title": "神秘世界历险记4",
		"casts": [{
			"alt": "https://movie.douban.com/celebrity/1395143/",
			"avatars": {
				"small": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1528456334.7.webp",
				"large": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1528456334.7.webp",
				"medium": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1528456334.7.webp"
			},
			"name": "阎么么",
			"id": "1395143"
		}, {
			"alt": "https://movie.douban.com/celebrity/1392959/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1531717367.71.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1531717367.71.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1531717367.71.webp"
			},
			"name": "赵一博",
			"id": "1392959"
		}, {
			"alt": "https://movie.douban.com/celebrity/1340809/",
			"avatars": {
				"small": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1526278703.48.webp",
				"large": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1526278703.48.webp",
				"medium": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1526278703.48.webp"
			},
			"name": "张磊",
			"id": "1340809"
		}],
		"collect_count": 49,
		"original_title": "神秘世界历险记4",
		"subtype": "movie",
		"directors": [{
			"alt": "https://movie.douban.com/celebrity/1321732/",
			"avatars": {
				"small": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1436771114.49.webp",
				"large": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1436771114.49.webp",
				"medium": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1436771114.49.webp"
			},
			"name": "王云飞",
			"id": "1321732"
		}, {
			"alt": "https://movie.douban.com/celebrity/1360428/",
			"avatars": {
				"small": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1526278577.39.webp",
				"large": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1526278577.39.webp",
				"medium": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1526278577.39.webp"
			},
			"name": "张林旭",
			"id": "1360428"
		}, {
			"alt": "https://movie.douban.com/celebrity/1337468/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1435053152.21.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1435053152.21.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1435053152.21.webp"
			},
			"name": "李佳怡",
			"id": "1337468"
		}],
		"year": "2018",
		"images": {
			"small": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2528380655.webp",
			"large": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2528380655.webp",
			"medium": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2528380655.webp"
		},
		"alt": "https://movie.douban.com/subject/30208005/",
		"id": "30208005"
	}, {
		"rating": {
			"max": 10,
			"average": 7.2,
			"stars": "35",
			"min": 0
		},
		"genres": ["喜剧", "爱情", "歌舞"],
		"title": "妈妈咪呀2",
		"casts": [{
			"alt": "https://movie.douban.com/celebrity/1318674/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1426508419.1.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1426508419.1.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1426508419.1.webp"
			},
			"name": "莉莉·詹姆斯",
			"id": "1318674"
		}, {
			"alt": "https://movie.douban.com/celebrity/1053586/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p4902.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p4902.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p4902.webp"
			},
			"name": "阿曼达·塞弗里德",
			"id": "1053586"
		}, {
			"alt": "https://movie.douban.com/celebrity/1031902/",
			"avatars": {
				"small": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1484993245.89.webp",
				"large": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1484993245.89.webp",
				"medium": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1484993245.89.webp"
			},
			"name": "朱丽·沃特斯",
			"id": "1031902"
		}],
		"collect_count": 1208,
		"original_title": "Mamma Mia! Here We Go Again",
		"subtype": "movie",
		"directors": [{
			"alt": "https://movie.douban.com/celebrity/1319911/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p48233.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p48233.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p48233.webp"
			},
			"name": "欧·帕克",
			"id": "1319911"
		}],
		"year": "2018",
		"images": {
			"small": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2528272481.webp",
			"large": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2528272481.webp",
			"medium": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2528272481.webp"
		},
		"alt": "https://movie.douban.com/subject/27050259/",
		"id": "27050259"
	}, {
		"rating": {
			"max": 10,
			"average": 8.9,
			"stars": "45",
			"min": 0
		},
		"genres": ["剧情", "喜剧"],
		"title": "我不是药神",
		"casts": [{
			"alt": "https://movie.douban.com/celebrity/1274297/",
			"avatars": {
				"small": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p43738.webp",
				"large": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p43738.webp",
				"medium": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p43738.webp"
			},
			"name": "徐峥",
			"id": "1274297"
		}, {
			"alt": "https://movie.douban.com/celebrity/1313837/",
			"avatars": {
				"small": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1496577458.38.webp",
				"large": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1496577458.38.webp",
				"medium": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1496577458.38.webp"
			},
			"name": "王传君",
			"id": "1313837"
		}, {
			"alt": "https://movie.douban.com/celebrity/1276085/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1514533436.1.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1514533436.1.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1514533436.1.webp"
			},
			"name": "周一围",
			"id": "1276085"
		}],
		"collect_count": 1067044,
		"original_title": "我不是药神",
		"subtype": "movie",
		"directors": [{
			"alt": "https://movie.douban.com/celebrity/1349765/",
			"avatars": {
				"small": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1529658740.26.webp",
				"large": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1529658740.26.webp",
				"medium": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1529658740.26.webp"
			},
			"name": "文牧野",
			"id": "1349765"
		}],
		"year": "2018",
		"images": {
			"small": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2519070834.webp",
			"large": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2519070834.webp",
			"medium": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2519070834.webp"
		},
		"alt": "https://movie.douban.com/subject/26752088/",
		"id": "26752088"
	}, {
		"rating": {
			"max": 10,
			"average": 6.6,
			"stars": "35",
			"min": 0
		},
		"genres": ["动作", "惊悚", "冒险"],
		"title": "摩天营救",
		"casts": [{
			"alt": "https://movie.douban.com/celebrity/1044707/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p45621.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p45621.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p45621.webp"
			},
			"name": "道恩·强森",
			"id": "1044707"
		}, {
			"alt": "https://movie.douban.com/celebrity/1027828/",
			"avatars": {
				"small": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1532109034.28.webp",
				"large": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1532109034.28.webp",
				"medium": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1532109034.28.webp"
			},
			"name": "内芙·坎贝尔",
			"id": "1027828"
		}, {
			"alt": "https://movie.douban.com/celebrity/1036774/",
			"avatars": {
				"small": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p23588.webp",
				"large": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p23588.webp",
				"medium": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p23588.webp"
			},
			"name": "黄经汉",
			"id": "1036774"
		}],
		"collect_count": 79396,
		"original_title": "Skyscraper",
		"subtype": "movie",
		"directors": [{
			"alt": "https://movie.douban.com/celebrity/1005149/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1377869988.64.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1377869988.64.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1377869988.64.webp"
			},
			"name": "罗森·马歇尔·瑟伯",
			"id": "1005149"
		}],
		"year": "2018",
		"images": {
			"small": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2527484082.webp",
			"large": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2527484082.webp",
			"medium": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2527484082.webp"
		},
		"alt": "https://movie.douban.com/subject/26804147/",
		"id": "26804147"
	}, {
		"rating": {
			"max": 10,
			"average": 7.1,
			"stars": "35",
			"min": 0
		},
		"genres": ["剧情", "喜剧", "动作"],
		"title": "邪不压正",
		"casts": [{
			"alt": "https://movie.douban.com/celebrity/1013782/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1368156632.65.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1368156632.65.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1368156632.65.webp"
			},
			"name": "彭于晏",
			"id": "1013782"
		}, {
			"alt": "https://movie.douban.com/celebrity/1007401/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1454644679.84.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1454644679.84.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1454644679.84.webp"
			},
			"name": "廖凡",
			"id": "1007401"
		}, {
			"alt": "https://movie.douban.com/celebrity/1021999/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1517818343.94.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1517818343.94.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1517818343.94.webp"
			},
			"name": "姜文",
			"id": "1021999"
		}],
		"collect_count": 306270,
		"original_title": "邪不压正",
		"subtype": "movie",
		"directors": [{
			"alt": "https://movie.douban.com/celebrity/1021999/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1517818343.94.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1517818343.94.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1517818343.94.webp"
			},
			"name": "姜文",
			"id": "1021999"
		}],
		"year": "2018",
		"images": {
			"small": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2526297221.webp",
			"large": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2526297221.webp",
			"medium": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2526297221.webp"
		},
		"alt": "https://movie.douban.com/subject/26366496/",
		"id": "26366496"
	}, {
		"rating": {
			"max": 10,
			"average": 5.6,
			"stars": "30",
			"min": 0
		},
		"genres": ["喜剧", "动画", "奇幻"],
		"title": "神奇马戏团之动物饼干",
		"casts": [{
			"alt": "https://movie.douban.com/celebrity/1041022/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p21481.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p21481.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p21481.webp"
			},
			"name": "艾米莉·布朗特",
			"id": "1041022"
		}, {
			"alt": "https://movie.douban.com/celebrity/1027146/",
			"avatars": {
				"small": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1452855116.89.webp",
				"large": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1452855116.89.webp",
				"medium": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1452855116.89.webp"
			},
			"name": "约翰·卡拉辛斯基",
			"id": "1027146"
		}, {
			"alt": "https://movie.douban.com/celebrity/1054410/",
			"avatars": {
				"small": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1453792417.87.webp",
				"large": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1453792417.87.webp",
				"medium": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1453792417.87.webp"
			},
			"name": "伊恩·麦克莱恩",
			"id": "1054410"
		}],
		"collect_count": 5308,
		"original_title": "Magical Circus : Animal Crackers",
		"subtype": "movie",
		"directors": [{
			"alt": "https://movie.douban.com/celebrity/1277815/",
			"avatars": {
				"small": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1500617178.26.webp",
				"large": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1500617178.26.webp",
				"medium": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1500617178.26.webp"
			},
			"name": "托尼·班克罗夫特",
			"id": "1277815"
		}, {
			"alt": "https://movie.douban.com/celebrity/1206807/",
			"avatars": {
				"small": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1500623271.8.webp",
				"large": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1500623271.8.webp",
				"medium": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1500623271.8.webp"
			},
			"name": "斯科特·克里斯汀·萨瓦",
			"id": "1206807"
		}],
		"year": "2017",
		"images": {
			"small": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2528298973.webp",
			"large": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2528298973.webp",
			"medium": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2528298973.webp"
		},
		"alt": "https://movie.douban.com/subject/26253783/",
		"id": "26253783"
	}, {
		"rating": {
			"max": 10,
			"average": 5.0,
			"stars": "25",
			"min": 0
		},
		"genres": ["儿童", "动画", "冒险"],
		"title": "新大头儿子和小头爸爸3：俄罗斯奇遇记",
		"casts": [{
			"alt": "https://movie.douban.com/celebrity/1318433/",
			"avatars": {
				"small": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p44177.webp",
				"large": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p44177.webp",
				"medium": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p44177.webp"
			},
			"name": "刘纯燕",
			"id": "1318433"
		}, {
			"alt": "https://movie.douban.com/celebrity/1318435/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p44180.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p44180.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p44180.webp"
			},
			"name": "董浩",
			"id": "1318435"
		}, {
			"alt": "https://movie.douban.com/celebrity/1274251/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1494778054.15.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1494778054.15.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1494778054.15.webp"
			},
			"name": "鞠萍",
			"id": "1274251"
		}],
		"collect_count": 7167,
		"original_title": "新大头儿子和小头爸爸3：俄罗斯奇遇记",
		"subtype": "movie",
		"directors": [{
			"alt": "https://movie.douban.com/celebrity/1342907/",
			"avatars": {
				"small": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1469705072.9.webp",
				"large": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1469705072.9.webp",
				"medium": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1469705072.9.webp"
			},
			"name": "何澄",
			"id": "1342907"
		}],
		"year": "2018",
		"images": {
			"small": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2522820714.webp",
			"large": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2522820714.webp",
			"medium": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2522820714.webp"
		},
		"alt": "https://movie.douban.com/subject/30198729/",
		"id": "30198729"
	}, {
		"rating": {
			"max": 10,
			"average": 8.1,
			"stars": "40",
			"min": 0
		},
		"genres": ["喜剧", "动作", "动画"],
		"title": "超人总动员2",
		"casts": [{
			"alt": "https://movie.douban.com/celebrity/1002721/",
			"avatars": {
				"small": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p21297.webp",
				"large": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p21297.webp",
				"medium": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p21297.webp"
			},
			"name": "格雷格·T·尼尔森",
			"id": "1002721"
		}, {
			"alt": "https://movie.douban.com/celebrity/1031838/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p48614.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p48614.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p48614.webp"
			},
			"name": "霍利·亨特",
			"id": "1031838"
		}, {
			"alt": "https://movie.douban.com/celebrity/1186797/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1529654136.33.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1529654136.33.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1529654136.33.webp"
			},
			"name": "莎拉·沃威尔",
			"id": "1186797"
		}],
		"collect_count": 106242,
		"original_title": "Incredibles 2",
		"subtype": "movie",
		"directors": [{
			"alt": "https://movie.douban.com/celebrity/1027204/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1529655910.45.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1529655910.45.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1529655910.45.webp"
			},
			"name": "布拉德·伯德",
			"id": "1027204"
		}],
		"year": "2018",
		"images": {
			"small": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2522880251.webp",
			"large": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2522880251.webp",
			"medium": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2522880251.webp"
		},
		"alt": "https://movie.douban.com/subject/25849049/",
		"id": "25849049"
	}, {
		"rating": {
			"max": 10,
			"average": 5.9,
			"stars": "30",
			"min": 0
		},
		"genres": ["喜剧", "冒险"],
		"title": "汪星卧底",
		"casts": [{
			"alt": "https://movie.douban.com/celebrity/1044709/",
			"avatars": {
				"small": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p7197.webp",
				"large": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p7197.webp",
				"medium": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p7197.webp"
			},
			"name": "威尔·阿奈特",
			"id": "1044709"
		}, {
			"alt": "https://movie.douban.com/celebrity/1049714/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1373705281.63.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1373705281.63.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1373705281.63.webp"
			},
			"name": "卢达克里斯",
			"id": "1049714"
		}, {
			"alt": "https://movie.douban.com/celebrity/1040517/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p26071.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p26071.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p26071.webp"
			},
			"name": "斯坦利·图齐",
			"id": "1040517"
		}],
		"collect_count": 2475,
		"original_title": "Show Dogs",
		"subtype": "movie",
		"directors": [{
			"alt": "https://movie.douban.com/celebrity/1036533/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p5860.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p5860.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p5860.webp"
			},
			"name": "拉加·高斯内尔",
			"id": "1036533"
		}],
		"year": "2018",
		"images": {
			"small": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2526399205.webp",
			"large": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2526399205.webp",
			"medium": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2526399205.webp"
		},
		"alt": "https://movie.douban.com/subject/26930056/",
		"id": "26930056"
	}, {
		"rating": {
			"max": 10,
			"average": 6.8,
			"stars": "35",
			"min": 0
		},
		"genres": ["动作", "科幻", "冒险"],
		"title": "侏罗纪世界2",
		"casts": [{
			"alt": "https://movie.douban.com/celebrity/1017967/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1408711300.32.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1408711300.32.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1408711300.32.webp"
			},
			"name": "克里斯·帕拉特",
			"id": "1017967"
		}, {
			"alt": "https://movie.douban.com/celebrity/1027772/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p315.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p315.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p315.webp"
			},
			"name": "布莱丝·达拉斯·霍华德",
			"id": "1027772"
		}, {
			"alt": "https://movie.douban.com/celebrity/1350981/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1523860646.23.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1523860646.23.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1523860646.23.webp"
			},
			"name": "贾斯蒂斯·史密斯",
			"id": "1350981"
		}],
		"collect_count": 190212,
		"original_title": "Jurassic World: Fallen Kingdom",
		"subtype": "movie",
		"directors": [{
			"alt": "https://movie.douban.com/celebrity/1305510/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1372318484.25.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1372318484.25.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1372318484.25.webp"
			},
			"name": "胡安·安东尼奥·巴亚纳",
			"id": "1305510"
		}],
		"year": "2018",
		"images": {
			"small": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2522069454.webp",
			"large": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2522069454.webp",
			"medium": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2522069454.webp"
		},
		"alt": "https://movie.douban.com/subject/26416062/",
		"id": "26416062"
	}, {
		"rating": {
			"max": 10,
			"average": 0,
			"stars": "00",
			"min": 0
		},
		"genres": ["历史", "战争"],
		"title": "浴血广昌",
		"casts": [{
			"alt": "https://movie.douban.com/celebrity/1384169/",
			"avatars": {
				"small": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1511950470.56.webp",
				"large": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1511950470.56.webp",
				"medium": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1511950470.56.webp"
			},
			"name": "卢秋宏",
			"id": "1384169"
		}, {
			"alt": "https://movie.douban.com/celebrity/1326695/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1492423392.22.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1492423392.22.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1492423392.22.webp"
			},
			"name": "何达",
			"id": "1326695"
		}, {
			"alt": "https://movie.douban.com/celebrity/1317855/",
			"avatars": {
				"small": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p41469.webp",
				"large": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p41469.webp",
				"medium": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p41469.webp"
			},
			"name": "郑昊",
			"id": "1317855"
		}],
		"collect_count": 262,
		"original_title": "浴血广昌",
		"subtype": "movie",
		"directors": [{
			"alt": "https://movie.douban.com/celebrity/1319184/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p46010.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p46010.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p46010.webp"
			},
			"name": "高峰",
			"id": "1319184"
		}, {
			"alt": "https://movie.douban.com/celebrity/1327101/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1532071022.25.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1532071022.25.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1532071022.25.webp"
			},
			"name": "张馨",
			"id": "1327101"
		}],
		"year": "2018",
		"images": {
			"small": "http://img3.doubanio.com/view/photo/s_ratio_poster/public/p2529260597.webp",
			"large": "http://img3.doubanio.com/view/photo/s_ratio_poster/public/p2529260597.webp",
			"medium": "http://img3.doubanio.com/view/photo/s_ratio_poster/public/p2529260597.webp"
		},
		"alt": "https://movie.douban.com/subject/27180974/",
		"id": "27180974"
	}, {
		"rating": {
			"max": 10,
			"average": 0,
			"stars": "00",
			"min": 0
		},
		"genres": ["爱情", "歌舞"],
		"title": "三十那年",
		"casts": [{
			"alt": "https://movie.douban.com/celebrity/1398491/",
			"avatars": {
				"small": "http://img3.doubanio.com/f/movie/ca527386eb8c4e325611e22dfcb04cc116d6b423/pics/movie/celebrity-default-small.png",
				"large": "http://img7.doubanio.com/f/movie/63acc16ca6309ef191f0378faf793d1096a3e606/pics/movie/celebrity-default-large.png",
				"medium": "http://img3.doubanio.com/f/movie/8dd0c794499fe925ae2ae89ee30cd225750457b4/pics/movie/celebrity-default-medium.png"
			},
			"name": "尤天翔",
			"id": "1398491"
		}, {
			"alt": "https://movie.douban.com/celebrity/1398492/",
			"avatars": {
				"small": "http://img3.doubanio.com/f/movie/ca527386eb8c4e325611e22dfcb04cc116d6b423/pics/movie/celebrity-default-small.png",
				"large": "http://img7.doubanio.com/f/movie/63acc16ca6309ef191f0378faf793d1096a3e606/pics/movie/celebrity-default-large.png",
				"medium": "http://img3.doubanio.com/f/movie/8dd0c794499fe925ae2ae89ee30cd225750457b4/pics/movie/celebrity-default-medium.png"
			},
			"name": "张颖冰",
			"id": "1398492"
		}, {
			"alt": "https://movie.douban.com/celebrity/1327158/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1362572723.03.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1362572723.03.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1362572723.03.webp"
			},
			"name": "秦汉擂",
			"id": "1327158"
		}],
		"collect_count": 5,
		"original_title": "三十那年",
		"subtype": "movie",
		"directors": [{
			"alt": "https://movie.douban.com/celebrity/1398490/",
			"avatars": {
				"small": "http://img3.doubanio.com/f/movie/ca527386eb8c4e325611e22dfcb04cc116d6b423/pics/movie/celebrity-default-small.png",
				"large": "http://img7.doubanio.com/f/movie/63acc16ca6309ef191f0378faf793d1096a3e606/pics/movie/celebrity-default-large.png",
				"medium": "http://img3.doubanio.com/f/movie/8dd0c794499fe925ae2ae89ee30cd225750457b4/pics/movie/celebrity-default-medium.png"
			},
			"name": "郑小东",
			"id": "1398490"
		}],
		"year": "2018",
		"images": {
			"small": "http://img3.doubanio.com/view/photo/s_ratio_poster/public/p2529362957.webp",
			"large": "http://img3.doubanio.com/view/photo/s_ratio_poster/public/p2529362957.webp",
			"medium": "http://img3.doubanio.com/view/photo/s_ratio_poster/public/p2529362957.webp"
		},
		"alt": "https://movie.douban.com/subject/30285932/",
		"id": "30285932"
	}, {
		"rating": {
			"max": 10,
			"average": 7.3,
			"stars": "40",
			"min": 0
		},
		"genres": ["剧情", "动作", "冒险"],
		"title": "动物世界",
		"casts": [{
			"alt": "https://movie.douban.com/celebrity/1314140/",
			"avatars": {
				"small": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1403196522.98.webp",
				"large": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1403196522.98.webp",
				"medium": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1403196522.98.webp"
			},
			"name": "李易峰",
			"id": "1314140"
		}, {
			"alt": "https://movie.douban.com/celebrity/1053620/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p4023.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p4023.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p4023.webp"
			},
			"name": "迈克尔·道格拉斯",
			"id": "1053620"
		}, {
			"alt": "https://movie.douban.com/celebrity/1274224/",
			"avatars": {
				"small": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p36798.webp",
				"large": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p36798.webp",
				"medium": "http://img3.doubanio.com/view/celebrity/s_ratio_celebrity/public/p36798.webp"
			},
			"name": "周冬雨",
			"id": "1274224"
		}],
		"collect_count": 203068,
		"original_title": "动物世界",
		"subtype": "movie",
		"directors": [{
			"alt": "https://movie.douban.com/celebrity/1314828/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p38015.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p38015.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p38015.webp"
			},
			"name": "韩延",
			"id": "1314828"
		}],
		"year": "2018",
		"images": {
			"small": "http://img3.doubanio.com/view/photo/s_ratio_poster/public/p2525528688.webp",
			"large": "http://img3.doubanio.com/view/photo/s_ratio_poster/public/p2525528688.webp",
			"medium": "http://img3.doubanio.com/view/photo/s_ratio_poster/public/p2525528688.webp"
		},
		"alt": "https://movie.douban.com/subject/26925317/",
		"id": "26925317"
	}, {
		"rating": {
			"max": 10,
			"average": 6.8,
			"stars": "35",
			"min": 0
		},
		"genres": ["剧情"],
		"title": "北方一片苍茫",
		"casts": [{
			"alt": "https://movie.douban.com/celebrity/1377028/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1532313486.15.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1532313486.15.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1532313486.15.webp"
			},
			"name": "田天",
			"id": "1377028"
		}, {
			"alt": "https://movie.douban.com/celebrity/1398259/",
			"avatars": {
				"small": "http://img3.doubanio.com/f/movie/ca527386eb8c4e325611e22dfcb04cc116d6b423/pics/movie/celebrity-default-small.png",
				"large": "http://img7.doubanio.com/f/movie/63acc16ca6309ef191f0378faf793d1096a3e606/pics/movie/celebrity-default-large.png",
				"medium": "http://img3.doubanio.com/f/movie/8dd0c794499fe925ae2ae89ee30cd225750457b4/pics/movie/celebrity-default-medium.png"
			},
			"name": "韩建玲",
			"id": "1398259"
		}, {
			"alt": "https://movie.douban.com/celebrity/1398253/",
			"avatars": {
				"small": "http://img3.doubanio.com/f/movie/ca527386eb8c4e325611e22dfcb04cc116d6b423/pics/movie/celebrity-default-small.png",
				"large": "http://img7.doubanio.com/f/movie/63acc16ca6309ef191f0378faf793d1096a3e606/pics/movie/celebrity-default-large.png",
				"medium": "http://img3.doubanio.com/f/movie/8dd0c794499fe925ae2ae89ee30cd225750457b4/pics/movie/celebrity-default-medium.png"
			},
			"name": "赵树林",
			"id": "1398253"
		}],
		"collect_count": 5167,
		"original_title": "北方一片苍茫",
		"subtype": "movie",
		"directors": [{
			"alt": "https://movie.douban.com/celebrity/1376541/",
			"avatars": {
				"small": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1506670355.4.webp",
				"large": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1506670355.4.webp",
				"medium": "http://img7.doubanio.com/view/celebrity/s_ratio_celebrity/public/p1506670355.4.webp"
			},
			"name": "蔡成杰",
			"id": "1376541"
		}],
		"year": "2017",
		"images": {
			"small": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2527454845.webp",
			"large": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2527454845.webp",
			"medium": "http://img7.doubanio.com/view/photo/s_ratio_poster/public/p2527454845.webp"
		},
		"alt": "https://movie.douban.com/subject/27079318/",
		"id": "27079318"
	}],
	"title": "正在上映的电影-北京"
}
```
### 数组高级API
+ 合并 concat()
+ 添加 unshift()/push()
+ 删除 shift()/pop()
+ 把数组转换为字符串toString()
    ```javascript
    var arr = ['a', 'b', 'c', 'd'];
    // 把数组转换为字符串,默认用逗号隔开
    console.log(arr.toString());//==>'a', 'b', 'c', 'd'
    ```
+ reverse 反转数组
    ```javascript
    console.log(arr);//==>['a', 'b', 'c', 'd']
    arr.reverse(); // 会改变原数组==>['a', 'b', 'c', 'd']
    console.log(arr);//==>['d', 'c', 'b', 'a']
    ```
+ 给数组排序sort()
    - 返回排序后的数组,如何排序看参数:
        - 无参：按照数组元素的首字符对应的Unicode编码值从小到大排列数组元素。
        - 带参：必须为函数（回调函数--callback）。函数中带有两个参数,代表数组中的前后元素。如果计算后（a-b），返回值为负数，a排b前面。等于0不动。返回值为正数，a排b后面。
    ```javascript
    var arr1 = [1, 2, 4, 3, 13];
    arr1.sort(); //改变原数组
    console.log(arr1);//==>[ 1, 13, 2, 3, 4 ]
    arr1.sort(function(a, b) { return a - b; })//==>[ 1, 2, 3, 4, 13 ]
    console.log(arr1);//==>[ 1, 2, 3, 4, 13 ]
    ```
+ 返回对应数值在数组中的下标indexOf()、lastIndexOf()
    ```javascript
    var arr2 = ['张三', '李四', '李四', '王五'];
    // 从左往右查找对应元素
    console.log(arr2.indexOf('李四')); // 1
    console.log(arr2.indexOf('王五')); // 3
    // 从后往前查找对应元素
    console.log(arr2.lastIndexOf('李四')); // 2
    // 如果查找不到 返回-1
    console.log(arr2.indexOf('小明')); // -1
    ```
+ 从当前数组中截取一个新的数组，不影响原来的数组slice(start,end)
    ```javascript
    // 参数start从0开始,end从1开始 [start,end)
    var arr3 = [1, 2, 3, 4, 5, 6];
    var newArr3 = arr3.slice(1, 4);
    console.log(newArr3); //[ 2, 3, 4 ]
    console.log(arr3.slice(0)); //复制数组0可写可不写
    ```
+ 删除或替换当前数组的某些项目splice(start,deleteCount,options(要替换的项目))
    ```javascript
    var arr4 = ['a', 'b', 'c', 8, 9];
    arr4.splice(0, 1, 89, 0);
    console.log(arr4); //[ 89, 0, 'c', 8, 9 ]
    arr4.splice(1, 2); // 不写替换元素,就实现了删除
    console.log(arr4); //[ 89, 8, 9 ]
    // 删除 arr4 里边的 9 这个元素
    arr4.splice(arr4.indexOf(9), 1)
    console.log(arr4); //[ 89, 8 ]
    ```
+ 清空数组
    ```javascript
    // arr.length = 0;
    // arr = [];
    var arr5 = [1, 2, 3];
    arr5.length = 0;
    // arr5 = [];
    console.log(arr5);
    ```
### string方法
+ charAt() / charCodeAt()
    ```javascript
    var str = 'how are you? and you?'
    console.log(str.length); // 21
    // charAt()获取相应位置字符
    // 空格也 占位置
    console.log(str.charAt(5)); //r
    // charCodeAt() 方法可返回指定位置字符的 Unicode 编码
    console.log(str.charCodeAt(5)); // 114
    ```
+ indexOf() / lastIndexOf()
    ```javascript
    // 返回字符在字符串中的位置
    console.log(str.indexOf('y')); // 8
    console.log(str.lastIndexOf('y')); // 17
    console.log(str.indexOf('2')); // -1
    ```
+ concat() 连接字符串
    ```javascript
    var str2 = ' me too';
    console.log(str.concat(str2));//how are you? and you? me too
    ```
+ slice()
    ```javascript
    //提取字符串的某个部分，并以新的字符串返回被提取的部分
    console.log(str.slice(0, 9)); // how are y
    console.log(str.slice()); // how are you? and you?
    console.log(str.slice(1, 4)); // 'ow '
    ```
+ toUpperCase()/toLowerCase()
    ```javascript
    //转换大小写
    console.log(str.toUpperCase()); // HOW ARE YOU? AND YOU?
    console.log(str);
    console.log(str.toLowerCase()); // how are you? and you?
    ```
### 练习-1
```javascript
// ['刘备','张飞','关羽'] ===> '刘备|张飞|关羽'
var arr = ['刘备', '关于', '张飞'],
    str = arr.join('|');
console.log(str);
```
### 练习-2
```javascript
// 找到数组中每个字母出现的次数["c","a","z","a","a","z","b"]
var arr = ["c", "a", "z", "a", "a", "z", "b"];
function foo(arr) {
    var obj = {};
    for (let i = 0; i < arr.length; i++) {
        if (!obj[arr[i]]) {
            obj[arr[i]] = 0;
        }
        obj[arr[i]]++;
    }
    return obj;
}
console.log(foo(arr));
```
### 练习-3
工资的数组[1500,1200,2000,2100,1800],把工资超过2000的删除
```javascript
var arr = [1500, 1200, 2000, 2100, 2200, 2300, 1800];
// 方法一
function foo(arr, num) {
    arr1 = [];
    for (let i = 0; i < arr.length; i++) {
        if (arr[i] <= num) {
            arr1.push(arr[i]);
        }
    }
    arr = [];
    arr = arr1;
    return arr;
}
console.log(foo(arr, 2000));

// 方法二
function foo1(arr, num) {
    for (let i = 0; i < arr.length; i++) {
        if (arr[i] > num) {
            arr.splice(i, 1);
            i--;//==>下标减一,避免错漏连续第二个符合条件的元素
        }
    }
    return arr;
}
console.log(foo1(arr, 2000));
```

