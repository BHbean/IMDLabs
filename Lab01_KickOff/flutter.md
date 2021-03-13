# Introduction of Flutter

### 1 Flutter 简介

- Flutter 是 Google 开源的 UI 工具包，帮助开发者通过一套代码库高效构建**多平台精美**应用，支持移动、Web、桌面和嵌入式平台。
- Flutter 可以**快速**在 iOS 和 Android 上构建高质量的原生用户界面，并且完全可以与现有的代码一起工作。
- 在全世界，Flutter 正在被越来越多的开发者和组织使用，其是完全**免费、开源**的。



### 2 Flutter 主要特点

#### 2.1 快速开发

- Flutter 的**热重载(hot reload)**可以快速地进行测试、构建UI、添加功能并更快地修复错误。在 iOS 和 Android 模拟器或真机上可以在保存原始状态的情形下迅速重载。

  ![avatar](https://flutterchina.club/images/intellij/hot-reload.gif)

#### 2.2 精美的 UI

- Flutter 内置精美的 *Material Design* 和 *Cupertino（iOS风格）widget*、丰富的 *motion API*、平滑而自然的滑动效果和平台感知，能为用户带来优良的用户体验。

  <img src="https://flutterchina.club/images/homepage/screenshot-1.png" alt="avatar" style="zoom:40%;" /><img src="https://flutterchina.club/images/homepage/screenshot-2.png" alt="avatar" style="zoom:40%;" /><img src="https://flutterchina.club/images/homepage/screenshot-3.png" alt="avatar" style="zoom:40%;" /><img src="https://flutterchina.club/images/homepage/ios-friendlychat.png" alt="avatar" style="zoom:40%;" />

  

#### 2.3 现代的，响应式框架

- *Flutter* 的现代、响应式框架和一系列基础 *widget*，能轻松构建用户界面。其功能强大且灵活的 *API*（针对 *2D*、动画、手势、效果等）解决艰难的 *UI* 挑战。

  ```java
  class CounterState extends State<Counter> {
    int counter = 0;
  
    void increment() {
      // 告诉Flutter state已经改变, Flutter会调用build()，更新显示
      setState(() {
        counter++;
      });
    }
  
    Widget build(BuildContext context) {
      // 当 setState 被调用时，这个方法都会重新执行.
      // Flutter 对此方法做了优化，使重新执行变的很快
      // 所以你可以重新构建任何需要更新的东西，而无需分别去修改各个widget
      return new Row(
        children: <Widget>[
          new RaisedButton(
            onPressed: increment,
            child: new Text('Increment'),
          ),
          new Text('Count: $counter'),
        ],
      );
    }
  }
  ```



#### 2.4 访问本地功能和 SDK

- 通过平台相关的 *API*、第三方 *SDK* 和原生代码让您的应用变得强大易用。 *Flutter* 允许程序员复用现有的 *Java* 、*Swift* 或 *ObjC* 代码，访问 *iOS* 和 *Android* 上的原生系统功能和系统 *SDK*。
- 访问平台功能非常简单。以下是 [interop example（互操作示例）](https://github.com/flutter/flutter/tree/master/examples/platform_channel)中的一个片段：

```dart
Future<Null> getBatteryLevel() async {
  var batteryLevel = 'unknown';
  try {
    int result = await methodChannel.invokeMethod('getBatteryLevel');
    batteryLevel = 'Battery level: $result%';
  } on PlatformException {
    batteryLevel = 'Failed to get battery level.';
  }
  setState(() {
    _batteryLevel = batteryLevel;
  });
}
```



#### 2.5 统一的应用开发体验

- *Flutter* 拥有丰富的工具和库，可以轻松地同时在 *iOS* 和 *Android* 系统中实现想法和创意。 对于没有任何移动端开发体验的开发人员而言，*Flutter* 是一种轻松快捷的方式来构建漂亮的移动应用程序。 对于经验丰富的 *iOS* 或 *Android* 开发人员而言，则可以使用 *Flutter* 作为视图( *View* )层， 并可以使用已经用 *Java / ObjC / Swift* 完成的部分（*Flutter* 支持混合开发）。

| 构建                                                         | 优化                                                         | 部署                                                         |
| :----------------------------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| *漂亮的用户界面：*<br>    丰富的 *2D* *GPU* 加速 *API*<br>    响应式框架<br>    动画 / 运动 *API*<br>    *Material* 组件和 *Cupertino widgets* | *测试：*<br>    单元测试<br>    集成测试<br>    设备上测试   | *编译：*<br>    *Native ARM* 代码<br>    *Dead code elimination* |
| *流畅的编码体验：*<br>    亚秒级、有状态的热重载<br>    *IntelliJ* : 代码重构、补全等<br>    *Dart* 语言和核心库<br>    包管理器 | *调试：*<br>    *IDE* 调试器<br>    基于 *Web* 的调试器<br>    *async / await aware*<br>    *Expression evaluator* | *发布：*<br>    *App Store*<br>    *Play Store*              |
| *全功能的应用程序：*<br>    与移动操作系统 *API* 和 *SDK* 交互<br>    *Maven / Java*<br>    *Cocoapods / ObjC / Swift* | *性能分析：*<br>    时间线（*Timeline*）<br>    *CPU* 和内存<br>    应用内性能图标 |                                                              |



