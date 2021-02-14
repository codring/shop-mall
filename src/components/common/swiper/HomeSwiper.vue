<template>
  <swiper ref="mySwiper" :options="swiperOptions" class="swiper-wrapp-style">
    <swiper-slide v-for="item in list" :key="item.acm">
      <a :href="item.link" style="block">
        <img :src="item.image" class="swiper-img-style" />
      </a>
    </swiper-slide>
    <div class="swiper-pagination" slot="pagination"></div>
  </swiper>
</template>

<script>
import { swiper, swiperSlide } from "vue-awesome-swiper";
export default {
  name: "HomeSwiper",
  components: {
    swiper,
    swiperSlide,
  },
  data() {
    return {
      swiperOptions: {
        pagination: {
          el: ".swiper-pagination",
        },
        observer: true, 
        observeParents: true,
        autoplay: {
          disableOnInteraction: false,
          delay: 1000,
        },
      },
    };
  },
  computed: {
    swiper() {
      return this.$refs.mySwiper.swiper;
    },
  },
  mounted() {
    this.swiper.slideTo(3, 1000, false);
  },
  props: {
    list: {
      type: Array
    },
  },
};
</script>

<style scoped>
.swiper-wrapp-style {
  width: 100%;
  height: 12.2rem;
}
.swiper-img-style {
  width: 100%;
  background-position: center;
  background-size: cover;
  min-height: 12.2rem;
}
</style>