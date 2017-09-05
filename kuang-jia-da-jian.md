# 框架搭建

下面是 Angular 项目的基本结构，Ionic 结构在此基础上多了些原生构建以及view层级的扩展，不过都是依赖于此。

```
angular-tour-of-heroes
...src   //文件夹是项目的根文件夹之一。 其它文件是用来帮助你构建、测试、维护、文档化和发布应用的。
......app
.........app.component.ts   //app.component.{ts,html,css,spec.ts} => 使用HTML模板、CSS样式和单元测试定义AppComponent组件。 它是根组件，随着应用的成长它会成为一棵组件树的根节点。
.........app.component.html
.........app.component.css
.........app.module.ts   //定义AppModule，这个根模块会告诉Angular如何组装该应用。 目前，它只声明了AppComponent。 稍后它还会声明更多组件。
.........app.component.spec.ts
......assets   //这个文件夹下你可以放图片等任何东西，在构建应用时，它们全都会拷贝到发布包中。
..........gitkeep
......environments   //为各个目标环境准备的文件，它们导出了一些应用中要用到的配置变量。
.........environment.prod.ts
.........environment.ts
......favicon.ico   //每个网站都希望自己在书签栏中能好看一点。 请把它换成你自己的图标。
......main.ts   //这是应用的主要入口点。 使用JIT compiler编译器编译本应用，并启动应用的根模块AppModule，使其运行在浏览器中。
......index.html   //这是别人访问你的网站是看到的主页面的HTML文件。 大多数情况下你都不用编辑它。 在构建应用时，CLI会自动把所有js和css文件添加进去，所以你不必在这里手动添加任何 <script> 或 <link> 标签。
......styles.css   //这里是你的全局样式。 大多数情况下，你会希望在组件中使用局部样式，以利于维护，不过那些会影响你整个应用的样式你还是需要集中存放在这里。
......polyfills.ts   //不同的浏览器对Web标准的支持程度也不同。 填充库（polyfill）能帮我们把这些不同点进行标准化。 你只要使用core-js 和 zone.js通常就够了
......test.ts   //这是单元测试的主要入口点。 它有一些你不熟悉的自定义配置，不过你并不需要编辑这里的任何东西。
......systemjs.config.js
......tsconfig.json   //tsconfig.{app|spec} TypeScript编译器的配置文件。tsconfig.app.json是为Angular应用准备的，而tsconfig.spec.json是为单元测试准备的。
......node_modules 
......package.json

/** 备注：这里记录了主要的文件概况，还有更多关于项目结构的更多用途信息，可以查看官方文档，更详细：https://angular.cn/guide/quickstart#项目文件概览 */
```

sidemenu框架创建后，会在src下面创建 pages

```
src
...app
...pages
......home //首页
......list //列表页
```

首先，在 项目需求 中已说明，项目需求的menu是 **Dashboard、记一笔、账单**，所以，我会把目录更改为以下结构：

```
src
...app
...pages
......bills //账单列表页面
.........bills.html 
.........bills.scss
.........bills.ts
......dashboard //仪表盘
.........dashboard.html
.........dashboard.scss
.........dashboard.ts
......take //记一笔
.........take-bill.html
.........take-bill.scss
.........take-bill.ts
```

ts中导出每个组件，例如：记一笔；其他逻辑基本相同

```
import { Component } from '@angular/core';
import { NavController } from 'ionic-angular';

@Component({
  selector: 'page-take-bill',
  templateUrl: 'take-bill.html'
})
export class TakeBillPage {

  constructor(public navCtrl: NavController) {

  }

}
```

基本的项目架子已经成形，下面需要为架子创建对象，也就是定义model数据，同样在 src 下面创建文件夹 model

```
src
...app
...pages
...model
......bill.model.ts //账单对象
......consume-type.model.ts  //消费类型对象
......member.model.ts  //会员详情对象
......account.model.ts  //会员帐户资产对象
```

> 注意：
>
> TypeScript中对于数字只有这么一种类型，没有byte、short、int、uint、long、float、double等类型，而TypeScript的number实际上是一个64为的双精度浮点数，可以看做其它语言中的double类型 !!!





