# weinre

## 简介

weinre 是一款较老的远程调试工具，功能与 Chrome DevTools 相似，需要在页面中插入一段 JS 脚本来实时调试页面 DOM 结构、样式、JS 等，另外它使用的是代理的方式，所以兼容性很好，无论是新老设备系统通吃，但对于有一些局限性：
- elements部分：可以查看dom，修改样式，但无法直接编辑dom
- resource部分：localstorage可以查看，但cookie看不到
- network部分：不知道https请求
- cosole部分：可以看console log、运行js，但无法像firebug那样报出js的错误，更不能加断点调试

## 安装

```
sudo npm -g install weinre
```

## 调试步骤

1. 启动 weinre 监听服务

```
ipconfig getifaddr en0 // 查看本机 IP
weinre --boundHost 192.168.0.107 --httpPort 8091//--boundHost 后填入你本机 IP 地址，--httpPort 后填入端口号，默认为 8080

```

2. 进入 weinre 管理页面

使用 Chrome 浏览器访问 http://192.168.0.107:8091/ ，在管理页面你可以看到使用相关的说明，有进入客户端调试界面的地址、使用的文档、DEMO 页面等等，说明中要求将一段 JS 脚本``` <script src="http://192.168.0.107:8091/target/target-script-min.js#anonymous"></script>```
插入到需要调试的页面中，插入代码后手机访问调试页面
![](http://upload-images.jianshu.io/upload_images/5018455-ccabc37446b9c0ae.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

3. 进入客户端调试界面

点击 debug client user interface：http://192.168.0.107:8091/client/#anonymous 的链接,效果如下：

![](http://upload-images.jianshu.io/upload_images/5018455-ff7155990234e4a6.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![](http://upload-images.jianshu.io/upload_images/5018455-211f326e928506bc.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

这样就可以开始你的调试了

## 补充

- 突破内网限制

大多公司的内网策略，导致手机和PC无法在一个网段，很多调试无法进行，可以利用Weinre搭建一个在外网的服务，再在打包工具里加入测试环境自动添加JS的功能，这样能为我们的调试提供很多方便。

- 多用户

当多用户访问时，只需要修改JS部分```<script src="http://192.168.0.107:8091/target/target-script-min.js#anonymous"></script>```井号后的anonymous，这其实是weinre的id，设置不一样即可

- 其它方案

由于weinre的一些局限，出现了一些基于weinre更方便简单的工具，下面介绍其中之一：spy-debugger

# spy-debugger

## 特性

1. 页面调试＋抓包

2. 操作简单，通过代理的方式拦截所有html自动注入weinre所需的js代码

3. 支持HTTPS

4. spy-debugger内部集成了weinre、node-mitmproxy、AnyProxy

5. 自动忽略原生App发起的https请求，只拦截webview发起的https请求。对使用了SSL pinning技术的原生App不造成任何影响

6. 可以配合其它代理工具一起使用(默认使用AnyProxy)

## 安装

Windows

```
npm install spy-debugger -g
```

Mac 

```
sudo npm install spy-debugger -g
```

## 调试步骤
1. 手机和PC保持在同一网络下
2. 命令行输入spy-debugger，按命令行提示用浏览器打开相应地址
![](http://upload-images.jianshu.io/upload_images/5018455-e6a7fc86c45936d6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
3. 设置手机的HTTP代理，代理IP地址设置为PC的IP地址，端口为spy-debugger的启动端口(默认端口：9888)
- Android设置代理步骤：设置 - WLAN - 长按选中网络 - 修改网络 - 高级 - 代理设置 - 手动
- iOS设置代理步骤：设置 - 无线局域网 - 选中网络 - HTTP代理手动
注意：代理的端口是启动端口9888，不是页面端口59713
4. 安装证书。注：手机必须先设置完代理后再通过(非微信)手机浏览器访问 http://spydebugger.com/cert 安装证书（手机首次调试需要安装证书，已安装了证书的手机无需重复安装)
![Android](http://upload-images.jianshu.io/upload_images/5018455-b81dcbe287d4c063.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![IOS](http://upload-images.jianshu.io/upload_images/5018455-71a06780f8259c25.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
5. 用手机浏览器访问你要调试的页面即可,效果如下
- 调试界面
![](http://upload-images.jianshu.io/upload_images/5018455-572e6bfa7914b524?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 抓包界面(注：如果发现访问https的网站证书不对，可安装此页提供的证书)
![](http://upload-images.jianshu.io/upload_images/5018455-663e2472d253c73b?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



