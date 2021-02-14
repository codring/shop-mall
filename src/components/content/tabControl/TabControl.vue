<template>
  <div>
    <div class="tab-control-wrapp flex flex-justify-around">
      <span class="tab-item-wrapp" v-for="(item, index) in tabbar" :key="index" :class="{ active: index === current_index }" @click="tab_click(index)" :data-type="item.parmas_name" :data-page="item.parmas_name">
      {{ item.views_name }}
      </span>
    </div>
    
  </div>
</template>

<script>
export default {
  name: "TabControl",
  data() {
    return {
      current_index: 0
    };
  },
  props: {
    tabbar: {
      type: Array,
    },
  },
  methods: {
    tab_click: function (index) {
      this.current_index = index;
      this.$emit('tabClick',index)
    },
  },
};
</script>

<style>
.tab-control-wrapp {
  width: 100%;
  padding: 0 0.5rem;
  height: auto;
  background: #ffffff;
  margin-top: 0.5rem;
}
.tab-control-wrapp .tab-item-wrapp {
  padding: 0.8rem 0.3rem;
  font-size: 0.7rem;
}
.tab-control-wrapp .tab-item-wrapp.active {
  padding: 0.6rem 0.3rem 0;
  font-size: 0.9rem;
  color: pink;
  border-bottom: 0.2rem solid pink;
}
</style>