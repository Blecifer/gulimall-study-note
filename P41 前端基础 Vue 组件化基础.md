# P41 前端基础 Vue 组件化基础

> 组件其实也是一个Vue实例，因此它在定义时也会接收：data、methods、生命周期函数等，不同的是组件不会与页面的元素绑定，否则就无法复用了，因此没有el属性。但是组件渲染需要html模板，所以增加了template属性，值就是HTML模板全局组件定义完毕，任何vue实例都可以直接在HTML中通过组件名称来使用组件了data必须是一个函数，不再是一个对象。
>
> 
>
> 定义好的组件可复用，提高效率

*全剧组件与局部组件*

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<body>

		<!-- 没有绑定vue对象所以全局组件不可用 -->
		<div>
			<counter></counter>
		</div>

		<div id="app">
			<button @click="count++">被点击了 {{count}} 次</button>
			<br />
			<!-- 全局组件使用 -->
			<counter></counter>
			<counter></counter>
			<br>
			<!-- 局部组件使用 -->
			<app-button></app-button>
			<app-button></app-button>


		</div>


		<script src="./js/vue.js"></script>

		<script>
			//全局组件记住全局注册的行为必须在根 Vue 实例 (通过 new Vue) 创建之前发生。
			Vue.component("counter", {
				template: `<button id="app" @click="count++">被点击了~ {{count}} 次</button>`,
				data() {
					return {
						count: 1
					}
				}
			})

			// 局部组件注册
			const buttonCounter = {
				template: `<button id="app" @click="count++">被点击了--- {{count}} 次</button>`,
				data() {
					return {
						count: 1
					}
				}
			}


			let vm = new Vue({
				el: "#app",
				data: {
					count: 0,
				},
				// 局部组件使用
				components: {
					// 形式为key-value；key为局部组件的名字，value为注册的组件名称
					"app-button": buttonCounter,
				}
			})
		</script>

	</body>
</html>

```

