<template>
  <div>
    <tab-bar>
      <tab-bar-item path="/home">
        <img slot="item-icon" src="~assets/img/tabbar/home.png">
        <img slot="item-icon-active" src="~assets/img/tabbar/homed.png">
        <div slot="item-text">首页</div>
      </tab-bar-item>
      <tab-bar-item path="/category">
        <img slot="item-icon" src="~assets/img/tabbar/fun.png">
        <img slot="item-icon-active" src="~assets/img/tabbar/funed.png">
        <div slot="item-text">分类</div>
      </tab-bar-item>
      <tab-bar-item path="/cart">
        <img slot="item-icon" src="~assets/img/tabbar/oeder.png">
        <img slot="item-icon-active" src="~assets/img/tabbar/ordered.png">
        <div slot="item-text">订单</div>
      </tab-bar-item >
      <tab-bar-item path="/profile">
        <img slot="item-icon" src="~assets/img/tabbar/index.png">
        <img slot="item-icon-active" src="~assets/img/tabbar/indexed.png">
        <div slot="item-text">我的</div>
      </tab-bar-item>
    </tab-bar>
  </div>
</template>

<script>
import TabBar from "@/components/common/tabbar/TabBar";
import TabBarItem from "@/components/common/tabbar/TabBarItem";
export default {
  name: "MainTabBar",
  components:{
    TabBar,TabBarItem
  }
}
</script>

<style scoped>

</style>