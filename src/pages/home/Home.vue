<template>
  <div class="home">
    <home-header></home-header>
    <home-swiper :list = 'swiperList'></home-swiper>
    <home-icons :list = 'iconList'></home-icons>
    <home-recommend :list = 'hotList'></home-recommend>
    <home-weekend :list = 'weekendList'></home-weekend>
  </div>
</template>

<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcons from './components/Icons'
import HomeRecommend from './components/Recommend'
import HomeWeekend from './components/Weekend'
import axios from 'axios'
import { mapState } from 'vuex'
export default {
  name: 'Home',
  components: {
    HomeHeader,
    HomeSwiper,
    HomeIcons,
    HomeRecommend,
    HomeWeekend
  },
  data () {
    return {
      lastCity: '',
      swiperList: [],
      iconList: [],
      hotList: [],
      weekendList: []
    }
  },
  computed: {
    ...mapState(['city'])
  },
  methods: {
    getHomeInfo () {
      axios.get('/api/index.json?city=' + this.city)
        .then(this.getHomeInfoSuccess)
    },
    getHomeInfoSuccess (res) {
      const result = res.data
      if (result.ret && result.data) {
        const data = result.data
        this.swiperList = data.swiperList
        this.iconList = data.iconList
        this.hotList = data.hotList
        this.weekendList = data.weekendList
      }
    }
  },
  mounted () {
    this.lastCity = this.city
    this.getHomeInfo()
  },
  activated () {
    if (this.lastCity !== this.city) {
      this.lastCity = this.city
      this.getHomeInfo()
    }
  }
}
</script>

<style lang="stylus" scoped>
.home
  font-size: 26px;
</style>
