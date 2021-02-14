<template>
  <nav-bar>
    <i class="icon iconfont icon-fanhui left" slot="left"></i>
    <div slot="center" class="center-input-wrapp">
      <i class="icon iconfont icon-sousuo"></i>
      <input class="center-input flex" placeholder="请输入搜索关键字" />
    </div>
    <i class="icon iconfont icon-erweima right" slot="right"></i>
  </nav-bar>
</template>

<script>
import NavBar from "@/components/common/navbar/NavBar.vue";
export default {
  name: "category",
  data() {
    return {
      title: "分类",
    };
  },
  components: {
    NavBar,
  },
};
</script>

<style>
</style>