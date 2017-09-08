# COCOS
COCOS DEMO


------->[点击体验StarScoreGame](https://fairyly.github.io/COCOS/start_project/build/web-mobile/index.html)


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
