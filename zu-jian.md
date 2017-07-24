# 组件

ionic app是由高级组件构建的,组件允许你快速地为你的应用程序构建界面,ionic有很多组件,包括模态框,弹框和卡片。下面是示例:你可以从里面了解每个组件的外观,并且了解每个组件的使用,一旦了解了这些,就可以直觉去阅读API文档,了解如何定制每个组件。

### 一.底部弹出框

底部弹出框是从设备的底部滑出,并且显示一组选项,可以确认或取消操作。有时候，底部弹出框可以用来作为菜单的替代品，但是它们不能用于导航。

底部弹出框总是可以出现在页面上的任何其他组件之上，为了与底层内容交互，必须对其进行忽略。当它被触发时，页面的其余部分就会变暗，从而将更多的焦点放在底部弹出框选项上。

要了解更多信息，请查看API文档。

![](/assets/import.png)![](/assets/底部弹出框Android.png)

#### 基本用法                                                                                                                                                   [示例代码](https://github.com/ionic-team/ionic-preview-app/tree/master/src/pages/action-sheets/basic)

```
import { ActionSheetController } from 'ionic-angular';

export class MyPage {
  constructor(public actionSheetCtrl: ActionSheetController) {
  }

  presentActionSheet() {
    let actionSheet = this.actionSheetCtrl.create({
      title: 'Modify your album',
      buttons: [
        {
          text: 'Destructive',
          role: 'destructive',
          handler: () => {
            console.log('Destructive clicked');
          }
        },{
          text: 'Archive',
          handler: () => {
            console.log('Archive clicked');
          }
        },{
          text: 'Cancel',
          role: 'cancel',
          handler: () => {
            console.log('Cancel clicked');
          }
        }
      ]
    });
    actionSheet.present();
  }
}
```

### 二.弹出框

弹出框是向用户提供选择特定操作或操作列表的一种很好的方式,它们还可以向用户提供重要的信息,或者要求他们做出决策\(或多个决策\)。

从UI的角度来看，弹出框可以被认为是一种仅浮动屏幕中的一部分“浮动”模式。 这意味着弹出框只能用于快速操作，如密码验证，小型应用通知或快速选项。 弹出的时候保留全屏模式。

弹出框是非常灵活的，可以轻松地定制。

要了解更多信息，请查看API文档。

其中包括:

