# node mvc 框架

一个简单的mvc框架，使用koa2,nunjucks,sequelize等构建，并添加日志组件log4js和测试框架mocha。

支持自定义模板引擎（需要自己实现自己模板加载器）
支持restful 风格api（案例后面以微信小程序补充）

并没有使用pm2去管理项目进程，因为整合目标仅用于学习参考，如果有用于生产环境的需求，欢迎issue，后期补充。

## 环境要求
Redis必须，mysql非必须，但是已经集成了sequelize，可以参考注释掉的示例使用。
node版本 > 8

## 如何使用
- clone 项目
git clone 项目地址
- 安装所需依赖（推荐使用cnpm）
```
npm install
```
- 配置redis，在config/redis目录下，启动redis
- 测试环境运行项目
```
npm run dev
```

![启动界面](https://maxiaofeng-blog.oss-cn-hangzhou.aliyuncs.com/markdown/WX20180324-201926%402x.png)

- 访问本机地址：http://127.0.0.1:3000
- 输入账户密码登录 test01 123456

## 如何配置
所有的配置文件在config目录下，都分为dev配置和prod配置，根据开发环境的不同，加载不同的配置文件。

## 如何自定义
- 静态资源是放在assets目录下的，是由assets-handler（我称作静态资源处理器）加载的，生产环境建议使用nginx处理静态资源，以获得高效的性能。
- 模板引擎默认使用的是nunjucks，你可以修改template-loader.js（我称它为模板加载器）来加载你喜欢用的模板引擎。

## 如何测试
测试脚本默认都放在项目的test文件夹下，编写好脚本之后直接执行
```
npm test 
```

测试框架使用mocha，使用方式参考mocha官方文档。
实际开发中业务较为复杂，一般使用测试框架，并不能满足业务需求，测试框架只能测试简单的工具类，期望的响应状态和类型。对于动态数据，比如较为复杂的sql中的数据每次取值可能都不同，测试覆盖不到业务层面。有更好的测试方式，欢迎提供！

## 关于安全
因为本框架是自己学习过程中搭建，没有刻意考虑安全问题，框架层面nunjuck默认开启了转义，可以避免xss攻击，建议sequelize使用参数绑定的方式生成sql，可以避免sql注入攻击（参考squelize文档）。对于csrf攻击，后期会加入配置开启，并定义中间件处理。

## 声明
该整合框架仅用于学习和测试，如用于生产环境，请自行评估安全性,影响性。本框架在整合过程中，参考了廖雪峰老师的博客，并根据自己生产环境中使用其他语言框架的经验做了一定调整。
本案例是在mac上编写，未在windows上做过充分测试，不保证windows系统的可用性。

欢迎star，您的star是我继续维护更新的动力，更欢迎各位大神批评指正。