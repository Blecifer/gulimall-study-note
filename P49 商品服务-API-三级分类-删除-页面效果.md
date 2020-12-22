# P49 商品服务-API-三级分类-删除-页面效果

*启动product、gateway、renren-fast三个服务模块*

指改动一个vue文件，细心一点可以的

```vue
<template>

<!--  :expand-on-click-node    show-checkbox    node-key="catId" 具体功能去官网查看
第一个button按钮，v-if="node.level<=2" 这样只有1,2级菜单才能使用添加功能
第二个button按钮，v-if="node.childNodes.length==0"  只有没有子节点的菜单才能使用删除功能
在methods中添加了append和remove方法用来测试
-->
  <el-tree :data="menus" :props="defaultProps" :expand-on-click-node="false" show-checkbox node-key="catId">
    <span class="custom-tree-node" slot-scope="{ node, data }">
      <span>{{ node.label }}</span>
      <span>
        <el-button v-if="node.level<=2" type="text" size="mini" @click="() => append(data)">
          Append
        </el-button>
        <el-button v-if="node.childNodes.length==0" type="text" size="mini" @click="() => remove(node, data)">
          Delete
        </el-button>
      </span>
    </span>
  </el-tree>

</template>

<script>
  export default {
    comments: {},
    props: {},

    data() {
      return {
        menus: [],
        defaultProps: {
          children: 'children',
          label: 'name'
        }

      };
    },

    methods: {
      getMenus() {
        this.$http({
          url: this.$http.adornUrl('/product/category/list/tree'),
          method: 'get',
        }).then(({
          data
        }) => {
          // 注意then里面的data是{data}解构赋值！！！！
          console.log("successly get data...", data.data)
          return this.menus = data.data
        })
      },

      append(data) {
        console.log("append", data)
      },

      remove(node, data) {
        console.log("remove", node, data)
      },

    },

    created() {
      this.getMenus()
    }

  }
</script>

<style scoped>
</style>

```

