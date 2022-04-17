<p align="center">
<img src="https://s3.bmp.ovh/imgs/2022/03/b32a1257070aed37.webp" alt="ABlog logo" style="width: 200px; height: 200px">
</p>

<p align="center">
	<img src="https://img.shields.io/badge/JDK-1.8+-orange">
	<img src="https://img.shields.io/badge/SpringBoot-2.6.4-brightgreen">
	<img src="https://img.shields.io/badge/MyBatis-3.5.5-red">
	<img src="https://img.shields.io/badge/Vue-2.6.11-brightgreen">
	<img src="https://img.shields.io/badge/license-MIT-blue">
	<img src="https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fgithub.com%2FNaccl%2FNBlog&count_bg=%2344CC11&title_bg=%23555555&icon=notist.svg&icon_color=%231296DB&title=hits&edge_flat=false">
</p>

## 简介

本着『前后端分离，人不分离』的要领，开发了此基于 Spring Boot + Vue 前后端分离博客系统

## 功能

### 已经完成功能

* [ ]  登录
* [ ]  注册
* [ ]  文章列表
* [ ]  文章归档
* [ ]  标签
* [ ]  关于
* [ ]  点赞与评论
* [ ]  留言
* [ ]  历程
* [ ]  文章详情（支持代码语法高亮）
* [ ]  文章详情目录
* [ ]  移动端适配
* [ ]  github 授权登录

## 后端

主流技术栈：

1. 核心框架：[Spring Boot](https://github.com/spring-projects/spring-boot)
2. 安全框架：[Spring Security](https://github.com/spring-projects/spring-security)
3. Token 认证：[jjwt](https://github.com/jwtk/jjwt)
4. 持久层框架：[MyBatis](https://github.com/mybatis/spring-boot-starter)
5. 分页插件：[PageHelper](https://github.com/pagehelper/Mybatis-PageHelper)
6. NoSQL缓存：[Redis](https://github.com/redis/redis)
7. Markdown 转 HTML：[commonmark-java](https://github.com/commonmark/commonmark-java)
8. 离线 IP 地址库：[ip2region](https://github.com/lionsoul2014/ip2region)
9. 定时任务：[quartz](https://github.com/quartz-scheduler/quartz)
10. UserAgent 解析：[yauaa](https://github.com/nielsbasjes/yauaa)

邮件模板参考自[Typecho-CommentToMail-Template](https://github.com/MisakaTAT/Typecho-CommentToMail-Template)

基于 JDK8 开发，8以上要添加依赖：

```xml
<dependency>
    <groupId>javax.xml.bind</groupId>
    <artifactId>jaxb-api</artifactId>
    <version>2.3.0</version>
</dependency>
```

模块：

- [ablog-common]：公共子模块，前台系统和后台系统分别取依赖公共模块
- [ablog-api]：前台系统接口模块
- [ablog-cms-api]：后台系统接口模块

# 前端

Vue 项目基于 @vue/cli4.x 构建：

- Vue^2.x
- Vue Router
- Vuex

JS 依赖及参考的 css：

- [axios](https://github.com/axios/axios)
- [moment](https://github.com/moment/moment)
- [nprogress](https://github.com/rstacruz/nprogress)
- [v-viewer](https://github.com/fengyuanchen/viewerjs)
- [prismjs](https://github.com/PrismJS/prism)
- [APlayer](https://github.com/DIYgod/APlayer)
- [MetingJS](https://github.com/metowolf/MetingJS)
- [lodash](https://github.com/lodash/lodash)
- [mavonEditor](https://github.com/hinesboy/mavonEditor)
- [echarts](https://github.com/apache/echarts)
- [tocbot](https://github.com/tscanlin/tocbot)
- [iCSS](https://github.com/chokcoco/iCSS)

### 后台 UI

- 后台 CMS 部分基于 [vue-admin-template](https://github.com/PanJiaChen/vue-admin-template) 模板进行开发
- UI 框架为 [Element UI](https://github.com/ElemeFE/element)

### 前台 UI

- [Semantic UI](https://semantic-ui.com/)：主要使用，页面布局样式，个人感觉挺好看的，比较适合前台界面的开发，语义化的 css，可惜该框架 Vue 版的开发完成度不高，见 [Semantic UI Vue](https://semantic-ui-vue.github.io/#/)
- [Element UI](https://github.com/ElemeFE/element)：部分使用，一些小组件，弥补了 Semantic UI 的不足，便于快速实现效果
- 文章排版：基于 [typo.css](https://github.com/sofish/typo.css) 修改

## 快速开始

1. 创建 MySQL 数据库 `nblog`，并执行 `/blog-api/ablog.sql`初始化表数据
2. 修改配置信息 `ablog-api/src/main/resources/application-dev.yml`
3. 安装 Redis 并启动
4. 启动后端服务
5. 分别在 `ablog-cms`和 `ablog-view`目录下执行 `yarn install`安装依赖
6. 分别在 `ablog-cms`和 `ablog-view`目录下执行 `yarn run serve`启动前后台页面

## 注意事项

一些常见问题：

- MySQL 确保数据库字符集为 `utf8mb4`的情况下通常没有问题（”站点设置“及”文章详情“等许多表字段需要 `utf8mb4`格式字符集来支持 emoji 表情，否则在导入 sql 文件时，即使成功导入，也会有部分字段内容不完整，导致前端页面渲染数据时报错）
- 确保 Maven 能够成功导入现版本依赖，请勿升级或降低依赖版本
- 注意修改 `application-dev.properties`的配置信息
  - Redis 若没有密码，留空即可
  - 注意修改 `token.secretKey`，否则无法保证 token 安全性
  - `spring.mail.host`及 `spring.mail.port`的默认配置为阿里云邮箱，其它邮箱服务商参考关键字 `spring mail 服务器`（邮箱配置用于接收评论提醒）

## Thanks

感谢 [JetBrains](https://www.jetbrains.com/) 提供的非商业开源软件 License

感谢上面提到的每个开源项目
