# P50 商品服务-API-三级分类-删除-逻辑删除



![image-20201117000619866](P50 商品服务-API-三级分类-删除-逻辑删除.assets/image-20201117000619866.png)

![image-20201117004012256](P50 商品服务-API-三级分类-删除-逻辑删除.assets/image-20201117004012256.png)

![image-20201117004049578](P50 商品服务-API-三级分类-删除-逻辑删除.assets/image-20201117004049578.png)

所谓的逻辑删除就是调用update方法，把show_status改为0（其值为1时可见，其值为0时不可见）