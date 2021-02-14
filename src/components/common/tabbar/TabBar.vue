<template>
  <div class="tabbar-wrapp-style flex flex-justify-around">
    <slot></slot>
  </div>
</template>

<script>
export default {

}
</script>

<style>
  .tabbar-wrapp-style{
    width: 100%;
    height: 2.8rem;
    background: #ffffff;
    box-shadow: 0 -0.1rem 0.5rem #ececec;
    padding:0.3rem 0 0.5rem;
    position: fixed;
    bottom: 0;
  }
</style>