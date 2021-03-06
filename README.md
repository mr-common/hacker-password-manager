
## 开源协议补充说明：

* [ ✔️ ] fork、star、push
* [ ✔️ ] 自建服务，发布体验版本的小程序，并允许少量用户使用（≤50人）
* [ ✔️ ] 借鉴项目，二次开发并开源
* [ ❌ ] 出售代码等所有获利行为
* [ ❌ ] 拷贝代码并发布线上版本
* [ ❌ ] 其它商业目的、注册商标、专利申请

<hr />

## Hacker密码

相比1.0版本，此次升级重新设计了页面语言、操作流程、加解密和通信方式。 

### 前言

目前市面上大多数的密码管理器通常采用一个主密码作为应用密码，所有保存的账户密码等敏感信息采用服务端加密的方式保存下来，这种以一个密码来保护所有密码的方式。

当然这里并不是说目前采用这种方式的密码管理器就不安全， 越来越多的密码管理工具通过引入其他身份验证、用户行为分析等方式来保护您的账户安全。

Hacker密码更多的是一次尝试和实践，旨在用一种新的形式来探索密码保护。同时也希望通过开源透明的方式给更多有密码存储需要的用户一个值得信赖的选择。

### 为什么不做本地化离线存储的加密工具

的确。本地存储从某种意义上而言，的确让人更容易接受这款软件，毕竟所有的隐私信息都存储在我信赖的机器上。 但是更容易接受并不意味着就更安全，逆向工程、暴力破解使得很多离线应用变得并不那么安全。

### 为什么说Hacker密码是值得信赖的隐私保护工具

#### 完全开源

前后端代码、数据库设计、加解密设计逻辑这些完全开源在github和gitee两大平台。

#### 支持私有部署

您可以clone代码，并部署在自己的服务器上。通过修改内部加密参数，达到完全私有化的隐私保护。

> 依照开源协议，您只可以发布少于50人使用的体验版小程序。不可发布线上版！

#### 本地化加密

软件采用本地生成随机参数加解密的离线化方式对隐私数据进行保护。

#### 密钥文件“防复制”

密钥文件本身并不是一串明文参数，他是由本地化生成的加解密参数、服务端身份验证参数混淆、加密、压缩产生的。因此，即便得到了您的密钥文件，他也无法直接从密钥文件内获取最初用于加密的参数，同时在使用密钥的过程中，会先对使用者的身份进行认证。故即便是复制了您的密钥文件，如果没有得到你的微信身份授权，一样是无法使用的。

#### 多方“不见面”加密

整个过程会有用户端、应用端、服务端、微信端参与，每一加密传递过程都至少引入两方。同时参与加密的参数尽可能的由其中一方产生、不被其他方所知（具备认证作用的参数除外）。

## 加密逻辑（简图）

<img src="docs/encryptionProcess.png" width="100%">

<br />

`科普小剧场`

<img src="docs/exampleStory.png" width="100%">

## 体验

<img src="screenshots/gh_72a49c29672c_1280.jpg" width="200px" height="200px" />

`微信扫码体验`

<hr />

## 帮助

### 视频教程

