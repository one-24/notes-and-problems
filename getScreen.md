#pc 端 rem 适配
##1、利用 JS 或者 @media 媒体查询设置 html 的font-size 
**js 代码如下**
```javascript
window.onload = function () {
    function getRem() {
        var whdef = 100 / 1920;// 1920图,使用100PX的默认值
        var wH = window.innerHeight;// 当前窗口的高度
        var wW = window.innerWidth;// 当前窗口的宽度
        wW = wW - 17;   //  减掉滚动条的宽度
        var rem = wW * whdef;// 以默认比例值乘以当前窗口宽度,得到该宽度下的相应FONT-SIZE值
        document.getElementsByTagName("html")[0].style.fontSize = rem + "px";
        //console.log(rem + "px")
    }
    getRem();
    window.onresize = getRem;
}
```
**媒体查询**
以下媒体查询是减掉 滚动条的宽度   如果不减掉17px 会撑出横向滚动条   1920 的设计图 100px 为基数   计算公式为 `100/1920 * ( 分辨率宽度 - 17 )`  
```css
@media screen and (min-width: 1024px) {
    html {
        font-size: 52.44px
    }
}
/*>=1024的设备屏幕*/

@media screen and (min-width: 1100px) {
    html {
        font-size: 56.4px
    }
}
/*>=1100的设备屏幕*/

@media screen and (min-width: 1280px) {
    html {
        font-size: 65.78px;
    }
}
/*>=1280的设备屏幕*/

@media screen and (min-width: 1366px) {
    html {
        font-size: 70.26px !important;
    }
}
/*>=1366的设备屏幕*/

@media screen and (min-width: 1440px) {
    html {
        font-size: 74.11px !important;
    }
}
/*>=1440的设备屏幕*/

@media screen and (min-width: 1680px) {
    html {
        font-size: 86.61px;
    }
}
/*>=1680的设备屏幕*/

@media screen and (min-width: 1920px) {
    html {
        font-size: 99.11px;
    }
}
```

如果设计图纸 是 1920 那么 开发时候的 font-size 以 100px 为基准   基准值就取决于设计图


#手机端 适配
##淘宝 flexible 适配方案
手机端的设计图一般是 750 
1、引入两个 js 文件
`flexible_css.debug.js`
`flexible.debug.js`
后 在chrome 调试器选择 iphone6 就可以看到 html 的 font-size 已经是 75px ;
2、不用写
`<meta name="viewport" content="width=device-width,minimum-scale=1.0,maximum-scale=1.0,user-scalable=no"/>`
flexible.js 自动生成   此时的 html 根元素的 font-size 也是自动根据手机屏幕大小设置   所以可以直接以 rem 为单位
3、选择 @2x 倍图   和  @3x 倍图
例如以下代码   dpr 是 flexible 适配生成的一个标准 
[data-dpr="3"] 大屏幕的时候使用高倍图

```css
#download-left {
    float: left;
    height: 1.0666666666666667rem;
    width: 0.4533333333333333rem;
    background: url(../img/安卓2x.png) no-repeat left center;
    background-size: 100%;
    margin-right: 0.7333333333333333rem;
}
[data-dpr="3"] #download-left {
    background: url(../img/安卓3x.png) no-repeat left center;    
  }
```


