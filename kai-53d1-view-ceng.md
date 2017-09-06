# View布局开发

> _必须先声明一下.. 我是一个完全没有html，css，js基础的android开发人员，所以这次的开发在view层面，我不会在页面美化上费太多时间，只要能完成需求即可，主心骨还是业务逻辑处理以及http交互等。_

那么，Dashboard 页面暂且保持不变，先从 ‘记一笔’ 页面渲染开始

> ### **src/pages/take/take-bill.html**

```
<ion-header>
  <ion-navbar>
    <button ion-button menuToggle>
      <ion-icon name="menu"></ion-icon>
    </button>
    <ion-title>记一笔</ion-title>
  </ion-navbar>
</ion-header>

<ion-content padding>
  <ion-list inset>
    <ion-item>
      <ion-label>日期</ion-label>
      <ion-datetime displayFormat="MM月DD日" min="2017" max="2017" [(ngModel)]="currentDate"></ion-datetime>
    </ion-item>
    <ion-item>
      <ion-label>消费类型</ion-label>
      <ion-select [(ngModel)]="consumeType">
        <ion-option value="consume1">日常开销</ion-option>
        <ion-option value="consume2">购物</ion-option>
        <ion-option value="consume3">餐饮</ion-option>
        <ion-option value="consume4">娱乐</ion-option>
        <ion-option value="consume5">请客</ion-option>
      </ion-select>
    </ion-item>
    <ion-item>
      <ion-label>消费金额</ion-label>
      <!-- Possible values are: "text", "password", "email", "number", "search", "tel", or "url". -->
      <ion-input type="number" value=""></ion-input>
    </ion-item>

    <button ion-button class="take-bill center" color="danger" round center>+ 记一笔</button>
  </ion-list>
</ion-content>
```

> ### **src/pages/take/take-bill.ts**

```
import { Component } from '@angular/core';
import { NavController, Events } from 'ionic-angular';

@Component({
  selector: 'page-take-bill',
  templateUrl: 'take-bill.html'
})

export class TakeBillPage {

  constructor(public navCtrl: NavController, public events: Events) { 
    
  }

    // console.log((new Date().getMonth() + 1) + '月' + new Date().getDate() + '日');
  currentDate: any =  (new Date().getMonth() + 1) + '月' + new Date().getDate() + '日';
  consumeType: any = '日常开销';
}
```



