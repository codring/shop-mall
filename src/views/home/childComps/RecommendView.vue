<template>
  <div class="recommend flex flex-wrapp">
    <a class="recommend-item flex flex-direction-column" v-for="item in recommend" :key="item.sort" :href="item.link">
      <img :src="item.image" alt="" class="img-info-style">
      <span class="text-info-style">{{item.title}}</span>
    </a>
  </div>
</template>

<script>
export default {
  name:'RecommendView',
  data() {
    return {
      
    }
  },
  props:{
    recommend:{
      type:Array
    }
  }
};
</script>

<style>
  .recommend {
    display: flex;
    width: 100%;
    text-align: center;
    font-size: 0.7rem;
    padding: 1rem 0 1rem;
    background: #ffffff;
  }
  .recommend-item {
    width: 25%;
    text-align: center;
  }

  .recommend-item .img-info-style{
    width: 3.5rem;
    height: 3.5rem;
    margin:0 auto 0.5rem;
  }
  .recommend-item .text-info-style{
    color: #bbb8b8;
    font-size: 0.75rem;

  }
</style>