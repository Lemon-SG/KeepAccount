# 开发前准备

当然是环境配置咯～

Ionic 和 Angular 的环境配置其实不需要记录太多，官方文档都描述的很清楚。这里就简单走个过场～

这里有我前几天写的一篇关于 Angular 环境搭建的文章： [http://www.cnblogs.com/bbm7/p/7406619.html](http://www.cnblogs.com/bbm7/p/7406619.html)

不管怎样，node 肯定是必须的，再安装 npm，用 npm 可以安装到你想安装的一切～。～

> _题外话_
>
> _对了，之前看到过一篇文章，这里也贴一下，文章实在写的太好了！_
>
> _看完这篇文章，基本上前端大部分的技术你都有个大概的了解～大科普喔～哈哈 _[_https://zhuanlan.zhihu.com/p/22782487_](https://zhuanlan.zhihu.com/p/22782487)

```
// 安装ionic
$ npm install -g cordova ionic
// 安装后可以验证一下版本
$ ionic -version
3.9.2
-----------------------------------------------------------------
// 创建应用:KeepAccount是我的这个项目名称
$ ionic start KeepAccount sidemenu
$ cd KeepAccount/
// 在浏览器中运行项目，并且启动了本地服务端口，一般是8100，有了webpack，只需要修改代码，保存，浏览器会自动更新
$ ionic serve
```

> 关于创建应用，官方有明确的说明：
>
> If the tutorial template isn’t something you want to use, Ionic has a few templates available:
>
> * `tabs`: a simple 3 tab layout 
> * `sidemenu`: a layout with a swipable menu on the side
> * `blank`: a bare starter with a single page
> * `super`: starter project with over 14 ready to use page designs
> * `tutorial`: a guided starter project
>
> If you don’t specify a template by running`ionic start MyIonicProject`, the [tabs template](https://github.com/ionic-team/ionic2-starter-tabs) will be used.
>
> > 大概意思：创建应用不指定模版框架的话，默认是 tabs template，我这个项目我选择了 sidemenu 框架模版，所以在 start 时，就直接生成 sidemenu 即可。上面还有一个 tutorial 模版，这个模版就我感觉，应该跟 sidemenu 差不多吧，具体我还没深究～。～

备注：网上很多人都说要在后面追加ionic的版本号，像这样：ionic start KeepAccount --v2 ，事实上，我用的版本是3.9.2，如果这样启动项目的话，会报 **Sorry! The --v1 and --v2 flags have been removed. **错误，很明显，追加版本号在v3后应该是被废弃了的。



又啰嗦了一大堆。。。

