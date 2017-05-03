---
title: 如何使用Angular 2绑定表单元素
tags:
  - angular2
  - 数据绑定
abbrlink: 9f028a85
date: 2016-10-06 07:53:44
---
**概述**
ng2的数据绑定为用户表单操作提供了便捷性,用户一旦修改了单选钮选项、输入框值、复选框、下拉菜单,
绑定的对象属性就会修改,我们直接在ts|js中拿着用即可。
下面贴出主要的代码块。

**接口创建**
```
// user.interface.ts

export interface User {
    name: string; // text
    age?: number; // number
    gender?: string; // radio
    role?: string; // select (primitive)
    theme?: Theme; // select (object)
    topics?: string[]; // multiple select 
    isActive?: boolean; // checkbox
    toggle?: string; // checkbox toggle either 'toggled' or 'untoggled'
}
```

**在组件里创建对象并初始化值**
```
import { Component } from '@angular/core';
import { User } from './user.interface';
import { Theme } from './theme.interface';

@Component({
  moduleId: module.id,
  selector: 'my-app',
  templateUrl: 'app.component.html',
})
export class AppComponent {
  public user: User;

  public genders = [
    { value: 'F', display: 'Female' },
    { value: 'M', display: 'Male' }
  ];
  public roles = [
    { value: 'admin', display: 'Administrator' },
    { value: 'guest', display: 'Guest' },
    { value: 'custom', display: 'Custom' }
  ]

  public themes: Theme[] = [
    { backgroundColor: 'black', fontColor: 'white', display: 'Dark' },
    { backgroundColor: 'white', fontColor: 'black', display: 'Light' },
    { backgroundColor: 'grey', fontColor: 'white', display: 'Sleek' }
  ];

  public topics = [
    { value: 'game', display: 'Gaming' },
    { value: 'tech', display: 'Technology' },
    { value: 'life', display: 'Lifestyle' },
  ];

  public toggles = [
    { value: 'toggled', display: 'Toggled' },
    { value: 'untoggled', display: 'UnToggled' },
  ];

  public t = {
    true: { value: 'toggled', display: 'Toggled' },
    false: { value: 'untoggled', display: 'UnToggled' }
  }

  ngOnInit() {
    this.user = {
      name: '',
      gender: this.genders[0].value,
      role: null,
      theme: this.themes[0],
      isActive: false,
      toggle: this.toggles[1].value,
      topics: [this.topics[1].value]
    }
  }

  save(isValid: boolean, f: User) {
    if (!isValid) return;
    console.log(f);
  }
}

```
**视图模板遍历展示**
```
<div class="container">
  <h1>Add user</h1>
  <form #f="ngForm" novalidate>
    <div class="form-group">
      <label>Name</label>
      <input type="text" class="form-control" name="name" [(ngModel)]="user.name">
    </div>
    <div class="form-group">
      <label>Age</label>
      <input type="number" class="form-control" name="age" [(ngModel)]="user.age">
    </div>
    <div class="form-group">
      <label>Gender</label>
      <div class="radio" *ngFor="let gender of genders">
        <label>
          <input type="radio" name="gender" [(ngModel)]="user.gender" [value]="gender.value">
          {{gender.display}}
        </label>
      </div>
    </div>
    <div class="form-group">
      <label>Role</label>
      <select name="role" class="form-control" [(ngModel)]="user.role">
        <option *ngFor="let role of roles" [value]="role.value">{{role.display}}</option>
      </select>
    </div>
    <div class="form-group">
      <label>Theme</label>
      <select name="theme" class="form-control" [(ngModel)]="user.theme">
        <option *ngFor="let theme of themes" [ngValue]="theme">{{theme.display}}</option>
      </select>
    </div>
    <div class="form-group">
      <div class="checkbox">
        <label>
          <input type="checkbox" name="isActive" [(ngModel)]="user.isActive">
          Is Active
        </label>
      </div>
    </div>
    <div class="form-group">
      <label>Topics</label>
      <select multiple name="topics" class="form-control" [(ngModel)]="user.topics">
        <option *ngFor="let topic of topics" [value]="topic.value">{{topic.display}}</option>
      </select>
    </div>
    <div class="form-group">
      <input type="hidden" name="toggle" [(ngModel)]="user.toggle">
      <div class="checkbox">
        <label>
          <input type="checkbox" [checked]="user.toggle === toggles[0].value" 
              (change)="$event.target.checked? (user.toggle = toggles[0].value) : (user.toggle = toggles[1].value)">
          {{ toggles[0].display }}
        </label>
      </div>
    </div>
    <button type="submit" (click)="save(f.value, f.valid)" class="btn btn-default">Submit</button>
  </form>
  <div style="margin-top: 20px" *ngIf="f">
    <div>Form details:-</div>
    <pre>Is form valid?: <br>{{f.valid | json}}</pre>
    <pre>Is form submitted?: <br>{{f.submitted | json}}</pre>
    <pre>submitted value: <br>{{f.value | json}}</pre>
  </div>
</div>

```
