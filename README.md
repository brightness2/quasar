# Quasar demo
Quasar demo

# 环境要求
Node > 14
npm >  6.13.4

# 环境部署
```
npm i -g @quasar/cli

npm init quasar
```

# APP开发
https://quasar-cn.vercel.app/quasar-cli-vite/developing-capacitor-apps/preparation#introduction

## 工具安装
1、安装JDK,并配置环境变量
```
JAVA_HOME
<jdk-path>

CLASSPATH
.;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar

path环境变量中添加
%JAVA_HOME%\bin
和
%JAVA_HOME%\jre\bin

```
2、安装Gradle，并添加path环境变量
```
 D:\<gradle-path>\bin
```
3、安装 Android Studio 
```
 ANDROID_HOME "<Android-sdk-path>"

 ANDROID_SDK_ROOT "<Android-sdk-path>"

 path添加 ";%ANDROID_SDK_ROOT%\tools;%ANDROID_SDK_ROOT%\platform-tools;<gradle_path>\bin;"
```

## Capacitor模式
1、添加Capacitor模式
```
 quasar mode add capacitor
  npx cap add android
  //npx cap add ios
  //npx cap add electron

  quasar dev -m capacitor -T [android|ios]
```

Android Studio出现Caused by: org.gradle.api.internal.plugins.PluginApplicationException: Failed to app

在项目中的F:\我的资料\Quasar\demo\src-capacitor\android\gradle.properties文件中添加语句：

```
android.overridePathCheck=true
```

2、最好使用模拟器进行调试
比如夜神模拟器
如果Android studio 找不到夜神模拟器，可以运行一下命令，连接模拟器
```
cd <your_path>\Nox\bin

nox_adb.exe connect 127.0.0.1:62001
```


3、打包
```
quasar build -m capacitor -T [ios|android]
```
4、签名App
```
//java 工具命令
keytool -genkey -v -keystore my-release-key.keystore -alias alias_name -keyalg RSA -keysize 2048 -validity 20000

jarsigner -verbose -sigalg SHA1withRSA -digestalg SHA1 -keystore my-release-key.keystore <path-to-unsigned-apk-file> alias_name

```
5、优化 APK
```
/path/to/Android/sdk/build-tools/VERSION/zipalign

zipalign -v 4 <path-to-same-apk-file> HelloWorld.apk
```
##  Cordova 模式
1、安装Gradle
https://downloads.gradle-dn.com/distributions/gradle-4.10.3-all.zip

解压后把 bin 目录的路径添加到 path 中
```
<gradle_path>\bin
```
2、安装 cordova cli
```
 npm install -g cordova

```
3、添加 cordova 模式
```
quasar mode add cordova
```

4、添加平台
```
 cd .\src-capacitor\

cordova platform add [android|ios]

cordova requirements

```


