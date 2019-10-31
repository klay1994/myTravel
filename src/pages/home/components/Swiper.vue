<template>
  <div class="wrapper">
    <swiper :options="swiperOption" ref="mySwiper" v-if="showSwiper">
    <!-- slides -->
    <swiper-slide v-for="item of list" :key="item.id">
      <img :src="item.imgUrl" class="swiper-image">
    </swiper-slide>
    <div class="swiper-pagination"  slot="pagination"></div>
    <!-- pagination专门用来显示分页 -->
    <!-- <div class="swiper-button-prev" slot="button-prev"></div>
    <div class="swiper-button-next" slot="button-next"></div> -->
    <!-- 控制左右箭头 -->
    <!-- <div class="swiper-scrollbar"   slot="scrollbar"></div> -->
    <!-- 控制滚动条 -->
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeSwiper',
  props: {
    list: Array
  },
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        /* 配置项，代表可以分页 */
        loop: true
        /* 轮播图可以循环 */
      }
    }
  },
  computed: {
    showSwiper () {
      return this.list.length
    }
  }
}
</script>

<style lang="stylus" scoped>
.wrapper >>> .swiper-pagination--bullet-active
    background: yellowgreen;
.wrapper
    width: 100%;
    height: 0;
    overflow: hidden;
    padding-bottom: 28%;
  .swiper-image
    width: 100%;
</style>
