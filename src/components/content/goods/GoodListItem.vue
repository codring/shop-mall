<template>
    <a :href="goodsItem.link" class="goods-info-wrapp">
      <img :src="goodsItem.show.img" class="goods-info-img" />
      <div class="goods-info-content">
        <div class="content-name-style">{{ goodsItem.title }}</div>
        <div class="price-info-wrapp flex flex-align-end">
          <div class="orgPrice-info-style">{{goodsItem.orgPrice}}</div>
          <div class="price-price-style">￥{{goodsItem.price}}</div>
        </div>
      </div>
    </a>
</template>

<script>
export default {
  name: "GoodListItem",
  props: {
    goodsItem: {
      type: Object,
      default(){
        return {}
      }
    },
    data() {
      return {
        
      }
    },
  },

};
</script>

<style scoped>
.goods-position-wrapp {
  padding: 0 0.35rem 0.6rem;
  width: 100%;
  height: auto;
}
.goods-position-wrapp .goods-info-wrapp {
  width: 49%;
  height: auto;
  border-radius: 0.8rem;
  margin-top: 0.6rem;
  display: block;
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
.goods-info-content .price-info-wrapp{
  padding-top: 0.3rem;
  color: pink;
}
.price-info-wrapp .orgPrice-info-style{
  font-size: 0.75rem;
  text-decoration:line-through;
}
.goods-info-content .price-price-style {
  font-size: 0.8rem;
  font-weight: bold;
  margin-left: 0.5rem;
}
</style>