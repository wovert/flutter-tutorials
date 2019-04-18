# Flutter

## What Flutter

> Flutter allows you to build beautiful native apps on iOS and Android from a single codebase.

Flutter是谷歌的**移动UI框架**，可以快速在iOS和Android上构建高质量的**原生用户界面**。 Flutter可以**与现有的代码一起工作**。在全世界，Flutter正在被越来越多的开发者和组织使用，并且Flutter是完全免费、**开源**

- **跨平台**：现在Flutter至少可以跨4种平台，甚至支持嵌入式开发。我们常用的有Linux、Android、IOS，甚至可以在谷歌最新的操作系统上Fuchsia进行运行,经过第三方扩展，甚至可以跑在MacOS和Windows上，到目前为止，Flutter算是支持平台最多的框架了，良好的跨平台性，直接带来的好处就是**减少开发成本**。

- **原生用户界面**：它是原生的，让我们的体验更好，性能更好。用官方的话讲就是平滑而自然的滑动效果和平台感知，为您的用户带来全新的体验。

- **开源免费**

### 主流框架的对比

- **Cordova**：Cordova是基于**网页技术进行包装**，利用插件的形式开发移动应用的。无论是性能还是体验，Flutter都可以完胜。
- **RN（React Native）**：RN的效率由于是将**View编译成了原生View**,所以效率上要比基于Cordova的HTML5高很多,但是它也有效率问题,RN的**渲染机制**是基于前端框架的考虑,**复杂的UI渲染是需要依赖多个view叠加**.比如我们渲染一个复杂的ListView,每一个小的控件,都是一个native的view,然后相互组合叠加.想想此时如果我们的list再需要滑动刷新,会有多少个对象需要渲染.所以也就有了前面所说的RN的列表方案不友好。
- **Flutter**：吸收了前两者的教训之后,在**渲染技术**上,选择了自己**实现(GDI)**,由于有更好的**可控性**,使用了新的语言Dart,避免了RN的那种**通过桥接器与Javascript通讯导致效率低下的问题**,所以在性能方面比RN更高一筹;有经验的开发者可以打开Android手机**开发者选项**里面的**显示边界布局**,发现Flutter的布局是一个整体.说明Flutter的渲染没用使用原生控件进行渲染。

### 120fps超高性能

Flutter采用**GPU渲染技术**，所以性能极高。

Flutter编写的应用是可以达到120fps(每秒传输帧数)，它完全可以**胜任游戏**的制作。而我们常说的**RN**的性能只能达到**60fps**，这也算是Flutter的一个超高竞争力。官方宣称Flutter甚至会超过原生性能。如果你想迈入移动游戏领域，学习Flutter也是一个非常好的选择

### Flutter生态情况

由于有google这样的超级公司支持和推广，Flutter虽然刚出来没有多久，但是生态还是非常好的，中国也有了大量的Flutter爱好者。

目前**阿里集团**已经开始使用Flutter来进行开发了，比如我们经常使用的**闲鱼**，**主要模块就是Flutter进行开发**的

我们先来看一下Flutter的插件情况。由法国人总结了一个**Flutter的插件列表**，我们可以打开看一下，里边的插件非常丰富。所以小伙伴们完全没有必要为Flutter的生态环境而担忧。

Flutter 的官方网站为我们提供了一个[**showcase**](https://github.com/Solido/awesome-flutter)

## 环境搭建

### Windows 系统的基本要求

- **操作系统**：必须`windows7`以上 `64`位操作系统
- **磁盘空间**：`大于3个G`，虽然官方说的是400M，但是你还需要安装**Android Studio 和 虚拟机**，所以至少要3个G左右，如果能达到5个G就更好
- **Git环境**：Flutter需要git环境的支持

### JAVA环境的安装

既然要做原生应用了，而且是基于**Android**的，那还是需要我们安装一下JAVA的环境

JAVA环境下载地址：
`https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html`

### 下载安装 FlutterSDK

1. 官网下载Flutter安装包，下载地址:`https://flutter.io/sdk-archive/#windows`

2. 将安装包zip解压到你想安装Flutter SDK的路径（如：`E:\fluter\flutter`；注意，不要将flutter安装到需要一些高权限的路径如C:\Program Files\

3. 在Flutter安装目录的flutter文件下找到`flutter_console.bat`，双击运行并启动`flutter`命令行，接下来，你就可以在`Flutter`命令行运行`flutter`命令了。

4. 配置环境变量，Flutter的执行是要进行联网的，由于国内的原因，所以你需要设置环境变量

``` sh
export PUB_HOSTED_URL=https://pub.flutter-io.cn
export FLUTTER_STORAGE_BASE_URL=https://storage.flutter-io.cn
```

5. 如果你想在任何地方都可以执行`Flutter`命令，你需要把`Flutter SDK的目录`配到环境变量中的`path`条目下

### 进行 flutter docker 的测试

在终端中输入`flutter doctor`，你可能会得到下面类似的结果

``` sh
# flutter doctor
Android toolchain - develop for Android devices
    • Android SDK at D:\Android\sdk
    ✗ Android SDK is missing command line tools; download from https://goo.gl/XxQghQ
    • Try re-installing or updating your Android SDK,
      visit https://flutter.io/setup/#android-setup for detailed instructions.
```

### 下载 Android Studio 和 Android SDK

Android Studio下载地址：http://www.android-studio.org/

下载Android SDK的时候，记得搭上梯子，否则你会等到天荒地老

如果你有安装，那么第一步要作的是允许协议（android-licenses）。允许方法就是在终端运行如下命令：`flutter doctor --android-licenses`



### 一条命令快速开启虚拟机

> 制作一个批处理文件，来直接开启AVD虚拟机

开启虚拟机需要两个步骤：

1. 打开`emulator.exe`这个程序，你可以巧妙利用windows的查找工具进行查找。
2. 打开你设置的虚拟机，批处理时需要填写你设置的虚拟机名称。

具体步骤如下：

1. 新建一个xxx.bat文件到桌面，xxx的意思是，你可以自己取名字，随意叫什么都可以。我这里叫EmulatorRun.bat.
2. 查找emulator.exe文件的路径，把查找到的路径放到bat文件中（如图）。 你一般会查找到两个emulator.exe文件，一个是在tools目录下，一个是在emulator目录下，我们选择emulator目录下的这个,复制它的路径。
`C:\Users\Administrator\AppData\Local\Android\Sdk\emulator\emulator.exe`
(特别说明，你的和我的很有可能不一样，你要复制i电脑中的路径，不要复制这里的代码)

3. 打开Android Studio，并查看你的AVD虚拟机名称（如图所示）。 如果你觉的输入不方便和怕出错，你可以点击图片后边的笔型按钮，进入编辑模式，复制这个名称。

4. 然后根据你复制的名称，把bat文件输入成如下形式。

`C:\Users\Administrator\AppData\Local\Android\Sdk\emulator\emulator.exe -netdelay none -netspeed full -avd Nexus_5X_API_28`

进行保存后双击bat文件，就可以迅速打开虚拟机了。

- 参数解释：
  - `-netdelay none` :设置模拟器的网络延迟时间，默认为none，就是没有延迟。
  - `-netspeed full`: 设置网络加速值，full代表全速。

### flutter run 开启预览

现在模拟器也有了，VSCode也支持Flutter开发了。现在可以在VSCode中直接打开终端，快捷键是`ctrl+~`，然后在终端中输入下面的命令。

`flutter run`

经过短暂的编译后就会启动我们的程序了

到此处，终于搭建出了适合前端程序员的开发环境

#