# 运行环境要求
- Mac + Safari 浏览器
- iPhone（iOS 6 +） + Safari 浏览器
# 调试步骤
1. 使用数据线将 iPhone 与 Mac 相连
2. iPhone 开启 Web 检查器（设置 -> Safari -> 高级 -> 开启 Web 检查器)
![](http://upload-images.jianshu.io/upload_images/5018455-b538b959e592a92e.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
3. iPhone 使用 Safari 浏览器打开要调试的页面
![](http://upload-images.jianshu.io/upload_images/5018455-33420ae3b9781cc4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
4. Mac 打开 Safari 浏览器调试（菜单栏-> 开发-> iPhone 设备名-> 选择调试页面）
![](http://upload-images.jianshu.io/upload_images/5018455-f9ca7fdbcbf2f3a1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
如果你的菜单栏没有“开发”选项，可以到左上角 Safari-> 偏好设置-> 高级-> 在菜单栏中显示“开发”菜单
![](http://upload-images.jianshu.io/upload_images/5018455-304e76b4b024fa9d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
5. 在弹出的 Safari Developer Tools 中调试
![](http://upload-images.jianshu.io/upload_images/5018455-1d0a07587182fabf.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

经过如上步骤就可在 Mac 端调试 iPhone 上 Safari 运行的页面了，但对于 WebView 页面就不适用了，另外 Windows 系统不适用此方案。

# Xcode模拟器调试
没有 iPhone 设备可以在 App Store 安装 Xcode 使用其内置的 iOS 模拟器，安装完成后通过以下两种方式开启：
- 右键 Xcode 图标-> Open Developer Tool-> Simulator
- 右键 Finder 图标-> 前往文件夹-> /应用程序/Xcode.app/Contents/Developer/Applications/-> 运行 Simulator.app

运行 iOS 模拟器后，在模拟器中打开调试页面，再通过 Mac Safari 开发功能就可以调试到。
![](http://upload-images.jianshu.io/upload_images/5018455-41d1ff289fc45916.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
如果我需要调试更低版本的 iOS 怎么办？实际使用的 iPhone 不可能去降版本，不必担心，Simulator 有。
点击左上角 Xcode -> Preferences-> Downloads就可以看到提供了如下版本：
![](http://upload-images.jianshu.io/upload_images/5018455-ec458c6572b94124.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)