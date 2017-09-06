# View布局开发

> _必须先声明一下.. 我是一个完全没有html，css，js基础的android开发人员，所以这次的开发在view层面，我不会在页面美化上费太多时间，只要能完成需求即可，主心骨还是业务逻辑处理以及http交互等。_

那么，Dashboard 页面暂且保持不变，先从 ‘记一笔’ 页面渲染开始

# Take\(记一笔\)

---

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

![](/assets/take-bill.png)

# Bills\(账单\)

---

> ### **src/pages/bills/bills.html**

```
<ion-header>
  <ion-navbar>
    <button ion-button menuToggle>
      <ion-icon name="menu"></ion-icon>
    </button>
    <ion-title>账单</ion-title>
  </ion-navbar>
</ion-header>

<ion-content padding>
  <ion-list>
    <button ion-item *ngFor="let item of items" (click)="itemTapped($event, item)">
        <ion-icon [name]="item.bill.consume_type_info.consume_type_icon" item-left></ion-icon>
        {{item.bill.consume_type_info.consume_type_name}}
        <div class="item-note" item-right>
          {{item.bill.consume_amount}}
        </div>
      </button>
  </ion-list>
  <div *ngIf="selectedItem" padding>
    You navigated here from <br>
    type => <b>{{selectedItem.bill.consume_type_info.consume_type_name}}</b> 
    and 
    amount => <b>{{selectedItem.bill.consume_amount}}</b>
  </div>
</ion-content>
```

> ### **src/pages/bills/bills.ts**

```
import { Component } from '@angular/core';
import { NavController, NavParams } from 'ionic-angular';

import { Bill } from '../../model/bill.model';
// import { ConsumeType } from '../../model/consume-type.model';

@Component({
  selector: 'page-bills',
  templateUrl: 'bills.html'
})
export class BillsPage {

  selectedItem: any;
  icons: string[];
  consumeTypeNames: string[];

  items: Array<{ bill: Bill }>;

  constructor(public navCtrl: NavController, public navParams: NavParams) {
    // If we navigated to this page, we will have an item available as a nav param
    this.selectedItem = navParams.get('item');

    // Let's populate this page with some filler content for funzies 官方提供的icon名称
    this.icons = ['flask', 'wifi', 'beer', 'football', 'basketball', 'paper-plane',
      'american-football', 'boat', 'bluetooth', 'build'];
    this.consumeTypeNames = ['日常开销', '购物', '餐饮', '娱乐', '请客', '聚会', '贷款'];

    this.items = [];
    for (var index = 0; index < 6; index++) {
      this.items.push({
        bill: {
          /** 账单id */
          bill_id: index,
          /** 账单所属消费类型 */
          consume_type_info: {
            /** 消费类型id */
            consume_type_id: index,
            /** 消费类型名称 */
            consume_type_name: this.consumeTypeNames[Math.floor(Math.random() * this.consumeTypeNames.length)],
            /** 消费类型 图标 */
            consume_type_icon: this.icons[Math.floor(Math.random() * this.icons.length)]
          },
          /** 账单 支出金额 */
          consume_amount: index * index + 15.7,
          /** 账单时间 */
          bill_date_format: (new Date().getMonth() + 1) + '月' + new Date().getDate() + '日'
        }
      })
    }
  }

  itemTapped(event, item) {
    // That's right, we're pushing to ourselves!
    this.navCtrl.push(BillsPage, {
      item: item
    });
  }
}

```

![](/assets/bills.png)  ==&gt;  ![](/assets/bills-click-switch.png)

