# QuranAPP.apk
QuranAPP powered by quranenc.com. 方便中国穆斯林。

Becuase the quranenc.com app is only availible in the Google Play.

Hoever Google Play is banned, and all this kind of Apps are banned too.

## With the method below, you can package many websites to Adroid .apk.

# Method
在 Linux 系统上使用以下命令安装 Android Studio 并完成相关配置的步骤：

## 1. 安装依赖
在安装 Android Studio 之前，需要安装一些必要的依赖包。以基于 Red Hat 的系统（如 Rocky Linux）为例，使用以下命令安装：

`sudo dnf install -y java-11-openjdk-devel unzip wget`

对于基于 Debian 的系统（如 Ubuntu），可以使用以下命令：

`sudo apt-get install -y openjdk-11-jdk unzip wget`

## 2. 下载 Android Studio
使用 wget 命令从官方网站下载 Android Studio 的压缩包：

`wget https://redirector.gvt1.com/edgedl/android/studio/ide-zips/2024.3.1.13/android-studio-2024.3.1.13-linux.tar.gz`

请根据实际情况选择最新版本的下载链接。

## 3. 解压并安装 Android Studio
将下载的压缩包解压到指定目录，例如 /opt：

`sudo tar -xvf android-studio-2024.3.1.13-linux.tar.gz -C /opt`

## 4. 配置环境变量
打开你的 shell 配置文件（如 .bashrc、.bash_profile 或 .zshrc），添加以下内容：
```
export ANDROID_HOME=$HOME/Android/Sdk
export PATH=$PATH:$ANDROID_HOME/emulator
export PATH=$PATH:$ANDROID_HOME/tools
export PATH=$PATH:$ANDROID_HOME/tools/bin
export PATH=$PATH:$ANDROID_HOME/platform-tools
export PATH=$PATH:$ANDROID_HOME/cmdline-tools/latest/bin
export PATH=$PATH:/opt/android-studio/bin
```

使配置文件生效：

`source ~/.bashrc`

## 5. 启动 Android Studio 并完成初始设置
首次启动 Android Studio 时，需要完成一些初始设置，包括安装 SDK 组件等。使用以下命令启动：

`/opt/android-studio/bin/studio.sh`

在启动过程中，按照提示完成 SDK 组件的安装。可以选择安装所需的 Android 版本和开发工具。

## 6. 验证安装
安装完成后，可以通过以下命令验证 Android SDK 和相关工具是否正常工作：

`adb --version`

如果能正常显示 ADB 的版本信息，则说明安装和配置成功。

## 7. 安装 Cordova
首先，确保你已经安装了 Node.js 和 npm。然后，使用 npm 全局安装 Cordova：

`npm install -g cordova`

## 8. 创建一个新的 Cordova 项目
在当前目录下创建一个新的 Cordova 项目：
```
cordova create quranApp com.example.quranApp QuranApp
cd quranApp
```

## 9. 添加平台支持
添加你想要支持的移动平台，例如 Android 和 iOS：
```
cordova platform add android
cordova platform add ios
```

## 10. 配置 config.xml 文件
打开 config.xml 文件，将 content 标签的 src 属性设置为目标网页的 URL：

`<content src="https://quranenc.com/zh/browse/chinese_makin" />`

## 11. 允许访问外部网站
在 config.xml 文件中添加以下 allow-navigation 和 allow-intent 标签，以允许应用访问外部网站：
```
<allow-navigation href="https://quranenc.com/*" />
<allow-intent href="https://quranenc.com/*" />
```

## 12. 构建和运行应用
构建并运行应用到你的设备或模拟器上：
```
cordova clean android
cordova build android
cordova run android
```

## 注意事项
- 权限问题：确保应用具有访问网络的权限。
- 安全问题：由于应用直接访问外部网站，需要注意安全问题，如防止跨站脚本攻击（XSS）。
- 兼容性问题：不同的移动设备和浏览器可能对网页的显示效果有所不同，需要进行充分的测试。
- 依赖问题：如不同版本的 JDK，Gradle Wrapper 等的调试安装。

通过以上步骤，你可以将指定的网页打包成一个移动应用程序，并通过 Android Studio 并中的安卓手机模拟起来测试。
