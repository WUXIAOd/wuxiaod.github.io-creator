---
title: "Flutter 初识"
date: 2019-12-08T10:36:04+08:00
draft: false
---

## Flutter


官网介绍：

[Flutter中文网](https://book.flutterchina.club/chapter1/flutter_intro.html)

Flutter是谷歌的移动UI框架，可以快速在iOS和Android上构建高质量的原生用户界面。 Flutter可以与现有的代码一起工作。在全世界，Flutter正在被越来越多的开发者和组织使用，并且Flutter是完全免费、开源的。

总结：

* 跨平台：现在Flutter至少可以跨4种平台，甚至支持嵌入式开发。我们常用的有Linux、Android、IOS，甚至可以在谷歌最新的操作系统上Fuchsia进行运行,经过第三方扩展，甚至可以跑在MacOS和Windows上，到目前为止，Flutter算是支持平台最多的框架了，良好的跨平台性，直接带来的好处就是减少开发成本。

* 原生用户界面： 它是原生的，让我们的体验更好，性能更好。用官方的话讲就是平滑而自然的滑动效果和平台感知，为您的用户带来全新的体验。（可以看一下图片，这是Flutter的表现）

* 开源免费

[github地址](https://github.com/Solido/awesome-flutter)

`代表项目： 闲鱼app`

### 安装

##### 安装JAVA环境

选择适合自己机型的版本（64位 or 32位）

[JAVA下载地址](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)

安装完成到终端（命令行）里输入java运行，如果出现一大堆命令，则表示安装成功。

#### 下载安装 FlutterSDK

* 去官网下载Flutter安装包，[下载地址](https://flutter.io/sdk-archive/#windows)

* 将安装包zip解压到你想安装Flutter SDK的路径（如： D:\fluter\flutter；注意，不要将flutter安装到需要一些高权限的路径如C:\Program Files\)

* 在Flutter安装目录的flutter文件下找到`flutter_console.bat`，双击运行并启动flutter命令行，接下来，你就可以在Flutter命令行运行flutter命令了。

* 配置环境变量，在 高级系统设置中找到系统变量中的 Path 点击编辑添加: `D:\Flutter\flutter\bin`保存。这样就可以在任何地方执行 flutter 命令了。

* 在终端中输入`flutter doctor`,会薄一些错，是因为还要安装 `Android studio`

#### Android Studio的安装

* [下载地址](
https://developer.android.com/)进入后下拉寻找下载按钮带=点击下载。

* 安装Android Studio 软件，几乎就是点next就行了。也可以看此教程：
[
Android Studio 软件安装教程](https://www.cnblogs.com/xiadewang/p/7820377.html)

* 打开Android Stuido 软件，然后找到Plugin的配置，搜索Flutter插件，点击 install 安装，安装完后重启 Android Stuido。

#### 安装Android证书

命令行输入：

`flutter doctor --android-licenses`
一路选择 y/Y 直到完成 。

**到此，基础环境已经安装完成了，接下来就是安装AVD虚拟机了，当然也可以用真机来进行预览，这样效果会更好。**
 
1. Android studio新建Flutter项目

* 打开Andorid Studio，选择新建Flutter项目,打开第二个窗口后，选择第一个选项Flutter Application(flutter应用)。这步完成后，系统就会自动为我们创建一个Flutter项目。

2. 安装虚拟机

* 点击Android Studio中的上方菜单tool 选择AVD Manager选项。
* 出现新建菜单，选择Create Virtual Device

* 选择虚拟机类型（Nexus 5x），随你选择。

* 选择系统，这里尽量选择最新的。

* 安装好后，点击开始按钮，运行虚拟机。

* 虚拟机运行以后，可以点击debug按钮，让Flutter程序跑起来。

至此，Flutter 的开发环境差不多全部搭建完成，接下来就来写一个 hello world 吧

-------

建议使用  VScode 编辑器来写代码和测试，虚拟机可以使用一个脚本文件来自动打开。

具体步骤如下：

1. 新建一个xxx.bat文件到桌面。xxx随你换。
2. 查找emulator.exe文件的路径，把查找到的路径放到bat文件中，注意，此处需要的是emulator 目录下的 emulator.exe 文件，复制这个路径。
3. 打开Android Studio，并查看 AVD虚拟机名称 （ 我的是：Nexus 5X API 29），复制。然后把前面复制的路径和虚拟机名字粘贴到xxx.bat 文件中，形如：`C:\Users\12913\AppData\Local\Android\Sdk\emulator\emulator.exe -netdelay none -netspeed full -avd Nexus_5X_API_29` 。中间的参数无需改动。

*参数解释：
🎈 -netdelay none :设置模拟器的网络延迟时间，默认为none，就是没有延迟。
🎈 -netspeed full: 设置网络加速值，full代表全速。*

4. flutter run 开启预览，把你的flutter项目在 vscode 中打开，安装flutter 插件，安装完后，在终端输入：`flutter run `启动程序。

#### 写一个 hello world 

找到项目根目录下的\bin\main.dart文件，将其默认的代码删掉，然后添加如下代码：

```
import 'package:flutter/material.dart';
//主函数（入口函数）
void main() =>runApp(MyApp());
// 声明MyApp类class MyApp extends StatelessWidget{
  //重写build方法
  @override
  Widget build(BuildContext context){
    //返回一个Material风格的组件
   return MaterialApp(
      title:'Welcome to Flutteraa',
      home:Scaffold(
        //创建一个Bar，并添加文本
        appBar:AppBar(
          title:Text('Welcome to Flutter'),
        ),
        //在主体的中间区域，添加一个hello world 的文本
        body:Center(
          child:Text('Hello World'),
        ),
      ),
    );
  }
}
```

写完后打开终端，运行`flutter run`,等待一小会，就会看到虚拟机中显示了Hello World的内容。

#### VSCode中的一些常用功能键

* r 键：点击后热加载，也就算是重新加载吧。
* p 键：显示网格，这个可以很好的掌握布局情况，工作中很有用。
* o 键：切换android和ios的预览模式。
* q 键：退出调试预览模式。

✨鼠标必须 focus 在终端的运行界面
