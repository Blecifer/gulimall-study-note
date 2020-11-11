# P43 前端基础-Vue 生命周期和钩子函数

官网链接：https://cn.vuejs.org/v2/guide/instance.html#%E6%95%B0%E6%8D%AE%E4%B8%8E%E6%96%B9%E6%B3%95

*注意一点，钩子函数要定义在methos方法体外面*

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<body>
		<div id="app">
			<span>id:{{id}}</span>
			<br />
			<span>name:{{name}}</span>
			<h2>有{{num}}人点赞</h2>
			<button @click="add">点赞</button>
		</div>
		<script src="./js/vue.js"></script>
		<script>
			let vm = new Vue({
				el: "#app",
				data: {
					id: "101",
					name: "张三",
					num: 100,


				},
				methods: {
					show() {
						return this.num;
					},
					add() {
						return this.num++;
					}

				},


				beforeCreate: function() {
					console.group('beforeCreate 创建前状态===============》');
					console.log("%c%s", "color:red", "el     : " + this.$el); //undefined
					console.log("%c%s", "color:red", "data   : " + this.$data); //undefined
					console.log("%c%s", "color:red", "message: " + this.message)
				},
				created: function() {
					console.group('created 创建完毕状态===============》');
					console.log("%c%s", "color:red", "el     : " + this.$el); //undefined
					console.log("%c%s", "color:red", "data   : " + this.$data); //已被初始化
					console.log("%c%s", "color:red", "message: " + this.message); //已被初始化
				},
				beforeMount: function() {
					console.group('beforeMount 挂载前状态===============》');
					console.log("%c%s", "color:red", "el     : " + (this.$el)); //已被初始化
					console.log(this.$el);
					console.log("%c%s", "color:red", "data   : " + this.$data); //已被初始化 
					console.log("%c%s", "color:red", "message: " + this.message); //已被初始化 
				},
				mounted: function() {
					console.group('mounted 挂载结束状态===============》');
					console.log("%c%s", "color:red", "el     : " + this.$el); //已被初始化
					console.log(this.$el);
					console.log("%c%s", "color:red", "data   : " + this.$data); //已被初始化
					console.log("%c%s", "color:red", "message: " + this.message); //已被初始化
				},
				beforeUpdate: function() {
					console.group('beforeUpdate 更新前状态===============》');
					console.log("%c%s", "color:red", "el     : " + this.$el);
					console.log(this.$el);
					console.log("%c%s", "color:red", "data   : " + this.$data);
					console.log("%c%s", "color:red", "message: " + this.message);
				},
				updated: function() {
					console.group('updated 更新完成状态===============》');
					console.log("%c%s", "color:red", "el     : " + this.$el);
					console.log(this.$el);
					console.log("%c%s", "color:red", "data   : " + this.$data);
					console.log("%c%s", "color:red", "message: " + this.message);
				},
				beforeDestroy: function() {
					console.group('beforeDestroy 销毁前状态===============》');
					console.log("%c%s", "color:red", "el     : " + this.$el);
					console.log(this.$el);
					console.log("%c%s", "color:red", "data   : " + this.$data);
					console.log("%c%s", "color:red", "message: " + this.message);
				},
				destroyed: function() {
					console.group('destroyed 销毁完成状态===============》');
					console.log("%c%s", "color:red", "el     : " + this.$el);
					console.log(this.$el);
					console.log("%c%s", "color:red", "data   : " + this.$data);
					console.log("%c%s", "color:red", "message: " + this.message)
				}

			})
		</script>
	</body>
</html>

```

