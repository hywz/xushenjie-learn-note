## 插件使用
### swiper插件
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <!-- 引入样式库 -->
    <link rel="stylesheet" href="css/swiper.min.css">
    <script src="../../lib/jquery-3.4.1.min.js"></script>
    <title>Document</title>
    <style>
        * {
            padding: 0;
            margin: 0;
        }
        
        .swiper-container {
            width: 1200px;
        }
        
        .swiper-slide img {
            width: 100%;
            /* height: 100%; */
        }
    </style>

</head>

<body>
    <div class="swiper-container">
        <div class="swiper-wrapper">
            <div class="swiper-slide">
                <div class="swiper-zoom-container">
                    <img src="img/1.jpg" alt="">
                </div>
            </div>
            <div class="swiper-slide">
                <div class="swiper-zoom-container">
                    <img src="img/2.jpg" alt="">
                </div>
            </div>
            <div class="swiper-slide">
                <div class="swiper-zoom-container">
                    <img src="img/3.jpg" alt="">
                </div>
            </div>
            <div class="swiper-slide">
                <div class="swiper-zoom-container">
                    <img src="img/4.jpg" alt="">
                </div>
            </div>
            <div class="swiper-slide">
                <div class="swiper-zoom-container">
                    <img src="img/5.jpg" alt="">
                </div>
            </div>
        </div>
        <!-- 如果需要分页器 -->
        <div class="swiper-pagination"></div>
    </div>
    <!-- 如果需要导航按钮 -->
    <div class="swiper-button-prev"></div>
    <div class="swiper-button-next"></div>

    <!-- 如果需要滚动条 -->
    <div class="swiper-scrollbar"></div>
    <!-- 导航等组件可以放在container之外 -->
    <!-- 引入依赖库 -->

    <!-- 引入核心库 -->
    <script src="js/swiper.min.js"></script>
    <script>
        var mySwiper = new Swiper('.swiper-container', {
                // initialSlide: 3,
                autoplay: true,
                direction: 'horizontal', // 垂直切换选项
                loop: true, // 循环模式选项

                // slide的切换效果
                effect: 'cube',
                // effect: 'flip',

                mousewheel: true, //开启鼠标滚轮控制Swiper切换


                // 如果需要分页器
                pagination: {
                    el: '.swiper-pagination',
                    type: 'bullets',
                    hideOnClick: true, //点击隐藏显示分页器
                    clickable: true, //点击分页器的指示点分页器会控制Swiper切换
                },

                // 如果需要前进后退按钮
                navigation: {
                    nextEl: '.swiper-button-next',
                    prevEl: '.swiper-button-prev',
                },

                // 如果需要滚动条
                scrollbar: {
                    el: '.swiper-scrollbar',
                },
                zoom: true, //双击放大/缩小
            })
            //鼠标覆盖停止自动切换
        mySwiper.$('.swiper-container')[0].onmouseover = function() {
            mySwiper.autoplay.stop();
        }
    </script>
</body>

</html>
```
### earch图表
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <!-- 引入 echarts 文件 -->
    <script src="https://cdn.bootcss.com/echarts/4.2.1-rc1/echarts-en.common.js"></script>
    <title>Document</title>
</head>

<body>
    <div id="main" style="width: 600px;height:400px;"></div>
</body>
<script type="text/javascript">
    // 基于准备好的dom，初始化echarts实例
    var myChart = echarts.init(document.getElementById('main'), 'dark');

    // 指定图表的配置项和数据
    var option = {
        title: {
            text: 'ECharts 入门示例'
        },
        tooltip: {},
        legend: {
            data: ['销量']
        },
        xAxis: {
            data: ["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋", "袜子"]
        },
        yAxis: {},
        series: [{
            name: '销量',
            type: 'bar',
            data: [5, 20, 36, 10, 10, 20]
        }]
    };

    // 使用刚指定的配置项和数据显示图表。
    myChart.setOption(option);
</script>

</html>
```
### 南丁格尔图
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <!-- 引入 echarts 文件 -->
    <script src="echarts/dist/echarts.min.js"></script>
    <script src="echarts/dist/echarts.js.map"></script>
    <title>Document</title>
    <style>
        * {
            padding: 0;
            margin: 0;
        }
    </style>
</head>

<body>
    <div id="main" style="width: 100%;height: 657px;"></div>
</body>
<script type="text/javascript">
    // 基于准备好的dom，初始化echarts实例
    var myChart = echarts.init(document.getElementById('main'), 'dark');

    // 指定图表的配置项和数据
    var option = {
        visualMap: {
            // 不显示 visualMap 组件，只用于明暗度的映射
            show: false,
            // 映射的最小值为 80
            min: 80,
            // 映射的最大值为 600
            max: 600,
            inRange: {
                // 明暗度的范围是 0 到 1
                colorLightness: [0, 1]
            }
        },
        tooltip: {
            trigger: 'item',
            formatter: "{a} <br/>{b} : {c} ({d}%)"
        },
        series: [{
            name: '访问来源',
            type: 'pie',
            color: ['#dd2d56', '#759aa0', '#e69d87', '#8dc1a9', '#ea9e33'],
            roseType: 'angle',
            radius: '55%',
            data: [{
                value: 235,
                name: '视频广告',
            }, {
                value: 274,
                name: '联盟广告'
            }, {
                value: 310,
                name: '邮件营销'
            }, {
                value: 335,
                name: '直接访问'
            }, {
                value: 400,
                name: '搜索引擎'
            }],
            itemStyle: {
                // 设置扇形的颜色
                // color: '#c23531',
                emphasis: {
                    shadowBlur: 200,
                    shadowColor: 'rgba(0, 0, 0, 0.5)',
                    // 阴影水平方向上的偏移
                    shadowOffsetX: 20,
                    // 阴影垂直方向上的偏移
                    shadowOffsetY: 20
                }
            },

        }],
        backgroundColor: '#2c343c',
        textStyle: {
            color: 'rgba(255, 255, 255, 0.3)'
        },
        label: {
            textStyle: {
                color: 'rgba(251, 252, 25, 0.3)'
            }
        },
        labelLine: {
            lineStyle: {
                color: 'rgba(255, 255, 255, 0.3)'
            }
        },
    };

    // 使用刚指定的配置项和数据显示图表。
    myChart.setOption(option);
</script>

</html>
```
### 地图
```html
<!DOCTYPE html>
<html>

<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <meta name="viewport" content="initial-scale=1.0, user-scalable=no" />
    <style type="text/css">
        body,
        html,
        #allmap {
            width: 100%;
            height: 100%;
            overflow: hidden;
            margin: 0;
            font-family: "微软雅黑";
        }
    </style>
    <script type="text/javascript" src="http://api.map.baidu.com/api?v=2.0&ak=你的密钥"></script>
    <title>地图展示</title>
</head>

<body>
    <div id="allmap"></div>
</body>

</html>
<script type="text/javascript">
    // 百度地图API功能
    var map = new BMap.Map("allmap"); // 创建Map实例
    map.centerAndZoom(new BMap.Point(113.64964385, 34.7566100641), 11); // 初始化地图,设置中心点坐标和地图级别
    //添加地图类型控件
    map.addControl(new BMap.MapTypeControl({
        mapTypes: [
            BMAP_NORMAL_MAP,
            BMAP_HYBRID_MAP
        ]
    }));
    map.setCurrentCity("郑州"); // 设置地图显示的城市 此项是必须设置的
    map.enableScrollWheelZoom(true); //开启鼠标滚轮缩放
</script>
```
