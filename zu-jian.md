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
* [Confirmation Alerts](http://ionicframework.com/docs/components/#alert-confirm)\(同意否决弹出框\)
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



