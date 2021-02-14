<template>
  <div class="page">
    <router-view></router-view>
    <tab-bar>
      <tab-bar-item path="/home">
        <img src="@/assets/img/tabbar/home.svg" class="img-wrapp-style" slot="tabbar-default-img">
        <img src="@/assets/img/tabbar/home_active.svg" class="img-wrapp-style"  slot="tabbar-active-img">
        <span class="text-wrapp-style" slot="tabbar-item-text">首页</span>
      </tab-bar-item>
      <tab-bar-item path="/category">
        <img src="@/assets/img/tabbar/category.svg" class="img-wrapp-style" slot="tabbar-default-img">
        <img src="@/assets/img/tabbar/category_active.svg" class="img-wrapp-style"  slot="tabbar-active-img">
        <span class="text-wrapp-style" slot="tabbar-item-text">分类</span>
      </tab-bar-item>
      <tab-bar-item path="/cart">
        <img src="@/assets/img/tabbar/shopcart.svg" class="img-wrapp-style" slot="tabbar-default-img">
        <img src="@/assets/img/tabbar/shopcart_active.svg" class="img-wrapp-style"  slot="tabbar-active-img">
        <span class="text-wrapp-style" slot="tabbar-item-text">购物车</span>
      </tab-bar-item>
      <tab-bar-item path="/profile">
        <img src="@/assets/img/tabbar/profile.svg" class="img-wrapp-style" slot="tabbar-default-img">
        <img src="@/assets/img/tabbar/profile_active.svg" class="img-wrapp-style"  slot="tabbar-active-img">
        <span class="text-wrapp-style" slot="tabbar-item-text">我的</span>
      </tab-bar-item>
    </tab-bar>
  </div>
</template>
<script>
import TabBar from '@/components/common/tabbar/TabBar.vue';
import TabBarItem from '@/components/common/tabbar/TabBarItem.vue'
export default {
  name:'App',
  data() {
    return {
      
    }
  },
  components:{
    TabBar,
    TabBarItem
  }

}
</script>
<style  scoped>
@import "./assets/css/base.css";
@import "./assets/fonts/iconfont.css";
.page{
  padding-bottom: 3rem;
}
</style>
