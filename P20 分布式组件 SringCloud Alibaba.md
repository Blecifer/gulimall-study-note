# P20 分布式组件 SringCloud Alibaba



#### 1、SpringCloud Alibaba 简介

1)、简介
Spring Cloud Alibaba致力于提供微服务开发的一站式解决方案。此项目包含开发分布式应用
微服务的必需组件，方便开发者通过SpringCloud编程模型轻松使用这些组件来开发分布
式应用服务。|
依托Spring Cloud Alibaba,您只需要添加一些注解和少量配置，就可以将Spring Cloud应用
接入阿里微服务解决方案，通过阿里中间件来迅速搭建分布式应用系统。
https://github.com/alibaba/spring-cloud-alibaba



SpringCloud的几大痛点

> SpringCloud部分组件停止维护和更新，给开发带来不便；
> SpringCloud部分环境搭建复杂，没有完善的可视化界面，我们需要大量的二次开发和定制
> SpringCloud配置复杂，难以上手，部分配置差别难以区分和合理应用

SpringCloud Alibaba的优势：

> 阿里使用过的组件经历了考验，性能强悍，设计合理，现在开源出来大家用
> 成套的产品搭配完善的可视化界面给开发运维带来极大的便利
> 搭建简单，学习曲线低。

结合SpringCloud Alibaba我们最终的技术搭配方案：

> SpringCloudAlibaba-Nacos:注册中心（服务发现/注册）
> SpringCloud Alibaba-Nacos:配置中心（动态配置管理）
> SpringCloud-Ribbon:负载均衡
> SpringCloud-Feign:声明式HTP客户端（调用远程服务）
> SpringCloud Alibaba-Sentinel:服务容错（限流、降级、熔断）
> SpringCloud-Gateway:API网关（webflux编程模式）
> SpringCloud-Sleuth:调用链监控
> SpringCloudAlibaba-Seata:原Fescar,即分布式事务解决方案

#### 2、确定适配版本号

查看spring-boot与spring-cloud的版本号：https://spring.io/projects/spring-cloud

查看spring-cloud与spring-cloud-alibaba的版本号：https://github.com/alibaba/spring-cloud-alibaba/wiki/%E7%89%88%E6%9C%AC%E8%AF%B4%E6%98%8E

自己用的是spring-boot-2.3.5版本

对应的是spring cloud hoxton

以及spring cloud alibaba 2.3.2

#### 3、导入依赖：

在gulimall-common的pom文件中添加依赖如下

```pom
<dependencyManagement>
    <dependencies>
        <dependency>
            <groupId>com.alibaba.cloud</groupId>
            <artifactId>spring-cloud-alibaba-dependencies</artifactId>
            <version>2.2.3.RELEASE</version>
            <type>pom</type>
            <scope>import</scope>
        </dependency>
    </dependencies>
</dependencyManagement>
```

P20完成。