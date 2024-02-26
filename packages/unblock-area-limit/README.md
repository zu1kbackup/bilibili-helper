# 解除B站区域限制

反馈问题前，先看这篇文档！！！大多数常见的问题，这里都有说明  
反馈问题前，先看这篇文档！！！大多数常见的问题，这里都有说明  
反馈问题前，先看这篇文档！！！大多数常见的问题，这里都有说明  

不要在Greasyfork中提交反馈，去GitHub，Greasyfork问题追踪系统太弱了，不好用

[点击进入设置页面](https://bangumi.bilibili.com/anime/5551)

![设置截图](https://user-images.githubusercontent.com/4396864/149929866-780bd8a2-413b-4539-a071-cdb66c5bc80e.png)

## 自定义代理服务器

由于用的人太多，前段时间BiliPlus直接被B站屏蔽了。故今后只能自己搭建代理服务器。  
这里简述几种可用的代理服务器，搭建完成后将网址添到脚本的“自定义代理服务”里面就行了。

**注意，代理服务器拥有你B站帐号的大部分访问权限，请不要使用不可信之人提供的代理服务器**

### 1. 反向代理

用Nginx反代`api.bilibili.com`，需要有VPS，比较贵，配置文件见[这里](https://github.com/ipcjs/bilibili-helper/pull/711#issue-542876230)

### 2. PHP空间

PHP空间相比VPS会便宜很多，目前有些小公司会提供PHP空间，php脚本用@zzc1086写的[这个](https://github.com/zzc10086/grocery_store/blob/master/bili_proxy/BPplayurl.php)就行

### 3. 阿里云函数计算

[阿里云函数计算](https://www.aliyun.com/product/fc)按次计费，还有免费额度，可以算是最便宜的了，配置也十分简单。@zzc1086也写了[函数计算版的php脚本](https://github.com/zzc10086/grocery_store/blob/master/bili_proxy/aliyun_Serverless_BPplayurl.php)，直接用就行

详细搭建方式，参考@realLyans写的[简易教程](https://github.com/ipcjs/bilibili-helper/issues/710#issuecomment-748976481)

### 4. 腾讯云CDN

CDN本质也是反向代理（  
详见@MoeACG-Xyrh写的教程：[使用腾讯云CDN解除哔哩哔哩番剧区域限制](https://www.lovewx.club/%e4%bd%bf%e7%94%a8%e8%85%be%e8%ae%af%e4%ba%91cdn%e8%a7%a3%e9%99%a4%e5%93%94%e5%93%a9%e5%93%94%e5%93%a9%e7%95%aa%e5%89%a7%e5%8c%ba%e5%9f%9f%e9%99%90%e5%88%b6/)

### 5. 网友搭建的服务器（**不保证**这些代理服务器是安全的，可信度需要你自己判断）

1. [公共解析服务器](https://github.com/yujincheng08/BiliRoaming/wiki/%E5%85%AC%E5%85%B1%E8%A7%A3%E6%9E%90%E6%9C%8D%E5%8A%A1%E5%99%A8)，哔哩漫游的服务器，脚本也能用，只要记得在地址前加上`https://`就行

| 提供者                                        | 类型       | 区域 | 网址                                                                                    |
| --------------------------------------------- | ---------- | ---- | --------------------------------------------------------------------------------------- |
| [@zzc10086](https://github.com/zzc10086)      | PHP空间    | 香港 | `https://bili-proxy.98e.org`                                                            |
| [@znAaron](https://github.com/znAaron)        | 阿里云函数 | 大陆 | `https://1985592077837091.cn-shanghai.fc.aliyuncs.com/2016-08-15/proxy/bili/bili_prox/` |
| [@AisukaYuki](https://github.com/AisukaYuki/) | 反向代理   | 台湾 | `https://bili.tuturu.top`                                                               |
| [@silicer](https://github.com/silicer)        | 腾讯云函数 | 香港 | `https://service-fi0gz11m-1252917345.hk.apigw.tencentcs.com`                            |

## 开发

最新版引入了rollup.js来打包脚本, 克隆代码后要执行`npm i`安装依赖, 修改代码时要执行`npm run dev:balh`生成打包好的user.js

## 问&答

### 如何安装脚本？

使用脚本前必须安装扩展，各浏览器对应的扩展如下：

1. Firefox浏览器：[Tampermonkey](https://addons.mozilla.org/en-US/firefox/addon/tampermonkey/) 、Greasemonkey 4
2. Chrome浏览器：[Tampermonkey](https://chrome.google.com/webstore/detail/tampermonkey/dhdgffkkebhmkfjojejmpbldmpobfkfo)
    * 访问不了[Chrome 网上应用店](https://chrome.google.com/webstore/category/extensions)的同鞋可以到下面的地址下载crx文件。下载下来的crx文件可能不能直接安装，需要手动拖到扩展管理界面（一般为`chrome://extensions/`）中，应该就能安装成功了：
        * [Tampermonkey各版本百度网盘](https://pan.baidu.com/s/1nuCc4Al)
        * [常用Crx离线安装包下载](https://yurl.sinaapp.com/crx2.php)
    * 国内的360极速浏览器、猎豹浏览器等其实上就是Chrome加个壳，装Tampermonkey就行了
    * 搜狗高速浏览器：[Tampermonkey Legacy](https://ie.sogou.com/app/app_4326.html)
    * Yandex Browser 手机版：详见：[希望可以支持一下手机版的网页](https://github.com/ipcjs/bilibili-helper/issues/112)
    * <del>傲游浏览器：[Violentmonkey](https://extension.maxthon.com/detail/index.php?view_id=1680)</del>（实测即使是最新版，也不兼容该脚本）
    * Edge：基于Chromium的新版Edge，理论上来说是支持的，老版不支持
3. Safari：不支持

### 脚本无效？

1. 如果在[番剧页面](https://bangumi.bilibili.com/anime/5551)中连设置按钮都看不到，说明你的浏览器版本太老了，请更新成最新版；如果还是不行，请换用最新版的[Firefox](https://www.mozilla.org/en-US/firefox/new/)或者[Chrome](https://www.google.com/chrome/browser/desktop/index.html)。
2. 确定你使用的播放器是**HTML5**版的。Flash版请在播放器界面的右上角切换成HTML5版。
3. 确定可以打开[代理服务器上的链接](https://biliplus.ipcjs.top/api/bangumi?season=5551)。 如果打不开，可以点开设置窗口，换个代理服务器试试
4. 对于一些已知错误，脚本会弹窗提示，请认真阅读提示信息，按提示进行操作。
5. 如果依然无效，可能确实是这个脚本的问题了，请到GitHub反馈给我。

### 授权无效？

Chrome 80+上有可能出现的问题，详见：https://github.com/ipcjs/bilibili-helper/issues/588#issuecomment-603830842

### 播放卡顿？

#### “替换upos视频服务器”选项

**目前似乎存在替换upos后加载不出视频的问题！设为“不替换”可关闭该功能。**

在设置中有个“替换upos视频服务器”选项，针对大陆的视频有效果，可以试下。

#### 改hosts

港澳台的视频解析出来的视频文件的域名是`upos-hz-mirrorakam.akamaized.net`，这家CDN貌似没有国内的节点，大多数情况下这个域名都会指向美国的IP，速度特别慢。他们是有香港/台湾节点的，速度会快很多。手动改hosts，将域名解析到较快的IP，能够缓解卡顿的问题。

参考链接:

1. [zz5678/akamBiliChecker: 测试Bilibili海外CDN的下载速度](https://github.com/zz5678/akamBiliChecker)
2. [miyouzi/akamTester: 批量测试B站海外CDN](https://github.com/miyouzi/akamTester)
3. [如何提高B站海外CDN连接速度](https://www.bilibili.com/read/cv3118508)
4. [播放番剧，5秒一卡，速度非常慢 · Issue #401](https://github.com/ipcjs/bilibili-helper/issues/401)

### 看不了1080P画质？

1. 确定你是B站的[大会员](https://big.bilibili.com/site/big.html)
2. 确定当前视频拥有1080P画质的版本
3. 确定你登录了代理服务器（点击脚本设置界面的“帐号授权”，进行登录）

### 看不了付费番剧/影视？

**观看付费番剧/影视的前提是，你登录了代理服务器（点击脚本设置界面的“帐号授权”，进行登录）！！**

相关事项说明：

1. [付费抢先看番剧](https://bangumi.bilibili.com/anime/6012/play#103819)支付金额在特定情况下会显示`9876547210.33`的问题，这是因为代理服务器的接口获取不到金额，为了防止[手抖误操作](https://bangumi.bilibili.com/anime/5852/play?aid=9815508#103960#reply238854223)，默认显示一个逸。使用支付宝/微信扫码可以看到真实金额。
2. 以前的付费接口是不会检测区域的，但最近（2017-10-12）的[一些动画电影](https://bangumi.bilibili.com/movie/12116)的付费接口也会检测区域了，所以即使使用该脚本解除了视频的区域限制，依然没办法付费，只能看前面几分钟。一个解决办法是直接冲B站的大会员，大会员看所有的视频都是不需要付费的🙄。
3. 最近也[有人反馈有些番剧能付费，但付费后依然看不了](https://greasyfork.org/zh-CN/forum/discussion/29953/x)，所以付费前请谨慎

### 关于“被永封的大会员？”选项

**（这个条目并不是说“使用这个脚本会导致你的会员被封”，而是说“如果你有个被永封的大会员帐号，可以通过这个脚本继续观看会员专属视频”）**

1. 注册并登录一个小号
2. 在脚本设置界面勾选“被永封的大会员？”选项
3. 在[代理服务器](https://www.biliplus.com/login)中使用账号密码登录被永封的大会员账号
4. 就可以用小号看1080P了<img src="https://bbs.saraba1st.com/2b/static/image/smiley/nq/001.gif" alt="(扭曲"/>

## 开源

1. 源码仓库：[ipcjs/bilibili-helper at user.js](https://github.com/ipcjs/bilibili-helper/tree/user.js)
2. 代码贡献者：[Contributions](https://github.com/ipcjs/bilibili-helper/graphs/contributors)
3. 部分源码取自：
    - 通知相关：[Yet Another Weibo Filter - 看真正想看的微博](https://tiansh.github.io/yawf/zh-cn.html)
    - 自动跳转相关：[我就是要跳轉(B站番劇投稿頁跳轉去番劇頁)](https://greasyfork.org/zh-CN/scripts/29151)
    - B站视频接口：[soimort/you-get](https://github.com/soimort/you-get)、[哔哩哔哩UWP](https://www.microsoft.com/zh-cn/store/p/%E5%93%94%E5%93%A9%E5%93%94%E5%93%A9uwp/9n7c87236453)

## 友链

0. [BiliPlus - ( ゜- ゜)つロ 乾杯~](https://www.biliplus.com/)
1. [yujincheng08/BiliRoaming: 哔哩漫游，解除B站客户端番剧区域限制的Xposed模块，并且提供其他小功能](https://github.com/yujincheng08/BiliRoaming)
2. [kghost/bilibili-area-limit: Bilibili 港澳台, 解除区域限制](https://github.com/kghost/bilibili-area-limit)

## [高级设置/更新日志/测试页面 等](https://github.com/ipcjs/bilibili-helper/blob/user.js/packages/unblock-area-limit/README.dev.md)
