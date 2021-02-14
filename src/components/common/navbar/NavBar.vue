<template>
  <div class="nav-bar flex flex-justify-around flex-align-center" @click="back()">
    <slot name="left"></slot>
    <slot name="center"></slot>
    <slot name="right"></slot>
  </div>
</template>

<script>
export default {
  name:'NarBar',
  methods: {
    back(){
      this.$router.go(-1)
    }
  },
}
</script>

<style scoped>
  .nav-bar {
    height: 2.2rem;
    line-height: 2.2rem;
    text-align: center;
    box-shadow: 0 1px 1px rgba(100,100,100,.1);
    background: pink;
  }

  .left, .right {
    width: 60px;
    font-size: 1rem;
    color: #ffffff;
  }
  .center-input-wrapp{
    position:relative;
  }
  .center-input-wrapp i{
    font-size: 0.7rem;
    color: #c7c1c7;
    position: absolute;
    left: 0.75rem;
    top: 0;
    height: 1.6rem;
    line-height: 1.6rem;
  }
  .center-input{
    flex: 1;
    width: 100%;
    height: 1.6rem;
    background: #ffffff;
    border-radius: 0.8rem;
    font-size: 0.8rem;
    padding: 0 2rem;
    align-content: center;
    border: none;
  }
  .center-input::-webkit-input-placeholder{
    color: #c7c1c7;
  }
  .center-title {
    flex: 1;
    font-size: 1rem;
    color: #ffffff;
  }
</style>