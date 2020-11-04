P29 前端基础-ES6-let&const

1. ES的基本介绍

   > 1、简介
   > ECMAScript 6.0(以下简称ES6,ECMAScript是一种由Ecma国际（前身为欧洲计算机制造商协会，英文名称是European Computer Manufacturers Association)通过ECMA-262标准化的脚本程序设计语言）是JavaScript语言的下一代标准，已经在2015年6月正式发布了，并且从ECMAScript6开始，开始采用年号来做版本。即ECMAScript2015,就是ECMAScript6。它的目标，是使得JavaScript语言可以用来编写复杂的大型应用程序，成为企业级开发语言。
   > 每年一个新版本。
   >
   > 2、所以，ECMAScript是浏览器脚本语言的规范，而各种我们熟知的js语言，如JavaScript则是规范的具体实现。

2. 开启注释块运行体验，很简单

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<body>
		<script>
			// var声明的变量往往会域
			// let声明的变量有严格局部作用域
			
			// {
			// 	var a=1;
			// 	let b=2;
			// }
			
			// //输出1
			// console.log(a);
			
			// //输出 b is not defined
			// console.log(b); 
			
		// =====================分隔符==================
			// // 多次声明不会保存
			// var a=1;
			// var a=2;
			
			// // 多次声明报错
			// let b=3;
			// // Identifier 'b' has already been declared
			// // let b=4;
			// console.log(a);
			// console.log(b);
			
		// =====================分隔符==================
			
			// // undefined
			// console.log(a);
			// var a=10;
			
			//  // b is not defined
			// console.log(b);
			// let b=20;
		// =====================分隔符==================
		
		// // 声明之后不允许改变，一旦声明必须初始化，否则会报错
		// // const b;
		// const a=2;
		// // 再次声明就会报错，Assignment to constant variable.
		// // a=3;
		// console.log(a);
		
			
		</script>
		
		
	</body>
</html>

```

