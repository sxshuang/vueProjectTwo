<template>
  <div>
    <!-- fixed是固定 -->
    <mt-header title="我们的信息管理系统"></mt-header>

    <router-view class="tmpl"></router-view>

    <mt-tabbar v-model="selected" fixed>
      <!-- 路由名称通过id 来的，不要写中文， -->
      <mt-tab-item id="home">
        <img @click="changeHash" slot="icon" src="./assets/img/index.png">
        首页
      </mt-tab-item>
      <mt-tab-item id="member">
        <img @click="changeHash" slot="icon" src="./assets/img/vip.png">
        会员
      </mt-tab-item>
      <mt-tab-item id="shopcart">
        <img @click="changeHash" slot="icon" src="./assets/img/shopcart.png">
        购物车
      </mt-tab-item>
      <mt-tab-item id="search">
        <img @click="changeHash" slot="icon" src="./assets/img/find.png">
        搜索
      </mt-tab-item>
    </mt-tabbar>
  </div>
</template>
<script>
export default {
  data() {
    return {
      selected: ""
    };
  },
  methods: {
    changeHash() {
      // （如果不加 nextTick 这个，只放函数里的内容）该调用早于了，子组件赋值给父组件的selected
      this.$nextTick(function() {
        // 在vue完成渲染任务以后的行为
        this.$router.push({
          name:this.selected
        })
      })
    }
  },
  watch: {
    // 函数简单的监视，如果是对象则为深度监视 (给点击事件了，先不要监视了)
    // selected (newV, oldV) {
    //   this.$router.push({
    //     name: newV
    //   })
    // }
  }
};
</script>
<style scoped>
</style>