* [记录隐私信息、创建密钥](https://v.qq.com/x/page/c3223jlbijc.html)


## 常见问题

* 密钥二维码文件丢失，是否意味着无法再查看我存储的隐私数据

> 是的，密钥文件是完全本地化随机产生的，一旦丢失将无法找回。 但是您可以在创建密钥二维码之后，使用“备份密钥”的功能生成与此密钥二维码对应的备份密钥， 这样在密钥二维码丢失之后，可通过备份密钥进行恢复。
>

* 相比记在心里的密码，密钥二维码岂不是更容易被别人盗用

> 不是这样的，尽管密钥二维码确实容易被别人看到并拍照“盗取”。 但这并不意味着拿到您的密钥二维码便可以获取您的本地加密参数、更不要提明文的敏感信息了[参照上述的“密钥文件防复制”]。
>
> 同时就暴力破解的复杂度上，密钥二维码理论上而言则更为复杂。
>
> 尽管如此，仍烦请您妥善保管自己的密钥二维码文件和备份密钥。
>

## 如何反馈您的问题

如果您还有其他疑问，还可以通过下述方式进行反馈。

#### 开发者

> 如果您有关于项目上的漏洞、程序运行问题。 请在此仓库下提issue [ https://github.com/wahao/hacker-password-manager/issues ] 即可

#### 用户

> 您可以通过官方社区[ https://support.qq.com/products/137031 ] 进行反馈。 


## 项目结构


```

├── [2.6K]  README.md
├── [ 160]  docs                                    
│   ├── [157K]  encryptionProcess.png               - 加密流程
│   ├── [2.7K]  qrRecoverykey.md                    - 备份密钥
│   └── [2.8K]  qrkey.md                            - 密钥二维码
├── [ 704]  miniprogram                             
│   ├── [  96]  account                           
│   │   └── [ 448]  pages
│   │       ├── [4.0K]  detail.js                   
│   │       ├── [  27]  detail.json
│   │       ├── [2.1K]  detail.wxml
│   │       ├── [ 513]  detail.wxss
│   │       ├── [4.4K]  edit.js                     
│   │       ├── [  27]  edit.json
│   │       ├── [2.7K]  edit.wxml
│   │       ├── [ 459]  edit.wxss
│   │       ├── [2.4K]  share.js                   
│   │       ├── [  27]  share.json
│   │       ├── [1.6K]  share.wxml
│   │       └── [ 189]  share.wxss
│   ├── [ 256]  api                               
│   │   ├── [1.3K]  account.js
│   │   ├── [1.1K]  category.js
│   │   ├── [ 146]  index.js
│   │   ├── [1.0K]  key.js
│   │   ├── [ 558]  share.js
│   │   └── [1.0K]  user.js
│   ├── [  96]  app
│   │   └── [ 192]  pages
│   │       ├── [1.2K]  about.js
│   │       ├── [  27]  about.json
│   │       ├── [ 274]  about.wxml
│   │       └── [ 121]  about.wxss
│   ├── [ 733]  app.js
│   ├── [1.6K]  app.json
│   ├── [  15]  app.wxss
│   ├── [  96]  assets
│   │   └── [ 37K]  share.jpg
│   ├── [  96]  category
│   │   └── [ 192]  pages
│   │       ├── [1.3K]  apply.js
│   │       ├── [  30]  apply.json
│   │       ├── [ 610]  apply.wxml
│   │       └── [ 142]  apply.wxss
│   ├── [ 640]  components
│   │   ├── [ 192]  account-category
│   │   │   ├── [1.9K]  index.js
│   │   │   ├── [  51]  index.json
│   │   │   ├── [ 941]  index.wxml
│   │   │   └── [ 657]  index.wxss
│   │   ├── [ 192]  button
│   │   │   ├── [ 830]  index.js
│   │   │   ├── [  48]  index.json
│   │   │   ├── [ 586]  index.wxml
│   │   │   └── [ 756]  index.wxss
│   │   ├── [ 192]  clipboard-card
│   │   │   ├── [ 653]  index.js
│   │   │   ├── [  48]  index.json
│   │   │   ├── [ 338]  index.wxml
│   │   │   └── [ 334]  index.wxss
│   │   ├── [ 224]  empty
│   │   │   ├── [ 290]  index.js
│   │   │   ├── [  48]  index.json
│   │   │   ├── [ 171]  index.wxml
│   │   │   ├── [ 194]  index.wxss
│   │   │   └── [  96]  source
│   │   │       └── [117K]  no-data.png
│   │   ├── [ 192]  half-dialog
│   │   │   ├── [1.3K]  index.js
│   │   │   ├── [  48]  index.json
│   │   │   ├── [ 689]  index.wxml
│   │   │   └── [ 912]  index.wxss
│   │   ├── [ 256]  icon
│   │   │   ├── [ 393]  index.js
│   │   │   ├── [  48]  index.json
│   │   │   ├── [ 201]  index.wxml
│   │   │   ├── [ 148]  index.wxss
│   │   │   └── [ 160]  sources
│   │   │       ├── [ 672]  dark
│   │   │       │   ├── [3.0K]  add.png
│   │   │       │   ├── [7.6K]  app.png
│   │   │       │   ├── [ 12K]  archives.png
│   │   │       │   ├── [4.9K]  back.png
│   │   │       │   ├── [ 13K]  boom.png
│   │   │       │   ├── [7.6K]  close.png
│   │   │       │   ├── [4.6K]  copy.png
│   │   │       │   ├── [ 12K]  earth.png
│   │   │       │   ├── [ 10K]  fingerprint.png
│   │   │       │   ├── [5.5K]  home.png
│   │   │       │   ├── [6.9K]  list.png
│   │   │       │   ├── [7.5K]  refresh.png
│   │   │       │   ├── [ 11K]  restore.png
│   │   │       │   ├── [4.3K]  save.png
│   │   │       │   ├── [4.8K]  scan.png
│   │   │       │   ├── [ 13K]  share.png
│   │   │       │   ├── [4.0K]  success.png
│   │   │       │   └── [7.1K]  trash.png
│   │   │       └── [ 672]  white
│   │   │           ├── [3.2K]  add.png
│   │   │           ├── [8.5K]  app.png
│   │   │           ├── [ 16K]  archives.png
│   │   │           ├── [5.3K]  back.png
│   │   │           ├── [ 19K]  boom.png
│   │   │           ├── [8.2K]  close.png
│   │   │           ├── [4.8K]  copy.png
│   │   │           ├── [ 16K]  earth.png
│   │   │           ├── [ 15K]  fingerprint.png
│   │   │           ├── [5.9K]  home.png
│   │   │           ├── [7.5K]  list.png
│   │   │           ├── [8.2K]  refresh.png
│   │   │           ├── [ 16K]  restore.png
│   │   │           ├── [4.6K]  save.png
│   │   │           ├── [5.5K]  scan.png
│   │   │           ├── [ 16K]  share.png
│   │   │           ├── [4.2K]  success.png
│   │   │           └── [7.6K]  trash.png
│   │   ├── [ 192]  image-cropper
│   │   │   ├── [ 36K]  index.js
│   │   │   ├── [  23]  index.json
│   │   │   ├── [2.2K]  index.wxml
│   │   │   └── [1.8K]  index.wxss
│   │   ├── [ 256]  input
│   │   │   ├── [1.7K]  index.js
│   │   │   ├── [  96]  index.json
│   │   │   ├── [1.1K]  index.wxml
│   │   │   ├── [ 673]  index.wxss
│   │   │   └── [ 128]  sources
│   │   │       └── [ 14K]  upload.png
│   │   ├── [ 192]  layout
│   │   │   ├── [1.0K]  index.js
│   │   │   ├── [  90]  index.json
│   │   │   ├── [ 257]  index.wxml
│   │   │   └── [ 188]  index.wxss
│   │   ├── [ 192]  navigation
│   │   │   ├── [1.3K]  index.js
│   │   │   ├── [  48]  index.json
│   │   │   ├── [ 565]  index.wxml
│   │   │   └── [ 459]  index.wxss
│   │   ├── [ 192]  navigator
│   │   │   ├── [ 431]  index.js
│   │   │   ├── [  48]  index.json
│   │   │   ├── [ 376]  index.wxml
│   │   │   └── [ 255]  index.wxss
│   │   ├── [ 256]  network-image
│   │   │   ├── [ 620]  index.js
│   │   │   ├── [  48]  index.json
│   │   │   ├── [ 293]  index.wxml
│   │   │   ├── [ 103]  index.wxss
│   │   │   └── [ 128]  sources
│   │   │       └── [ 21K]  error.png
│   │   ├── [ 192]  painter
│   │   │   ├── [ 256]  lib
│   │   │   │   ├── [7.0K]  downloader.js
│   │   │   │   ├── [4.1K]  gradient.js
│   │   │   │   ├── [ 24K]  pen.js
│   │   │   │   ├── [ 25K]  qrcode.js
│   │   │   │   ├── [1.5K]  util.js
│   │   │   │   └── [ 11K]  wx-canvas.js
│   │   │   ├── [ 26K]  painter.js
│   │   │   ├── [  48]  painter.json
│   │   │   └── [1.3K]  painter.wxml
│   │   ├── [ 224]  qrkey
│   │   │   ├── [3.8K]  index.js
│   │   │   ├── [  95]  index.json
│   │   │   ├── [ 638]  index.wxml
│   │   │   ├── [ 224]  index.wxss
│   │   │   └── [1.9K]  qrTemplate.js
│   │   ├── [ 192]  qrscan
│   │   │   ├── [2.0K]  index.js
│   │   │   ├── [  48]  index.json
│   │   │   ├── [ 705]  index.wxml
│   │   │   └── [ 371]  index.wxss
│   │   ├── [ 224]  share-poster
│   │   │   ├── [3.0K]  index.js
│   │   │   ├── [  94]  index.json
│   │   │   ├── [1.1K]  index.wxml
│   │   │   ├── [ 154]  index.wxss
│   │   │   └── [2.8K]  posterTemplate.js
│   │   └── [ 192]  text
│   │       ├── [ 334]  index.js
│   │       ├── [  48]  index.json
│   │       ├── [ 117]  index.wxml
│   │       └── [ 236]  index.wxss
│   ├── [ 192]  config
│   │   ├── [ 634]  config.develop.js             - 开发版参数，本地调试用
│   │   ├── [  20]  config.release.js             - 线上参数，同config.develop.js
│   │   ├── [  20]  config.trial.js               - 体验版参数
│   │   └── [ 794]  index.js
│   ├── [ 192]  custom-tab-bar
│   │   ├── [1.1K]  index.js
│   │   ├── [  48]  index.json
│   │   ├── [ 515]  index.wxml
│   │   └── [ 337]  index.wxss
│   ├── [ 320]  magics
│   │   ├── [3.4K]  ajax.js
│   │   ├── [1.2K]  crypto.js
│   │   ├── [  96]  libs
│   │   │   └── [2.0K]  mp-axios.js
│   │   ├── [2.9K]  qrKeyManage.js
│   │   ├── [3.1K]  qrRecoveryKeyManage.js
│   │   ├── [ 893]  updateManager.js
│   │   ├── [ 632]  util.js
│   │   └── [6.3K]  zip.js
│   ├── [  96]  miniprogram_npm
│   │   └── [ 128]  crypto-js
│   │       ├── [212K]  index.js
│   │       └── [256K]  index.js.map
│   ├── [  54]  package.json
│   ├── [  96]  pages
│   │   └── [ 448]  home
│   │       ├── [4.3K]  add.js
│   │       ├── [  27]  add.json
│   │       ├── [2.5K]  add.wxml
│   │       ├── [ 452]  add.wxss
│   │       ├── [2.0K]  list.js
│   │       ├── [  60]  list.json
│   │       ├── [ 672]  list.wxml
│   │       ├── [ 379]  list.wxss
│   │       ├── [1.4K]  my.js
│   │       ├── [  27]  my.json
│   │       ├── [2.2K]  my.wxml
│   │       └── [ 430]  my.wxss
│   ├── [2.4K]  project.config.json
│   ├── [ 191]  sitemap.json
│   ├── [ 806]  theme.wxss
│   └── [  96]  tools
│       └── [ 192]  pages
│           ├── [2.7K]  recovery.js
│           ├── [  27]  recovery.json
│           ├── [2.5K]  recovery.wxml
│           └── [ 404]  recovery.wxss
├── [ 128]  screenshots
│   └── [257K]  gh_72a49c29672c_1280.jpg
└── [ 448]  server
    ├── [ 256]  apis
    │   ├── [5.6K]  account.js
    │   ├── [1.8K]  category.js
    │   ├── [ 278]  index.js
    │   ├── [1.8K]  key.js
    │   ├── [1.6K]  share.js
    │   └── [2.0K]  user.js
    ├── [ 160]  config
    │   ├── [ 573]  config.dev.js                    - 本地调试参数
    │   ├── [ 460]  config.prod.js                   - 线上参数， 同config.dev.js
    │   └── [ 339]  index.js
    ├── [ 263]  errCode.js
    ├── [ 192]  functions
    │   ├── [1022]  crypto.js
    │   ├── [ 694]  retMsg.js
    │   ├── [ 762]  user.js
    │   └── [ 690]  util.js
    ├── [ 192]  handler
    │   ├── [ 745]  request.auth.js
    │   ├── [2.5K]  request.decrypt.js
    │   ├── [2.1K]  request.file.js
    │   └── [ 605]  response.js
    ├── [1.5K]  index.js
    ├── [ 542]  model.js
    ├── [ 503]  package.json
    ├── [ 256]  schemas
    │   ├── [ 990]  account.js
    │   ├── [ 761]  category.js
    │   ├── [1.2K]  qrkey.js
    │   ├── [1.0K]  recovery.js
    │   ├── [ 733]  share.js
    │   └── [1.5K]  user.js
    ├── [  96]  uploads
    └── [ 288]  wechat
        ├── [ 213]  ac.txt
        ├── [ 507]  auth.js
        ├── [ 107]  index.js
        ├── [1.0K]  secCheck.js
        ├── [ 618]  urls.js
        ├── [3.1K]  util.js
        └── [1.5K]  wxacode.js


```
