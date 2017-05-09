# testResponsive 遇到的知识点

### 值得参考的网站
* [browerhack 各种浏览器兼容性写法](http://browserhacks.com/)
* [html5shiv 让不支持html5的浏览器支持html5](https://github.com/aFarkas/html5shiv)
* [腻子 抹平浏览器的差异性](https://github.com/Modernizr/Modernizr/wiki/HTML5-Cross-Browser-Polyfills)
* [对不确定的元素主动检测兼容性](https://modernizr.com/download?setclasses)
* [查看浏览器的兼容性情况](https://caniuse.com/)
* [npm](https://www.npmjs.com/)
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

需要注意的是，为了兼容不支持 rem 的浏览器，我们需要在各个使用了 rem 地方前面写上对应的 px 值，这样不支持的浏览器可以优雅降级。兼容性详情。

选择使用什么字体单位主要由你的项目来决定，如果你的用户群都使用最新版的浏览器，那推荐使用 rem，如果要考虑兼容性，那就使用 px，或者两者同时使用。
