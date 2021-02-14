<template>
  <div class="wrapper" ref="scroll">
    <div class="content">
      <slot></slot>
    </div>
  </div>
</template>
<script>
import BScroll from "better-scroll";
export default {
  name: "Scroll",
  data() {
    return {
      bscroll: null,
    };
  },
  methods: {},
  mounted() {
    // 创建bsscroll对象
    this.bscroll = new BScroll(this.$refs.scroll, {
      click: true,
      probeType: this.probeType,
      pullUpLoad: this.pullUpLoad,
      observeDOM:true
    });
    // 监听下路操作请求
    if(this.pullUpLoad===true){
      this.bscroll.on("pullingUp",()=>{
        this.$emit("more");
        console.log(this.probeType)
      });
    }
    // 滚动监听
    if(this.probeType===2 || this.probeType===3){
      this.bscroll.on("scroll", (position) => {
        this.$emit("scroll", position);
      });
    }
  },
  props: {
    probeType: {
      probeType: Number,
      default() {
        return 3;
      },
    },
    pullUpLoad: {
      type: Boolean,
      default() {
        return false;
      },
    },
  },
};
</script>

<style scoped>
#scroll {
  height: auto;
  overflow-y: scroll;
}
.content{
  padding-bottom:2.8rem;
}
</style>