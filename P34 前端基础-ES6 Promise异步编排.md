# P33 前端基础-ES6 Promise异步编排

有点难，多看几遍，多敲几次。。。

#### Promise

> 在JavaScript的世界中，所有代码都是单线程执行的。由于这个“缺陷”，导致JavaScript的所有网络操作，浏览器事件，都必须是异步执行。异步执行可以用回调函数实现。一旦有一连串的ajax请求a,b,c,d...后面的请求依赖前面的请求结果，就需要层层嵌套。这种缩进和层层嵌套的方式，非常容易造成上下文代码混乱，我们不得不非常小心翼翼处理内层函数与外层函数的数据，一旦内层函数使用了上层函数的变量，这种混乱程度就会加剧……总之，这种层叠上下文的层层嵌套方式，着实增加了神经的紧张程度。

案例：用户登录，并展示该用户的各科成绩。在页面发送两次请求

1.查询用户，查询成功说明可以登录
2.查询用户成功，查询科目
3.根据科目的查询结果，获取去成绩

分析：此时后台应该提供三个接口，一个提供用户查询接口，一个提供科目的接口，一个提供各科成绩的接口，为了渲染方便，最好响应json数据。在这里就不编写后台接口了，而是提供三个json文件，直接提供json数据，模拟后台接口：

建立文件夹，并在文件夹下创建一下文件：

corse_score_10.json

```json
{
	"id":100,
	"score":90
}
```

user.json

```json
{
	"id":1,
	"name":"zhangsan",
	"password":"123456"
}
```

user_corse_1.json

```json
{
	"id":10,
	"name":"Chinese"
}
```

建立promise.html文件进行模拟

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<script src="js/jquery.js"></script>
		
	</head>
	<body>
		
		<!-- 提前避坑
		 1、记得导入jquery依赖
		 2、记得url写的时候，尤其是带有${data.id}一定要检查是不是反引号，而不是引号
		 -->
		
		<script>
			// // 1、可以封装异步操作
			// let p=new Promise((resolve,reject)=>{
			// 	// 异步操作
			// 	$.ajax({
			// 		url:'mooc/user.json',
			// 		success:function(data){
			// 			console.log("查询用户成功：",data)
			// 			resolve(data);
			// 		},
			// 		error:function(err){
			// 			reject(err);
			// 			}
			// 	});
			// });
			
			// p.then((obj)=>{
			// 	return new Promise((resolve,reject)=>{
			// 		$.ajax({
			// 			url:`mooc/user_corse_${obj.id}.json`,
			// 			success:function(data){
			// 				console.log("查询用户课程成功：",data)
			// 				resolve(data);
			// 			},
			// 			error:function(err){
			// 				reject(err)
			// 			}
			// 		})
			// 	})
				
			// }).then((data)=>{
			// 	$.ajax({
			// 		url:`mooc/corse_score_${data.id}.json`,
			// 		success:function(data){
			// 			console.log("查询课程分数成功：",data)
						
			// 		},
			// 		error:function(err){
						
			// 		}
			// 	})
			// })
			
			function get(url,data){
				return new Promise((resolve,reject)=>{
					$.ajax({
						url:url,
						data:data,
						success:function(data){
							resolve(data)
							
						},
						error:function(err){
							reject(err)
						}
					})
				})
			}
			
			get('mooc/user.json')
			.then((data)=>{
				console.log("用户查询成功：",data)
				return get(`mooc/user_corse_${data.id}.json`);
			}).then((data)=>{
				console.log("用户课程查询成功：",data)
				return get(`mooc/corse_score_${data.id}.json`)
			}).then((data)=>{
				console.log("课程成绩查询成功：",data)
				
			}).catch((err)=>{
				console.log("出现异常：",err)
			});
			
		</script>
	</body>
</html>

```

