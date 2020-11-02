# P18 快速开发配置测试微服务基本的CURD功能

1. 整合mybatis-plus

   1. gulimall-common的pom文件导入依赖（这里按照上面的导入renren-fast依赖就不会有问题，主要是加入了mybatis-plus-boot-starter，版本是3.2.0）

   2. 配置

      1. 配置数据源

         1. gulimall-common的pom导入数据库驱动（mysql-connector驱动，版本是8.0.17（老师的））

         2. gulimall-product创建application.yml文件配置数据源信息，这里username不是name，否则可能会连接失败

            ```yaml
            # 配置数据源信息
            spring:
              datasource:
                username: root
                password: root
                url: jdbc:mysql://192.168.56.10:3306/gulimall_pms?useUnicode=true&characterEncoding=UTF-8&useSSL=false&serverTimezone=Asia/Shanghai
                driver-class-name: com.mysql.cj.jdbc.Driver
            
            #告诉 mybatis-plus，sql映射文件位置
            mybatis-plus:
              mapper-locations: classpath:/mapper/**/*.xml
              global-config:
                db-config:
                  id-type: auto
            
            ```

            

      2. 配置mybatis-plus

         1. 使用@MapperScan，在product module的GulimallProductApplication启动类中添加注释。（其实不加也会自动找到的）

            ```java
            @MapperScan("com.atguigu.gulimall.product.dao")
            @SpringBootApplication
            public class GulimallProductApplication {
            ```

         2. 告诉 mybatis-plus，sql映射文件位置，在上面。

2.测试

```java
@SpringBootTest
class GulimallProductApplicationTests {

    @Autowired
    BrandService brandService;
    @Test
    void contextLoads() {
        BrandEntity brandEntity=new BrandEntity();
        
//        测试插入数据
//        brandEntity.setDescript("华为NB");
//        brandEntity.setName("华为");
//        brandService.save(brandEntity);
//        System.out.println("保存成功");

        
//        测试修改数据
//        brandEntity.setBrandId(1L);
//        brandEntity.setName("xiaomi");
//        brandEntity.setDescript("love xiaomi");
//        brandService.updateById(brandEntity);
//        System.out.println("update success!");

//        测试查询数据
//        List<BrandEntity> list = brandService.list(new QueryWrapper<BrandEntity>().eq("brand_id", "1L"));
//        list.forEach((item)->{
//            System.out.println(item);
//        });

    }

}
```

没有报错，奈斯~~