* [Basic Alerts](http://ionicframework.com/docs/components/#alerts)\(基本弹出框\)
* [Prompt Alerts](http://ionicframework.com/docs/components/#alert-prompt)\(可输入弹出框\)
* [Confirmation Alerts](http://ionicframework.com/docs/components/#alert-confirm)\(确认信息弹出框\)
* [Radio Alerts](http://ionicframework.com/docs/components/#alert-radio)\(单选弹出框\)
* [Checkbox Alerts](http://ionicframework.com/docs/components/#alert-checkbox)\(多选弹出框\)

#### 基本弹出框                                                                                                                                                [示例代码](https://github.com/ionic-team/ionic-preview-app/tree/master/src/pages/alerts/basic)

基本弹出框常常应用于一些新信息\(应用程序的更改,新特性等\),一些情况的确认,或者用户是否确认.

![](/assets/基本弹出框.png)![](/assets/基本弹出框Android.png)

```
import { AlertController } from 'ionic-angular';

export class MyPage {
  constructor(public alertCtrl: AlertController) {
  }

  showAlert() {
    let alert = this.alertCtrl.create({
      title: 'New Friend!',
      subTitle: 'Your friend, Obi wan Kenobi, just accepted your friend request!',
      buttons: ['OK']
    });
    alert.present();
  }
}
```

#### 可输入弹出框                                                                                                                                        [示例代码](https://github.com/ionic-team/ionic-preview-app/tree/master/src/pages/alerts/prompt)

可输入弹出框提供了可输入数据或者信息,例如登录信息过期,提示用户输入密码.

![](/assets/可输入信息弹出框ios.png)![](/assets/可输入信息弹出框Android.png)

```
import { AlertController } from 'ionic-angular';

export class MyPage {
  constructor(public alertCtrl: AlertController) {
  }

  showPrompt() {
    let prompt = this.alertCtrl.create({
      title: 'Login',
      message: "Enter a name for this new album you're so keen on adding",
      inputs: [
        {
          name: 'title',
          placeholder: 'Title'
        },
      ],
      buttons: [
        {
          text: 'Cancel',
          handler: data => {
            console.log('Cancel clicked');
          }
        },
        {
          text: 'Save',
          handler: data => {
            console.log('Saved clicked');
          }
        }
      ]
    });
    prompt.present();
  }
}
```

#### 确认信息弹出框                                                                                                                                  [示例代码](https://github.com/ionic-team/ionic-preview-app/tree/master/src/pages/alerts/confirm)

当用户是否需要继续,确认选择这时候确认信息弹出框就会被用到,最典型的例子就是删除通讯录确认删除的弹出框.

![](/assets/确认信息弹出框ios.png)![](/assets/确认信息弹出框安卓.png)

```
import { AlertController } from 'ionic-angular';

export class MyPage {
  constructor(public alertCtrl: AlertController) {
  }

  showConfirm() {
    let confirm = this.alertCtrl.create({
      title: 'Use this lightsaber?',
      message: 'Do you agree to use this lightsaber to do good across the intergalactic galaxy?',
      buttons: [
        {
          text: 'Disagree',
          handler: () => {
            console.log('Disagree clicked');
          }
        },
        {
          text: 'Agree',
          handler: () => {
            console.log('Agree clicked');
          }
        }
      ]
    });
    confirm.present();
  }
}
```

#### 单选弹出框                                                                                                                                              [示例代码](https://github.com/ionic-team/ionic-preview-app/tree/master/src/pages/alerts/radio)

单选弹出框是一种确认弹出框,让用户做出选择,提供给用户一个选择的选项,但是只能选择一个选项.

![](/assets/单选弹出框ios.png)![](/assets/单选弹出框Android.png)

```
import { AlertController } from 'ionic-angular';

export class MyPage {
  constructor(public alertCtrl: AlertController) {
  }

  showRadio() {
    let alert = this.alertCtrl.create();
    alert.setTitle('Lightsaber color');

    alert.addInput({
      type: 'radio',
      label: 'Blue',
      value: 'blue',
      checked: true
    });

    alert.addButton('Cancel');
    alert.addButton({
      text: 'OK',
      handler: data => {
        this.testRadioOpen = false;
        this.testRadioResult = data;
      }
    });
    alert.present();
  }
}
```

#### 多选弹出框                                                                                                                                             [示例代码](https://github.com/ionic-team/ionic-preview-app/tree/master/src/pages/alerts/checkbox)

多选弹出框是一种确认弹出框，但使用多选框组件提供多种选择。 它们为用户提供一组可供选择的选项。

![](/assets/复选弹出框ios.png)![](/assets/复选弹出框Android.png)

```
import { AlertController } from 'ionic-angular';

export class MyPage {
  constructor(public alertCtrl: AlertController) {
  }

  showCheckbox() {
    let alert = this.alertCtrl.create();
    alert.setTitle('Which planets have you visited?');

    alert.addInput({
      type: 'checkbox',
      label: 'Alderaan',
      value: 'value1',
      checked: true
    });

    alert.addInput({
      type: 'checkbox',
      label: 'Bespin',
      value: 'value2'
    });

    alert.addButton('Cancel');
    alert.addButton({
      text: 'Okay',
      handler: data => {
        console.log('Checkbox data:', data);
        this.testCheckboxOpen = false;
        this.testCheckboxResult = data;
      }
    });
    alert.present();
  }
}
```

### 三.徽章                                                                                                                     [示例代码](https://github.com/ionic-team/ionic-preview-app/tree/master/src/pages/badges)

徽章是通常向用户传达数值的小组件。 它们通常用于一个项目。

![](/assets/徽章ios.png)![](/assets/徽章Android.png)

```
<ion-item>
  <ion-icon name="logo-twitter" item-start></ion-icon>
  Followers
  <ion-badge item-end>260k</ion-badge>
</ion-item>
```

徽章也可以赋予任何颜色属性：

```
<ion-badge color="secondary"></ion-badge>
```



