P33  前端基础-ES6 map&reduce

有点难，但是还可以

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<body>
		<script>
			// 数组中新增了map和reduce方法
			let arr = ['1', '2', '3', '4', '5'];
			
			// arr=arr.map((item)=>{
			// 	return item*2})
			
			arr = arr.map(item	 => item * 2);
			console.log(arr)
			
			// reduce()为数组中的每一个元素一次执行回调函数，不包括数组中被删除或从未被赋值的元素
			// ['2', '4', '6', '8', '10']
			// arr.reduce(callback,[initialValue])
			// 1、previousValue(上一次调用回调返回的值，或者是提供的初始值（initialValue)
			// 2、currentValue(数组中当前被处理的元素）
			// 3、index(当前元素在数组中的索引）
			// 4、array(调用reduce的数组）
			
			// let result=arr.reduce((a,b)=>{
			// 	console.log('上一次处理的值'+a);
			// 	console.log('当前处理的值'+b);
			// 	return a+b;
			// })
			
			let result=arr.reduce((a,b)=>{
				console.log('上一次处理的值'+a);
				console.log('当前处理的值'+b);
				return a+b;
			},100)
			console.log(result)
			
		</script>
	</body>
</html>

```

