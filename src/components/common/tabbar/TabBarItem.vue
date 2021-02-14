<template>
  <div class="item-wrapp-style flex flex-direction-column flex-align-center" @click="changing()">
    <div v-if="!isActive">
      <slot name="tabbar-default-img"></slot>
    </div>
    <div v-else>
      <slot name="tabbar-active-img"></slot>
    </div>
    <div :class="{default:!isActive,active:isActive}">
      <slot name="tabbar-item-text"></slot>
    </div>
  </div>
</template>

<script>
export default {
  name:'TabBarItem',
  data() {
    return {
      
    }
  },
  methods: {
    changing(){
      this.$router.push(this.path);
    }
  },
  computed:{
    isActive(){
      return this.$route.path.indexOf(this.path)!==-1
    }
  },
  props:{
    path:{
      type: String,
      default:"/home"
    }
  }
}
</script>

<style>
  .item-wrapp-style .img-wrapp-style{
    width: 1.2rem;
  }
 .item-wrapp-style .text-wrapp-style{
    font-size: 0.8rem;
    display: block;
 }
 .default{
   color: #000000;
 }
 .active{
   color: pink;
   font-weight: bold;
 }
</style>