## **Spring Boot 教程推荐**

下面的项目中要属艿艿的 SpringBoot-Labs 最为深入，这点当你看完所有项目之后就很容易看出来。

我开源的 springboot-guide 的话，有时间还是继续维护起来吧！分享一些实际有用的东西，让大家看了之后又就可以用到项目上。

**1.spring-boot-demo（15.2k star）**

spring boot demo 是一个用来深度学习并实战 spring boot 的项目，目前总共包含 65 个集成 demo，已经完成 53 个。

你也可以通过这个项目学习到 Spring Boot 与基本所有技术的集成，比如 actuator(`监控`)、JPA(强大的 ORM 框架)、mybatis(强大的 ORM 框架)、mybatis-plus(快速操作 Mybatis）等等。

项目地址：[https://github.com/xkcoding/spring-boot-demo](https://link.zhihu.com/?target=https%3A//github.com/xkcoding/spring-boot-demo) 。

这个仓库的部分内容如下：



![img](https://pic4.zhimg.com/v2-f95366d2307d402f0700b73d55edf18f_b.jpg)



**2.SpringBoot-Labs(4k star)**

基于 Spring Boot 2.X 的 Spring Boot 深入学习项目。

市面上的 Spring Boot **基础**入门文章很多，但是**深度**入门文章却很少。艿艿的 Spring Boot 系列，带你全面且深度地学习 Spring Boot 2.X 。

另外，这个项目不光有 Spring Boot 2.X,还有 Spring Cloud、Spring Cloud Alibaba、Dubbo、分布式消息队列、分布式事务这些内容。

项目地址： [https://github.com/YunaiV/SpringBoot-Labs](https://link.zhihu.com/?target=https%3A//github.com/YunaiV/SpringBoot-Labs) 。

这个仓库的部分内容如下：



![img](https://pic2.zhimg.com/v2-1b91baeaed32cd9603153bdde952c235_b.jpg)



**3.springboot-guide(2.1k star)**

这个项目是 Guide 自己开源的，说实话更新的不是特别勤快，有一段时间没更新了。

这个项目主要涵盖了 Spring Boot 比较重要的一些知识点，比如如何优雅地进行异常处理。

项目地址：[https://github.com/Snailclimb/springboot-guide](https://link.zhihu.com/?target=https%3A//github.com/Snailclimb/springboot-guide) 。

这个仓库的部分内容如下：



![img](https://pic3.zhimg.com/v2-c08607a106769524ac4fa3b4423fe8ae_b.jpg)



**4.springBoot（3.8k star）**

这个项目同样是 springboot 框架与其它组件结合如 jpa、mybatis、websocket、security、shiro、cache 等。

项目地址：[https://github.com/527515025/springBoot](https://link.zhihu.com/?target=https%3A//github.com/527515025/springBoot)。

这个仓库的部分内容如下：



![img](https://pic4.zhimg.com/v2-0b596fbc59dcdf6bd108e3e71f543d0f_b.jpg)



## **Spring Boot 实战项目/脚手架推荐**

对于下面的开源项目，可以这样说每一个开源项目都有很多可以优化的地方。如果你想真正学到东西的话，建议不光要把项目跑起来更要去优化！

简单说几个比较容易的优化点：



1. 全局异常处理，很多项目这方面都做的不是很好，可以参考我的这篇文章：[《使用枚举简单封装一个优雅的 Spring Boot 全局异常处理！》](https://link.zhihu.com/?target=https%3A//mp.weixin.qq.com/s/Y4Q4yWRqKG_lw0GLUsY2qw) 来做优化。
2. 项目的技术选型优化，比如使用 Guava 做本地缓存的地方可以换成 **Caffeine** 。Caffeine 的各方面的表现要更加好！再比如 Controller 层是否放了太多的业务逻辑。
3. 数据库方面：数据库设计可否优化？索引是否使用使用正确？SQL 语句是否可以优化？
4. …



**1.eladmin(9.4k star)**

eladmin 是一款基于 Spring Boot 2.1.0 、 Jpa、 Spring Security、redis、Vue 的前后端分离的后台管理系统，项目采用分模块开发方式， 权限控制采用 RBAC，支持数据字典与数据权限管理，支持一键生成前后端代码，支持动态路由。

这个开源项目基本稳定，并且后续作者还会继续优化。并且，完全开源！这个真的要为原作者点个赞，如果大家觉得这个项目有用的话，建议可以稍微捐赠一下原作者支持一下。后端整理代码质量、表设计等各个方面来说都是很不错的。前后端分离，前端使用的是国内常用的 vue 框架，也比较容易上手。



![img](https://pic3.zhimg.com/v2-525a13ead7e3ad5b322c5c57e0488c3e_b.jpg)



项目地址： [https://github.com/elunez/eladmin](https://link.zhihu.com/?target=https%3A//github.com/elunez/eladmin) 。



![img](https://pic3.zhimg.com/v2-c6878ba7ab649b290f4d9b14bea04572_b.jpg)

![img](https://pic2.zhimg.com/v2-0f70065f22b2a6cbcb68d7771663b4b5_b.jpg)



**2.mall(36.1k star)**

一位朋友的项目，非常不错，值得推荐!

mall 这个项目的话，是一套电商系统，包括前台商城系统及后台管理系统，基于 SpringBoot+MyBatis 实现，采用 Docker 容器化部署。

前台商城系统包含首页门户、商品推荐、商品搜索、商品展示、购物车、订单流程、会员中心、客户服务、帮助中心等模块。 后台管理系统包含商品管理、订单管理、会员管理、促销管理、运营管理、内容管理、统计报表、财务管理、权限管理、设置等模块。

另外，这个项目还提供了详细的文档，帮助你进一步学习。

![img](https://pic4.zhimg.com/v2-cef47fd5622ff886bafe0c67aa963c13_b.jpg)

项目地址：[https://github.com/macrozheng/mall](https://link.zhihu.com/?target=https%3A//github.com/macrozheng/mall) 。

![img](https://pic1.zhimg.com/v2-a42a6a435dee8ca99dba053541889a68_b.jpg)



**3.vhr(16.9k star)**

江南一点雨大佬的力作。整个项目不论是前端还是后端的代码质量都比较高，非常值得学习。

然后，vhr（微人事）这个项目的话，是一个前后端分离的人力资源管理系统，后端基于 SpringBoot 开发，前端基于 Vue 开发，并且，项目加入常见的企业级应用所涉及到的技术点，例如 Redis、RabbitMQ 等。

另外，这个项目提供了非常详细的文档。

项目地址：[https://github.com/lenve/vhr](https://link.zhihu.com/?target=https%3A//github.com/lenve/vhr) 。



![img](https://pic4.zhimg.com/v2-7c3d5dec83772488f973afcfa772594f_b.jpg)



**4.favorites-web(3.9k star)**

基于 Spring Boot 2.X 的开源项目。favorites-web（云收藏）是一个使用 Spring Boot 构建的开源网站，可以让用户在线随时随地收藏的一个网站，在网站上分类整理收藏的网站或者文章。

项目地址：[https://github.com/cloudfavorites/favorites-web](https://link.zhihu.com/?target=https%3A//github.com/cloudfavorites/favorites-web) 。



![img](https://pic1.zhimg.com/v2-79a4d1034657585532ca90a7484fd33c_b.jpg)



**5.community(0.8k star)**

开源论坛、问答系统，现有功能提问、回复、通知、最新、最热、消除零回复功能。功能持续更新中…… 技术栈 Spring、Spring Boot、MyBatis、MySQL/H2、Bootstrap。

目前这个写在简历上的重复率还好，自己稍微改造一下还是很有潜力的。

项目地址：[https://github.com/codedrinker/community](https://link.zhihu.com/?target=https%3A//github.com/codedrinker/community) 。



![img](https://pic3.zhimg.com/v2-dfc13c9b0a41172d42ee0c844aead032_b.jpg)



**6.SpringBoot-Shiro-Vue(2.7k star)**

提供一套基于 Spring Boot-Shiro-Vue 的权限管理思路.前后端都加以控制,做到按钮/接口级别的权限

项目地址： [https://github.com/Heeexy/SpringBoot-Shiro-Vue](https://link.zhihu.com/?target=https%3A//github.com/Heeexy/SpringBoot-Shiro-Vue) 。



![img](https://pic4.zhimg.com/v2-cb0d37fa1e9adba73b92663138ef17a3_b.jpg)