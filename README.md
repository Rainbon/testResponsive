# testResponsive 遇到的知识点

### 值得参考的网站
* [browerhack 各种浏览器兼容性写法](http://browserhacks.com/)
* [html5shiv 让不支持html5的浏览器支持html5](https://github.com/aFarkas/html5shiv)
* [腻子 抹平浏览器的差异性](https://github.com/Modernizr/Modernizr/wiki/HTML5-Cross-Browser-Polyfills)
* [对不确定的元素主动检测兼容性](https://modernizr.com/download?setclasses)
* [查看浏览器的兼容性情况](https://caniuse.com/)
* [npm 查看npm安装的包信息](https://www.npmjs.com/)
* [在多设备上调试实现同步的效果](https://www.browsersync.io/)
* [http-server服务部署](https://github.com/indexzero/http-server)

### 如何区别 px、em、rem

- `px` 在缩放页面时无法调整那些使用它作为单位的字体、按钮等的大小；
- `em` 的值并不是固定的，会继承父级元素的字体大小，代表倍数；
- `rem` 的值并不是固定的，始终是基于根元素 <html> 的，也代表倍数。

#### em

em 的使用是相对于其父级的字体大小的，即倍数。浏览器的默认字体高都是 16px，未经调整的浏览器显示 1em = 16px。但是由于 em 是相对于其父级字体的倍数的，当出现有多重嵌套内容时，使用 em 分别给它们设置字体的大小往往要重新计算。比如说你在父级中声明了字体大小为 1.2em，那么在声明子元素的字体大小时设置 1em 才能和父级元素内容字体大小一致，而不是1.2em（避免 1.2*1.2=1.44em）, 因为此 em 非彼 em。

#### rem

rem 的出现再也不用担心还要根据父级元素的 font-size 计算 em 值了，因为它始终是基于根元素（<html>）的。
比如默认的 html font-size=16px，那么想设置 12px 的文字就是：12÷16=0.75(rem)

#### 注意事项
谷歌浏览器默认字体大小最小是12px,如果为了计算方便而将html根元素字体设置为10px,即html{font-size:10px;}

此时子元素使用rem时来设置字体大小以及height\width等要注意:

1. 当字体大小小于12px时浏览器一律显示12px,如p{font-size:0.9rem;}，实际浏览器将p元素内字体大小以1.2rem显示

2. 当rem设置height\width时rem和px转换比是1：12，并非1:10。原因：谷歌浏览器默认字体大小最小是12px

一般来说，如果需要统一字体大小，建议用 rem，但有些局部，相对动态需要根据父元素字体来设置大小的，会选用 em。另外还有一些比较特殊的情况，比如需要与固定像素的图片配合布局等，那就要用到 px 了。

### 媒体查询

* [only screen参考文章](http://www.jianshu.com/p/2dfa5bab1ef1)
* [媒体查询中only not的理解](https://developer.mozilla.org/zh-CN/docs/Web/Guide/CSS/Media_queries)

### 从第一个li的兄弟元素开始

像头部导航 左右两边没有竖线 其他都用竖线隔开就可以使用这种方法实现：

``````
header .top ul li + li { /* 从第一个li的兄弟元素开始 及第二个li开始执行该代码*/
    border-left: 1px solid #999;
    margin-left: -3px;
}
``````

### calc的使用场景

* [calc的使用介绍 例子](http://www.w3cplus.com/css3/how-to-use-css3-calc-function.html)
* [box-sizing和calc的比较](http://www.w3cplus.com/css3/imitating-calc-fallback-fixed-width-sidebar-in-responsive-layout.html)

### 多余的文字 隐藏 不换行 省略号 显示

``````
p{
    display: inline-block;
    width: 200px;
    height: 20px;
    line-height: 20px;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
}
``````

### 清除浮动的实用方法

最实用的方法

``````

.clearfix:before,.clearfix:after{
    content: '';
    display: table;
}
.clearfix:after{
    clear: both;
}
``````

### grayscale灰度级

``````
 -webkit-filter: grayscale(100%); /*CSS3 grayscale滤镜图片变黑白*/
 filter: grayscale(100%);
``````