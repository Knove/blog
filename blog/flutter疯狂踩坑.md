 # <img src="https://flutter.io/images/flutter-mark-square-100.png" alt="Flutter" width="40" height="40" /> Flutter 疯狂踩坑
https://flutter.io
谷歌新的Flutter，一行代码，搞定IOS,安卓，看着感觉是颠覆性的！只是坑太多啦。
1.0版本，一个脚印一步坑

## flutter doctor
当你跟着官网一步走到flutter doctor 时候，可能遇到了Android license status unknown.这个错误
```bash
[!] Android toolchain - develop for Android devices (Android SDK 27.0.3)
    ✗ Android license status unknown.
```
解决方式就是添加 Android license
```bash
flutter doctor --android-licenses
```
执行这个通常会报错：
```bash
A newer version of the Android SDK is required. To update, run:
/Users/***/Android/sdk/tools/bin/sdkmanager --update
```
此时执行 给你提示的这个来进行update 的指令后，如果你的jdk是1.8以上，那么也会报错，如果这样，推荐再安装个jdk.18

成功之后，再执行 flutter doctor --android-licenses，然后按很多y，就可以了
## 代理
建好工程后，不管是VsCode 还是 Android Studio, 都需要挂载代理才能访问要下载的一些jar包


VsCode的话，直接android\build.gradle 中
```javascript
buildscript {
    repositories {
        google()
        maven{ url 'http://maven.aliyun.com/nexus/content/groups/public/'}
        jcenter()
    }

    dependencies {
        classpath 'com.android.tools.build:gradle:3.2.1'
    }
}

allprojects {
    repositories {
        google()
        maven{ url'http://maven.aliyun.com/nexus/content/groups/public/'}
        jcenter()
    }
}
```
否则会构建不成功

## 启动
什么都弄好了，但是在VsCode有时候F5启动时候，会有找不到设备，此问题无解，网上也无果。
果断把版本升级到master，解决了
看来是flutter1.0的BUG：
```bash
flutter channel master
```
这一行指令可以让你的flutter直接是github上master的代码，果然好用很多，BUG也少了。

## 写在最后
Flutter 网上文档较少

https://docs.flutter.io/ 

啃官方文档是必须的！ 什么API都有
