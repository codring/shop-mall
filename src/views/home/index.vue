<template>
  <div id="home">
    <nav-bar ref="navbar">
      <i class="icon iconfont icon-fanhui left" slot="left"></i>
      <span class="center-title" slot="center">{{ title }}</span>
      <i class="icon iconfont icon-erweima right" slot="right"></i>
    </nav-bar>
    <tab-control :tabbar="tab" @tabClick="tabClick" class="tabControl" v-if="tabControlShow"></tab-control>
    <scroll
      class="contenting"
      @scroll="scrollPosition"
      :probe-type="3"
      ref="scroll"
      :pull-up-load="true"
      @more="loadMore"
    >
      <home-swiper :list="solid" ref="swiper"></home-swiper>
      <recommend-view
        :recommend="recommend.list"
        ref="recommend"
      ></recommend-view>
      <feature-view ref="feature"></feature-view>
      <tab-control :tabbar="tab" @tabClick="tabClick" :class="{controlTop:isOffSetTop}" v-if="!tabControlShow"></tab-control>
      <good-list :goods="goods[currentType].list" v-if="!isPullUpLoad"></good-list>
    </scroll>
    <back-top v-show="isShowTopPlugin" @click.native="backTop"></back-top>
  </div>
</template>

<script>
import HomeSwiper from "@/components/common/swiper/HomeSwiper.vue";
import RecommendView from "@/views/home/childComps/RecommendView.vue";
import FeatureView from "@/views/home/childComps/FeatureView.vue";
import GoodList from "@/components/content/goods/GoodList.vue";

import NavBar from "@/components/common/navbar/NavBar.vue";
import TabControl from "@/components/content/tabControl/TabControl.vue";
import Scroll from "@/components/common/scroll/Scroll.vue";
import BackTop from "@/components/content/backTop/BackTop.vue";

import { getHomeMultidata, getHomeData } from "@/netword/home.js";
export default {
  components: {
    NavBar,
    HomeSwiper,
    RecommendView,
    FeatureView,
    TabControl,
    GoodList,
    Scroll,
    BackTop,
  },
  name: "home",
  data() {
    return {
      title: "首页",
      isClick: false,
      solid: [],
      recommend: {},
      tab: [
        {
          views_name: "流行",
          parmas_name: "pop",
        },
        {
          views_name: "新品",
          parmas_name: "new",
        },
        {
          views_name: "热销",
          parmas_name: "sell",
        },
      ],
      goods: {
        pop: { page: 0, list: [] },
        new: { page: 0, list: [] },
        sell: { page: 0, list: [] },
      },
      currentType: 'pop',
      isPullUpLoad: false,
      isShowTopPlugin: false,
      offSetTop:0,
      isOffSetTop:false,
      tabControlShow:false
    };
  },
  created() {
    this.getHomeMultid();
    this.createdGoods();
  },
  mounted() {
    this.getOffSetTop();
  },
  methods: {
    // 获取商品数量
    getHomeGoods(type) {
      let page= this.goods[type].page+1;
      getHomeData(type, page).then((res) => {
        let list = res.data.data.list;
        list.forEach((item) => {
          this.goods[type].list.push(item);
        });
      });
      this.goods[type].page +=1;
    },
    // 获取其他信息
    getHomeMultid() {
      getHomeMultidata().then((res) => {
        this.solid = res.data.data.banner.list;
        this.recommend = res.data.data.recommend;
      });
    },
    // 初始化获取商品数据
    createdGoods() {
      let type = this.currentType;
      this.getHomeGoods(type)
    },
    // 点击切换商品分类，且获取相应商品的数据
    tabClick(index) {
      switch (index) {
        case 0:
          this.currentType = "pop";
          break;
        case 1:
          this.currentType = "new";
          break;
        case 2:
          this.currentType = "sell";
          break;
      };
      let type = this.currentType;
      console.log(index,"index");
      this.getHomeGoods(type);
      
    },
    // 监听滚动位置
    scrollPosition(position) {
      this.positionY = position.y;
      -position.y > 1000
        ? (this.isShowTopPlugin = true)
        : (this.isShowTopPlugin = false);
      if(-position.y>=this.offSetTop ){
        this.isOffSetTop = true;
        this.tabControlShow = true
      }else{
         this.isOffSetTop = false;
        this.tabControlShow = false
      }
      console.log(-position.y+'-'+this.offSetTop)
    },
    // 返回头部
    backTop() {
      this.$refs.scroll.bscroll.scrollTo(0, 0, 2000);
    },
    // 加载下一页
    loadMore() {
      this.getHomeGoods(this.currentType);
      this.$refs.scroll.bscroll.finishPullUp();
      this.$refs.scroll.bscroll.refresh();
    },
    // 获取偏移高度
    getOffSetTop(){
      clearTimeout(timer);
      let timer = setTimeout(()=>{
        let obj = this.$refs,swiperHeight = obj.swiper.$el.clientHeight,recommendHeight = obj.recommend.$el.clientHeight,featureHeight = obj.feature.$el.clientHeight;
        this.offSetTop = swiperHeight+recommendHeight+featureHeight;
      },2000)
    }
  },
};
</script>

<style scoped>
#home {
  height: 100vh;
  padding-bottom: 2rem;
}
.data-info-wrapp {
  width: 100%;
  height: auto;
  padding: 0 0.5rem;
  background: pink;
  overflow: scroll;
  white-space: nowrap;
  margin-top: -0.22rem;
}
.data-info-wrapp .item-default-style {
  padding: 0.6rem 0;
  font-size: 0.8rem;
  color: #ffffff;
  border-bottom: 1px solid #ffffff;
}
.contenting {
  position: absolute;
  top: 2.2rem;
  bottom: 0rem;
  left: 0;
  right: 0;
}
.controlTop{
  position: fixed;
  left: 0;
  width: 100%;
}
.tabControl{
  position: fixed;
  top:-0.5rem;
  height: auto;
  left: 0;
  z-index: 9;
  width: 100%;
}
</style>