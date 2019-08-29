# Flutter

## Flutter History

- 2014.10 Open the Sky
- 2015.10 Rename Flutter
- 2017.5 Google I/O
- 2018.6 1.0 发布
- 2019.2 1.2 发布（支持Web）

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

- 选择OS：
  - Windows: 无法开发iOS
  - Mac: 开发iOS/Android
- 开发工具：Android Studio VS Visual Studio Code
  - Visual Studio Code
    - 前端开发利器
    - 无法调试Android
  - Android
    - Android 开发工具
    - 可以调试

### Mac 下搭建Flutter开发环境

#### 1.系统要求

- OS: macOS 64-bit
- Disk: 700MB(不包括Xcode或Android Studio的硬盘空间)
- Tool: Flutter 依赖这些命令行工具：bash/curl/git-2.x/mkdir/rm/unzip/which

#### 2.设置 Flutter 镜像（非必须）

- 由于国内访问Flutter可能会受到限制，Flutter 官方为中国开发者搭建了临时镜像。环境变量加入到用户环境变量中

Macintosh HD -> Users -> 用户名 -> .bash_profile
```sh
$ cd ~
#$ git clone -b dev https://github.com/flutter/flutter.git
$ vim ~/.bash_profile
#Flutter镜像
export PUB_HOSTED_URL=https://pub.flutter-io.cn
export FLUTTER_STORAGE_BASE_URL=https://storage.flutter-io.cn
# export PATH="$PWD/flutter/bin:$PATH"
#$ cd ./flutter
#$ flutter doctor
```

