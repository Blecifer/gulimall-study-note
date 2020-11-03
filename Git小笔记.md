# P21 分布式组件-SpringCloud Alibaba-Nacos注册中心

#### nacos服务

1. 下载nacos服务

   地址：https://github.com/alibaba/nacos/releases

   

2. 开启nacos服务（可能有闪退，开启不成功等问题，建议回退版本，不要用最新的）![image-20201103104859132](C:\Users\Lucifer\AppData\Roaming\Typora\typora-user-images\image-20201103104859132.png)![image-20201103104942373](C:\Users\Lucifer\AppData\Roaming\Typora\typora-user-images\image-20201103104942373.png)

#### 在IDEA中使用nacos服务

1. 导入依赖，因为每个微服务模块都需要导入nacos依赖，所以只在gulimall-common中添加依赖即可

   ```pom
    <dependency>
               <groupId>com.alibaba.cloud</groupId>
               <artifactId>spring-cloud-starter-alibaba-nacos-discovery</artifactId>
           </dependency>
   ```

   ![image-20201103105200875](C:\Users\Lucifer\AppData\Roaming\Typora\typora-user-images\image-20201103105200875.png)

2. 在每个微服务中配置nacos注册中心的地址，并为每个微服务指定名称

   ```yaml
   cloud:
       nacos:
         discovery:
           server-addr: 127.0.0.1:8848
     application:
       name: gulimall-coupon
   ```

   ![image-20201103105617558](C:\Users\Lucifer\AppData\Roaming\Typora\typora-user-images\image-20201103105617558.png)

3. 开启服务，在启动类上添加注解（其实不添加也可以，springboot自动帮我们配置了，包括配置8848端口也是默认配置了）![image-20201103105727426](C:\Users\Lucifer\AppData\Roaming\Typora\typora-user-images\image-20201103105727426.png)

4. 最后开启此微服务即可

#### 查看启动的微服务

​	地址：http://localhost:8848/nacos

​	用户和密码都是：nacos

​	启动成功如下图：

![image-20201103110107621](C:\Users\Lucifer\AppData\Roaming\Typora\typora-user-images\image-20201103110107621.png)