# COCOS
COCOS DEMO


------->[点击体验StarScoreGame](https://fairyly.github.io/COCOS/start_project/build/web-mobile/index.html)


## 预制资源（Prefab）

  即可创建出一个预制：在场景中编辑好节点后，直接将节点从 层级管理器 拖到 资源管理器：  
  即可创建出一个预制
  


## 切换场景

```
onLoad: function () {
    this.node.on('mousedown', function ( event ) { //监听鼠标点击事件
        console.log('Hello!');
        var sceneName = 'helloworld';
        var onLaunched = function () {
            console.log('Scene ' + sceneName + ' launched');
        };
        // 第一个参数为场景的名字，第二个可选参数为场景加载后的回调函数
        cc.director.loadScene(sceneName, onLaunched);
      });
}
```

## 监听事件

```
事件处理是在节点（cc.Node）中完成的。对于组件，可以通过访问节点 this.node 来注册和监听事件。
监听事件可以 通过 this.node.on() 函数来注册;

还可以使用 once 方法。once 监听在监听函数响应后就会关闭监听事件;

可以使用 off 方法关闭对应的监听事件。需要注意的是，off 方法的 参数必须和 on 方法的参数一一对应，才能完成关闭。

onLoad: function () {
    this.node.on('mousedown', function ( event ) {
      console.log('Hello!');
    });
  },  
```

## 发射事件

发射事件：emit 和 dispatchEvent。两者的区别在于，后者可以做事件传递

派送事件: dispatchEvent,在 Cocos Creator 的事件派送系统中，我们采用冒泡派送的方式。
         冒泡派送会将事件从事件发起节点，不断地向上传递给他的父级节点，
         直到到达根节点或者在某个节点的响应函数中做了中断处理 event.stopPropagation()。

```
onLoad: function () {
    this.node.on('say-hello', function (event) {
      console.log(event.detail.msg);
    });
  },

  start: function () {
    this.node.emit('say-hello', {
      msg: 'Hello, this is Cocos Creator',
    });
  },
  
当我们从节点 c 发送事件 “foobar”，倘若节点 a，b 均做了 “foobar” 事件的监听，则 事件会经由 c 依次传递给 b，a 节点。如：

// 节点 c 的组件脚本中
this.node.dispatchEvent( new cc.Event.EventCustom('foobar', true) );
如果我们希望在 b 节点截获事件后就不再将事件传递，我们可以通过调用 event.stopPropagation() 函数来完成。具体方法如下：

// 节点 b 的组件脚本中
this.node.on('foobar', function (event) {
  event.stopPropagation();
});
请注意，在发送用户自定义事件的时候，请不要直接创建 cc.Event 对象，因为它是一个抽象类，请创建 cc.Event.EventCustom 对象来进行派发。
  
```
## 事件对象

```

API 名	类型	意义
type	String	事件的类型（事件名）
target	cc.Node	接收到事件的原始对象
currentTarget	cc.Node	接收到事件的当前对象，事件在冒泡阶段当前对象可能与原始对象不同
getType	Funciton	获取事件的类型
stopPropagation	Function	停止冒泡阶段，事件将不会继续向父节点传递，当前节点的剩余监听器仍然会接收到事件
stopPropagationImmediate	Function	立即停止事件的传递，事件将不会传给父节点以及当前节点的剩余监听器
getCurrentTarget	Function	获取当前接收到事件的目标节点
detail	Function	自定义事件的信息（属于 cc.Event.EventCustom）
setUserData	Function	设置自定义事件的信息（属于 cc.Event.EventCustom）
getUserData	Function	获取自定义事件的信息（属于 cc.Event.EventCustom）

```

## 帮助和支持

* 除了本手册里提供的信息，您还可以随时通过下面的渠道获取信息或反馈问题给 Cocos Creator 开发团队：

[Cocos Creator 首页](http://www.cocos.com/creator/)

* QQ群：577848332（4群），548341746（3群已满），428196107（2群已满），246239860 (1群已满)

[论坛社区](http://forum.cocos.com/c/Creator)

* 演示和范例项目

  注意，所有 Github 上的演示和范例项目都会跟随版本进行更新，默认分支对应目前最新的 Cocos Creator 版本，老版本的项目会以 v0.7 这样的分支名区分，分   支名会和相同版本的 Cocos Creator 对应，下载使用的时候请注意。

  - [范例集合](https://github.com/cocos-creator/example-cases)：从基本的组件到交互输入，这个项目里包括了 case by case 的功能点用法介绍。
  
  - [Star Catcher](https://github.com/cocos-creator/tutorial-first-game)：也就是 快速上手 文档里分步讲解制作的游戏。
  
  - [腾讯合作开发的21点游戏](https://github.com/cocos-creator/tutorial-blackjack)
  
  - [UI 展示 Demo](https://github.com/cocos-creator/demo-ui)
  
  - [Duang Sheep](https://github.com/cocos-creator/tutorial-duang-sheep)：复制 FlappyBird 的简单游戏，不过主角换成了绵羊。
  - [暗黑斩 Cocos Creator 复刻版](https://github.com/cocos-creator/tutorial-dark-slash)：由 Veewo Games 独家授权原版暗黑斩资源素材，在 Cocos Creator 里复刻的演示项目
  - [i18n 游戏多语言支持范例](https://github.com/nantas/demo-i18n)：配套的文档教程是 i18n 游戏多语言支持
  - [响应式 UI Demo](https://github.com/cocos-creator/demo-responsive-ui)：展示了可适配任意屏幕尺寸的 UI 系统
  - [战斗动画 Demo](https://github.com/cocos-creator/demo-combat-animation)：使用强力灵活的动画系统制作战斗动画
  - [组队界面 Demo](https://github.com/cocos-creator/demo-team-build-ui)：展示使用 Prefab 实现数据和表现分离的动态 UI 构建

* 原生发布代码库

  打包发布 Android 平台需要的代码库：

  - [Android SDK Windows](http://cocostudio.download.appget.cn/android-sdk/android-sdk-win.zip)
  - [Android SDK Mac](http://cocostudio.download.appget.cn/Cocos/CocosStore/android22-sdk-macosx.zip)
  - [Android NDK Windows 32位](http://cocostudio.download.appget.cn/Cocos/CocosStore/android-ndk-r10d-windows-x86.zip)
  - [Android NDK Windows 64位](http://cocostudio.download.appget.cn/Cocos/CocosStore/android-ndk-r10e-Windows.zip)
  - [Android NDK Mac](http://cocostudio.download.appget.cn/Cocos/CocosStore/android-ndk-r10e-macosx.zip)

* 其他第三方工具和资源

  - 代码编辑工具

    [VS Code](https://code.visualstudio.com/) 微软推出的轻量级文本编辑器，支持 Cocos Creator 代码提示和语法高亮
  
    [WebStorm](https://www.jetbrains.com/webstorm/)
  
    [Sublime Text](http://www.sublimetext.com/)
  
    [Atom](https://atom.io/)

  - 图集生产工具

    [TexturePacker](https://www.codeandweb.com/texturepacker)
  
    [Zwoptex](https://zwopple.com/zwoptex/)
  
  - 位图字体生产工具

    [Glyph Designer](https://71squared.com/glyphdesigner)
  
    [Hiero](https://github.com/libgdx/libgdx/wiki/Hiero)
  
    [BMFont (Windows)](http://www.angelcode.com/products/bmfont/)
  
  - 2D 骨骼动画工具

    [Spine](http://esotericsoftware.com/)
  
    [Spriter](http://brashmonkey.com/spriter.htm)
  
    [DragonBones](http://www.angelcode.com/products/bmfont/)
  
  
  - 粒子特效制作工具

    [Particle Designer](http://particledesigner.71squared.com/)
  
    [Particle2dx](http://www.effecthub.com/particle2dx)：免费在线工具
  
  - 其他游戏开发资源

    [Cocos Store](http://store.cocos.com/)：各类游戏美术资源、扩展工具