**注意**：此镜像为临时镜像，并不能保证一直可用，可以从 [Using Flutter in China](https://flutter.dev/community/china) 上获得有关镜像服务器的最新动态

#### 3.获取Flutter SDK

[下载Fluter SDK安装包]

```sh
$ cd ~ 
$ curl -O https://storage.googleapis.com/flutter_infra/releases/stable/macos/flutter_macos_v1.2.1-stable.zip
$ unzip flutter_macos_v1.2.1-stable.zip
$ vim ~/.bash_profile
#Flutter环境变量
export PATH="$PATH:$PWD/flutter/bin"
$ source ~/.bash_profile

运行 flutter doctor
$ flutter doctor
$ flutter doctor --android-licenses

配置android环境变量
$ vim ~/.bash_profile
#android 环境变量
export ANDROID_HOME=$PWD/Library/Android/sdk
#Android 模拟器路径
export PATH=${PATH}:${ANDROID_HOME}/emulator
#Android tools 路径
export PATH=${PATH}:${ANDROID_HOME}/tools
#Android 平台工具路径
export PATH=${PATH}:${ANDROID_HOME}/platform-tools
#Android NDK路径
ANDROID_NDK_HOME=$PWD/Library/Android/ndk/android-ndk-r10e

$ flutter
```
> 第一次运行一个 `flutter` 命令(`flutter doctor`)时，它会下载依赖项并自行编译。以后再运行就会快得多。

#### 4.iOS 开发环境设置

> 要用 Flutter 开发 iOS App 需要 Xcode 9.0或更高版本

1. 安装 Xcode 9.0 或更新版本（苹果应用商店）
2. 配置Xcode命令行工具以使用新安装的Xcode版本

`sudo xcode-select --switch /Applications/Xcode.app/Contents/Developer`

以上路径时对于最新版Xcode的路径。如果需要使用不同的Xcode版本，需要指定相应路径

3. 确保Xcode许可协议是通过打开一次Xcode或通过命令`sudo xcodebuild -license`同意过了

接下来可以使用Xcode，再iOS设备或模拟器上运行Flutter App

#### 5.Android 开发环境设置

再iOS模拟器上运行并测试Flutter应用

1. 打开一个 iOS 模拟器 `$ open -a Simulator`
2. 通过模拟器菜单的 硬件>设备，确保打开的是64位 iPhone 5s或者更新的模拟器
3. 通过模拟器的 Windows>Scale 菜单下设置设备比例

#### 6. Android 创建插件

- Configure -> Dart/Flutter

#### 7. 创建和运行一个flutter项目

1. 通过命令行创建一个 Flutter 项目
`$ flutter create my_app`

2. 命令运行完成之后会再当前目录下创建一个名为`my_app`的flutter项目，然后通过一个命令可以运行它：

```sh
$ cd my_app
$ flutter run
```

#### 8. Flutter 安装到 iOS真机上

`flutter run` 将 Flutter 应用安装到iOS真机设备，需要一些额外的工具和一个Apple账户，还需要再Xcode中进行设置

> 用Xcode来将 Flutter 运行在真机上更简单，点一下`run` 按钮即可

1. 安装 [Homebrew](https://brew.sh)
2. 更新 homebrew `$ brew update`
3. 打开终端并运行这些命令用来将flutter应用安装到iOS设备的工具
```bash
$ brew install --HEAD usbmuxd
$ brew unlink usbmuxd && brew link usbmuxd
$ brew install --HEAD libimobiledevice
$ brew install ideviceinstaller ios-deploy cocoapods
$ pod setup
```
**注意**这些命令当中人物一个失败并出现错误，可运行`brew doctor`并按照说明解决问题
4. 遵循Xcode签名流程来配置项目

- 将Flutter项目目录中通过 `$ open ios/Runner.xcworkspace` 打开默认的Xcode workspace
- 在Xcode中，选择导航面板左侧中的Runner项目
- 在**Runner target** 设置页面中，确保在 **General>Signing>Team** 下选择**开发团队**。选择一个团队时，Xcode会**创建并下载开发证书**，设备注册账户，并创建和下载配置文件
  - 第一个iOS开发项目，需要使用**Apple ID登录Xcode**
- 第一次attach真机设备进行iOS开发时，需要同时信任你的Mac和该设备上的开发证书。首次将iOS设备连接到Mac时，请在对话框中选择 Trust。然后，转到iOS设备上的设置应用程序，**选择常规>设备管理** 并信任您的证书
- 如果Xcode中的自动签名失败，清验证项目的 **General > Identity > Bundle Identifier** 值是否唯一

5. 通过`flutter run`运行启动项目

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

### 用flutter 命令建立项目

```sh
# flutter create hello_world_app
```

### VSCode 配置并建立项目

- 打开命令面板(快捷键：`Ctrl + Shift + P`
- 安装扩展，搜索 flutter点击安装，发现 Dart 也一起安装好了
- 打开命令面板输入 `doctor`，选择 `Flutter: Run Flutter Doctor`
- 查看 “OUTPUT” 窗口中的输出是否有问题
- 创建项目
  - 打开命令面板
  - 选择 `Flutter: New Project`
  - 项目命名，遵循谷歌下划线命名，使用驼峰命名会报错

### 配置移动设备

1. 将自己的手机连接到电脑，打开**开发者模式**（连续点击版本号
2. 进入开发者选项，打开 **USB 调试**（不同手机'开发者选项'在不同位置）
3. 检查是否连接成功
4. 按 F5 键或点击 **调试>启动调试**(Debug>Start Debugging)，等待手机出现画面 
5. 体验热重载: 打开`main.dart` 文件 找到 `home: new MyHomePage(title: 'Flutter Demo Home Page')`,把 `title`里的内容改为`VSCode Flutter Demo`保存， 就可以在手机上看到更改了

### flutter run 开启预览

`flutter run`

``` sh
$ flutter config --android-sdk E:\adt-bundle-windows-x86_64-20140702\sdk
$ flutter config --android-studio-dir C:\Android\Android Studio
```

## 常用项目

- 导航框架：Scaffold + PageView
- http库：http
- 页面路由：Navigator
- 监听列表怒动：NotificationListener
- 定制化需求：自定义组件
- native代码封装/naitive SDK的调用：Native Modules
- native SDK：AI语音
- native 与 fluter 通信：Channel通信
- flutter与H5/Flutter与iOS/Flutter与Android混合开发
- flutter gridview（瀑布流布局）: 插件
- flutter 官方组件

