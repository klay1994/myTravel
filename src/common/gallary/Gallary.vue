<template>
  <div class="container" @click="handleGallaryClick">
    <div class="wrapper">
      <swiper :options="swiperOptions">
        <swiper-slide v-for="(item, index) in imgs" :key="index">
          <img :src="item" class="swiper-image">
        </swiper-slide>
        <div class="swiper-pagination"  slot="pagination"></div>
      </swiper>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CommonGallary',
  props: {
    imgs: {
      type: Array
      // default () {
      //   return [
      //     'https://www.chinapress.com.my/wp-content/uploads/2019/09/song0903b.jpg',
      //     'https://www.chinapress.com.my/wp-content/uploads/2019/09/song0903b.jpg',
      //     'https://www.chinapress.com.my/wp-content/uploads/2019/09/song0903b.jpg'
      //   ]
      // }
    }
  },
  data () {
    return {
      swiperOptions: {
        pagination: '.swiper-pagination',
        paginationType: 'fraction',
        observeParents: true,
        observer: true
      }
    }
  },
  methods: {
    handleGallaryClick () {
      this.$emit('close')
    }
  }
}
</script>

<style lang="stylus" scoped>
  .container  >>> .swiper-container
    overflow: inherit
  .container
    position: fixed
    top: 0
    left: 0
    bottom: 0
    top: 0
    right: 0
    background: #000
    z-index: 99
    display: flex
    flex-direction: column
    justify-content: center
    .wrapper
      height: 0
      width: 100%
      padding-bottom: 100%
      .swiper-image
        width: 100%
      .swiper-pagination
        bottom: -1rem
        color: #ccc
</style>
