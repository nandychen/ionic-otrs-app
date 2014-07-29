ionic-otrs-app
==============
a otrs(Open-source Ticket Request System) app base on ionic<br>
基于Ionic开发的Otrs(http://www.otrs.com/?lang=zh-hans IT运维管理/客服系统)手机客户端<br>
主要实现客户查询工单、投诉、加急处理的功能

##1.运行程序
###下载源码
git clone https://github.com/little51/ionic-otrs-app.git<br>或download zip
###下载依赖包
* 在ionic-otrs-app目录下执行：npm install 
* 为了使用gulp，还需要执行：npm install gulp -g
* 最新版的gulp-connect在windows上由于对盘符大小写判断有误，会出现403错误，具体解决方法如下
 修改ionic-otrs-app\node_modules\gulp-connect\node_modules\connect\node_modules\serve-static\node_modules\send\lib\send.js
* 注释掉第413行,return this.error(403)

###启动程序
gulp

###运行App（在浏览器中测试）
为了解决跨域访问问题
* Linux：chromium-browser --disable-web-security&
* Window:chrome浏览器启动项加 --disable-web-security
* http://localhost:8080
* 用户名：640001 口令:0000

##2.将ionic-otrs-app用于您的otrs
###导入GenericTicketConnector webservice接口
http://yourhost/otrs/index.pl?Action=AdminGenericInterfaceWebservice<br>
导入 ionic-otrs-app\ws\GenericTicketConnector.yml<br>
###修改app中webservice调用指向
在 ionic-otrs-app\www\js\ticketservices.js和authservices.js中的wsUrl变量值

##3.用到的技术要点
* gulp管理包依赖关系
* gulp-connect 实现web监听（浏览器环境下）
* GenericInterfaceWebservice 实现App调用otrs后台
* locationChangeStart event拦截实现Session控制
* $window.localStorage 实现Session的本地持久
* ion-infinite-scroll 实现分页

##4.文件列表
index.html       主页面
js:
* app.js           路由和模块引入
* authservices.js  登录控制
* common.js        xml转json
* controllers.js   控制器
* ticketservices.js工单查询服务
templates:
* about.html      关于
* login.html      登录
* myinfo.html     我的
* tabs.html       Tab
* ticket-detail.html 工单详细
* ticket-index.html  工单索引

##5.license
MIT license