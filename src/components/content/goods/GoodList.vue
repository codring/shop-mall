<template>

    <div
      class="goods-position-wrapp flex flex-justtify-between flex-wrapp"
    
    >
      <good-list-item
        v-for="(item, index) in goods"
        :goods-item="item"
        :key="index"
      ></good-list-item>
    </div>
    

</template>

<script>
import GoodListItem from "@/components/content/goods/GoodListItem.vue";
export default {
  name: "GoodList",
  props: {
    goods: {
      type: Array,
      default() {
        return [];
      },
    },
    isPullUpLoad: {
      type: Boolean,
      default() {
        return false;
      },
    },
  },
  components: {
    GoodListItem,
  },
};
</script>

<style scoped>
.goods-position-wrapp {
  padding: 0 0.55rem 0.6rem;
  width: 100%;
  height: auto;
  background: #ffffff;
}
.goods-position-wrapp .goods-info-wrapp {
  width: 49%;
  height: auto;
  border-radius: 0.8rem;
  margin-top: 0.6rem;
  display: block;
      box-shadow: 0rem 0.8rem 1.5rem #ececec, -0.1rem -0.5rem 1rem #ffffff;
}
.goods-info-wrapp .goods-info-img {
  width: 100%;
  height: 15rem;
  border-radius: 0.8rem 0.8rem 0 0;
}
.goods-info-wrapp .goods-info-content {
  width: 100%;
  height: auto;
  border-radius: 0 0 0.8rem 0.8rem;
  background: #ffffff;
  padding: 0.7rem 0.6rem 0.55rem;
}
.goods-info-content .content-name-style {
  color: #413e3e;
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: 1;
  overflow: hidden;
  text-overflow: ellipsis;
  font-size: 0.8rem;
}
.goods-info-content .price-info-wrapp {
  padding-top: 0.3rem;
  color: pink;
}
.price-info-wrapp .orgPrice-info-style {
  font-size: 0.75rem;
  text-decoration: line-through;
}
.goods-info-content .price-price-style {
  font-size: 0.8rem;
  font-weight: bold;
  margin-left: 0.5rem;
}
</style>