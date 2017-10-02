
# Charles

## 1. HTTP抓包

- 查看电脑IP地址

![](http://upload-images.jianshu.io/upload_images/5018455-4b02e13c530325b7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 设置手机HTTP代理（电脑和手机保持同一网段）

服务器为电脑IP、端口8888（设置里可改，这里是默认）

![](http://upload-images.jianshu.io/upload_images/5018455-13410d27634ce782.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 电脑上打开Charles进行HTTP抓包

手机上打开一个任意页面，这时候会弹出如下提示，点击允许


![](http://upload-images.jianshu.io/upload_images/5018455-995deaca17f5b96f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

比如我打开了m.ctrip.com,效果如下：

![](http://upload-images.jianshu.io/upload_images/5018455-88cee2ac7472749c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 2. HTTPS抓包

默认情况下，Charles 无法抓取到 HTTPS 的请求，所以我们需要在HTTP抓包基础上再进行设置，解决步骤如下：

- Mac 端安装证书

菜单 -> Help -> SSL Proxying -> Install Charles Root Certificate


![](http://upload-images.jianshu.io/upload_images/5018455-9db5059c731f99fa.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 安装证书

在电脑上导出 Charles SSL 证书，菜单 -> Help -> SSL Proxying -> Save Charles Root Certificate

![](http://upload-images.jianshu.io/upload_images/5018455-504b39f2ee9daa24.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

Android 设备将导出的 Charles SSL 证书存储到手机中并安装。

![](http://upload-images.jianshu.io/upload_images/5018455-109c9a088a3dfbb3.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

iOS 设备用 Safari 打开 [http://www.charlesproxy.com/getssl/](http://www.charlesproxy.com/getssl/) 页面，下载 Charles SSL 证书并安装。

![](http://upload-images.jianshu.io/upload_images/5018455-99687de75e69dcae.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

证书安装完成后，还需要给 Charles SSL 代理配置域名和端口号，菜单 -> Proxy -> SSL Proxying Settings，勾选 Enable SSL Proxying，点击 Add，填入域名和端口号，经过以上步骤就可以抓取到 HTTPS 的请求了。

![](http://upload-images.jianshu.io/upload_images/5018455-cfe33c4abc5ed1b1.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

大功告成

![](http://upload-images.jianshu.io/upload_images/5018455-a4a23a5b9f8b4ada.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 3. 网络映射修改文件

除了结合前面的方案调试，可以使用 Map Local 网络映射功能来实现对文件的修改，在菜单 -> Proxy -> Start Recording，开启抓包后访问页面，找到抓取到的样式文件，点击右键 Map Local，在 Local path 中设置本地映射文件的路径，修改后刷新页面可以看到效果。

![](http://upload-images.jianshu.io/upload_images/5018455-83e24281b57af1eb.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 4. 模拟网络速度


菜单 -> Proxy -> Throttle Settings -> 勾选 Enable Throttling，在 Throttling preset 中可以选择需要模拟的网络速度。

![](http://upload-images.jianshu.io/upload_images/5018455-4f70671111ed064e.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 5. 断点调试请求和响应内容

开启 Charles 断点 Proxy -> Breakpoints Settings -> Enable Breakpoints，点击 Add 可设置断点条件或者单独对需要的文件右键 Breakpoints 设置断点。

![](http://upload-images.jianshu.io/upload_images/5018455-1b604a83f2c95b57.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

访问页面后，即可编辑请求和响应的内容，点击 Execute 按钮完成。

![](http://upload-images.jianshu.io/upload_images/5018455-1d55b869505edd10.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

# Fiddle

## 1. HTTP抓包

- Fiddler设置

启动Fiddler，打开菜单栏中的 Tools -> Options。

![](http://upload-images.jianshu.io/upload_images/5018455-8429dc95746bd8fd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

切换到“Connections”选项卡，然后勾选“Allow romote computers to connect”后面的复选框。


![](http://upload-images.jianshu.io/upload_images/5018455-027ff0ef6232463f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

这里提示要重启Fiddler才生效，点击确定，然后点击OK，接着重启。

- 设置手机HTTP代理

步骤同Charles

- 电脑上打开Fiddler进行HTTP抓包

手机上打开一个页面，比如我还是打开m.ctrip.com,效果如下：

![](http://upload-images.jianshu.io/upload_images/5018455-4f7258be78eb1532.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 2. HTTPS抓包

- Fiddler设置

打开菜单栏中的 Tools -> Options -> HTTPS,选中 Capture HTTPS CONNECTs,接下来会提示你信任并安装证书：

![](http://upload-images.jianshu.io/upload_images/5018455-9bb05634d5d1f2d0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](http://upload-images.jianshu.io/upload_images/5018455-9bc1cb834c73da53.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

安装完证书，还可以配置一些子选项，默认就行，我这里选了Ignore server certificate errors，这样兼容性应该好点：

![](http://upload-images.jianshu.io/upload_images/5018455-45f00af2242085c2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


- 安装证书

打开手机浏览器，在浏览器地址输入代理服务器IP和端口，会看到一个Fiddler提供的页面：

![](http://upload-images.jianshu.io/upload_images/5018455-31690aff5f8ef46d.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

点击最下面的download FiddlerRoot certificate

![](http://upload-images.jianshu.io/upload_images/5018455-ec98da238672c886.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

允许后开始安装

![](http://upload-images.jianshu.io/upload_images/5018455-18429342c7464c86.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](http://upload-images.jianshu.io/upload_images/5018455-9ab2b145963310b6.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](http://upload-images.jianshu.io/upload_images/5018455-7eb4a943f95cf915.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 电脑上打开Fiddler进行HTTPS抓包

安装完成后，在手机上打开一个Https的页面，然后在电脑上打开Fiddler就能看到请求了：

![](http://upload-images.jianshu.io/upload_images/5018455-a3d8537a26b3b402.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 3. 其它

Fiddler和Charles一样拥有文件替换、模拟速度等功能，就不多介绍了，自己摸索。
