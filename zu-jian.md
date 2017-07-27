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

### 四.按钮

按钮是与应用程序交互和浏览应用程序的重要方式，并应清楚地说明用户点击后将采取什么反应。 按钮可以由文本和/或图标组成，并且可以通过各种属性进行增强。

由于可访问性原因，按钮使用标签&lt;button&gt;元素，但是ion-button使用指令进行了增强。

详细信息,请参考API;

其中包括:

* [Default Style](http://ionicframework.com/docs/components/#buttons)\(默认样式\)
* [Outline Style](http://ionicframework.com/docs/components/#outline-buttons)\(outline文字样式\)
* [Clear Style](http://ionicframework.com/docs/components/#clear-buttons)\(文字样式\)
* [Round Buttons](http://ionicframework.com/docs/components/#round-buttons)\(圆边角样式\)
* [Block Buttons](http://ionicframework.com/docs/components/#block-buttons)\(block样式\)
* [Full Buttons](http://ionicframework.com/docs/components/#full-buttons)\(宽度全屏样式\)
* [Button Sizes](http://ionicframework.com/docs/components/#button-sizes)\(按钮大小\)
* [Icon Buttons](http://ionicframework.com/docs/components/#icon-buttons)\(图标按钮\)
* [Buttons In Components](http://ionicframework.com/docs/components/#buttons-in-components)\(组件中的按钮\)

#### 默认样式                                                                                                                                               [ 示例代码](https://github.com/ionic-team/ionic-preview-app/tree/master/src/pages/buttons/basic)

```
<button ion-button>Button</button>
```

color属性设置按钮的颜色。 Ionic包括许多默认颜色，可以轻松覆盖：

![](/assets/默认按钮ios.png)![](/assets/默认按钮Android.png)

```
<button ion-button color="light">Light</button>
<button ion-button>Default</button>
<button ion-button color="secondary">Secondary</button>
<button ion-button color="danger">Danger</button>
<button ion-button color="dark">Dark</button>
```

#### outline样式                                                                                                                                               [示例代码](https://github.com/ionic-team/ionic-preview-app/tree/master/src/pages/buttons/outline)

要使用outline样式的按钮，只需添加outline属性：

![](/assets/outline样式按钮ios.png)![](/assets/outline样式按钮Android.png)

```
<button ion-button color="light" outline>Light Outline</button>
<button ion-button outline>Primary Outline</button>
<button ion-button color="secondary" outline>Secondary Outline</button>
<button ion-button color="danger" outline>Danger Outline</button>
<button ion-button color="dark" outline>Dark Outline</button>
```

#### 文字样式                                                                                                                                                   [示例代码](https://github.com/ionic-team/ionic-preview-app/tree/master/src/pages/buttons/clear)

要使用文字样式的按钮，只需添加清除属性：

![](/assets/文字样式按钮ios.png)![](/assets/文字样式按钮Android.png)

```
<button ion-button color="light" clear>Light Clear</button>
<button ion-button clear>Primary Clear</button>
<button ion-button color="secondary" clear>Secondary Clear</button>
<button ion-button color="danger" clear>Danger Clear</button>
<button ion-button color="dark" clear>Dark Clear</button>
```

#### 圆边角样式                                                                                                                                               [示例代码](https://github.com/ionic-team/ionic-preview-app/tree/master/src/pages/buttons/round)

要创建一个带圆角的按钮，只需添加round属性：

![](/assets/圆角按钮ios.png)![](/assets/圆角按钮Android.png)

```
<button ion-button color="light" round>Light Round</button>
<button ion-button round>Primary Round</button>
<button ion-button color="secondary" round>Secondary Round</button>
<button ion-button color="danger" round>Danger Round</button>
<button ion-button color="dark" round>Dark Round</button>
```

#### block样式                                                                                                                                                 [示例代码](https://github.com/ionic-team/ionic-preview-app/tree/master/src/pages/buttons/block)

使按钮宽度占父元素的100%,这个按钮将会有diplay:block;属性

![](/assets/block按钮ios.png)![](/assets/block按钮Android.png)

```
<button ion-button block>Block Button</button>
```

#### 宽度全屏样式                                                                                                                                           [示例代码](https://github.com/ionic-team/ionic-preview-app/tree/master/src/pages/buttons/full)

添加full样式按钮也将使按钮占据其父宽度的100％。 但是，它也将删除按钮的左右边框。 当按钮伸展到显示屏的整个宽度时，此样式很有用。

![](/assets/全屏宽度按钮ios.png)![](/assets/全品宽度按钮Android.png)

```
<button ion-button full>Full Button</button>
```

#### 按钮大小                                                                                                                                                   [示例代码](https://github.com/ionic-team/ionic-preview-app/tree/master/src/pages/buttons/sizes)

添加大的属性以使按钮更大，或更小以使其更小：

![](/assets/按钮大小ios.png)![](/assets/按钮大小Android.png)

```
<button ion-button small>Small</button>
<button ion-button>Default</button>
<button ion-button large>Large</button>
```

#### 图标按钮                                                                                                                                                   [示例代码](https://github.com/ionic-team/ionic-preview-app/tree/master/src/pages/buttons/icons)

要向按钮添加图标，请在其中添加一个图标组件和一个position属性：

![](/assets/图标按钮ios.png)![](/assets/图标按钮Android.png)

```
<!-- Float the icon left -->
<button ion-button icon-left>
  <ion-icon name="home"></ion-icon>
  Left Icon
</button>

<!-- Float the icon right -->
<button ion-button icon-right>
  Right Icon
  <ion-icon name="home"></ion-icon>
</button>

<!-- Only icon (no text) -->
<button ion-button icon-only>
  <ion-icon name="home"></ion-icon>
</button>
```

#### 组件中的按钮                                                                                                                                            [示例代码](https://github.com/ionic-team/ionic-preview-app/tree/master/src/pages/buttons/components)

虽然按钮可以自己使用，但它们可以轻松地在其他组件中使用。 例如，可以将按钮添加到列表项或导航栏。

![](/assets/组件中的按钮.png)![](/assets/组件中按钮Android.png)

```
<ion-header>
  <ion-navbar>
    <ion-buttons start>
      <button ion-button icon-only>
        <ion-icon name="contact"></ion-icon>
      </button>
    </ion-buttons>

    <ion-buttons end>
      <button ion-button icon-only>
        <ion-icon name="search"></ion-icon>
      </button>
    </ion-buttons>
  </ion-navbar>
</ion-header>

<ion-list>
  <ion-item>
    Left Icon Button
    <button ion-button outline item-end icon-left>
      <ion-icon name="star"></ion-icon>
      Left Icon
    </button>
  </ion-item>
</ion-list>
```

### 卡片

卡片是显示重要内容的好方法，并且迅速成为应用程序的核心设计模式。 它们是控制和组织信息的好方法，同时也为用户设定了可预见的期望。 随着这么多的内容能够立即显示，并且经常这么小的屏幕不可靠，卡已经成为许多公司的选择的设计模式，包括Google，Twitter和Spotify等。

对于移动端，卡片可以轻松地通过许多不同的屏幕尺寸在视觉上显示相同的信息。 它们允许更多的控制，灵活，甚至可以动画。 动画常放置在彼此之间，但也可以像“页面”一样使用，并在左，右之间滑动。

其中包括:

* [Basic Cards](http://ionicframework.com/docs/components/#cards)\(基本卡片\)
* [Card Headers](http://ionicframework.com/docs/components/#card-header)\(含标题卡片\)
* [Card Lists](http://ionicframework.com/docs/components/#card-list)\(列表卡片\)
* [Card Images](http://ionicframework.com/docs/components/#card-image)\(含图片的卡片\)
* [Background Images](http://ionicframework.com/docs/components/#card-background)\(背景图片卡片\)
* [Advanced Cards](http://ionicframework.com/docs/components/#advanced-cards)\(集成卡片\)

#### 基本卡片                                                                                                                                                 [示例代码](/Basic Cards Card Headers Card Lists Card Images Background Images Advanced Cards)

卡主要是一个CSS组件。 要使用基本卡片，请遵循以下结构：

![](/assets/基本卡片ios.png)![](/assets/基本卡片Android.png)

```
<ion-card>

  <ion-card-header>
    Card Header
  </ion-card-header>

  <ion-card-content>
    <!-- Add card content here! -->
  </ion-card-content>

</ion-card>
```

#### 含标题卡片

就像普通页面一样，卡片可以自定义为包含标题。 要向卡添加标题，请在卡片内添加&lt;ion-card-header&gt;组件：

![](/assets/含标题ios.png)![](/assets/含标题卡片Android.png)

```
<ion-card>
  <ion-card-header>
    Header
  </ion-card-header>
  <ion-card-content>
    The British use the term "header", but the American term "head-shot" the English simply refuse to adopt.
  </ion-card-content>
</ion-card>
```

#### 列表卡片                                                                                                                                                  [示例代码](https://github.com/ionic-team/ionic-preview-app/tree/master/src/pages/cards/list)

卡可以包含项目列表。 在卡片内容中添加列表组件以显示列表：

![](/assets/列表卡片ios.png)![](/assets/列表卡片Android.png)

```
<ion-card>
  <ion-card-header>
    Explore Nearby
  </ion-card-header>

  <ion-list>
    <button ion-item>
      <ion-icon name="cart" item-start></ion-icon>
      Shopping
    </button>

    <button ion-item>
      <ion-icon name="medical" item-start></ion-icon>
      Hospital
    </button>

    <button ion-item>
      <ion-icon name="cafe" item-start></ion-icon>
      Cafe
    </button>

    <button ion-item>
      <ion-icon name="paw" item-start></ion-icon>
      Dog Park
    </button>

    <button ion-item>
      <ion-icon name="beer" item-start></ion-icon>
      Pub
    </button>

    <button ion-item>
      <ion-icon name="planet" item-start></ion-icon>
      Space
    </button>

  </ion-list>
</ion-card>
```

#### 含图片卡片                                                                                                                                              [示例代码](https://github.com/ionic-team/ionic-preview-app/tree/master/src/pages/cards/image)

图像的大小通常有所不同，因此在整个应用程序中采用一致的风格很重要。 图片可以轻松添加到卡片中。 将图像添加到卡片中将给予图像一个指定的宽度和一个可变的高度。 列表，标题和其他卡组件可以轻松地与图像卡组合。 要将图像添加到卡中，请使用以下代码：

![](/assets/含有图片卡片ios.png)![](/assets/含图片的卡片Android.png)

```
<ion-card>
  <img src="img/nin-live.png"/>
  <ion-card-content>
    <ion-card-title>
      Nine Inch Nails Live
      </ion-card-title>
    <p>
      The most popular industrial group ever, and largely
      responsible for bringing the music to a mass audience.
    </p>
  </ion-card-content>
</ion-card>
```

#### 背景图片卡片                                                                                                                                           [示例代码](https://github.com/ionic-team/ionic-preview-app/tree/master/src/pages/cards/background)

卡片可用于实现多种设计。 我们提供许多元素来实现常见的设计，但有时需要添加自定义样式。 将背景图像添加到卡片中是一个完美的例子，说明如何添加自定义样式可以实现完全不同的外观。

![](/assets/背景图片ios.png)![](/assets/背景图片Android.png)

```
<ion-content class="card-background-page">

  <ion-card>
    <img src="img/card-saopaolo.png"/>
    <div class="card-title">São Paulo</div>
    <div class="card-subtitle">41 Listings</div>
  </ion-card>

  <ion-card>
    <img src="img/card-amsterdam.png"/>
    <div class="card-title">Amsterdam</div>
    <div class="card-subtitle">64 Listings</div>
  </ion-card>

  <ion-card>
    <img src="img/card-sf.png"/>
    <div class="card-title">San Francisco</div>
    <div class="card-subtitle">72 Listings</div>
  </ion-card>

  <ion-card>
    <img src="img/card-madison.png"/>
    <div class="card-title">Madison</div>
    <div class="card-subtitle">28 Listings</div>
  </ion-card>

</ion-content>
```

#### 集成卡片                                                                                                                                                   示例代码



