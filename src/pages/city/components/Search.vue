<template>
  <div>
    <div class="search">
      <input class="search-input" type="text" placeholder="输入城市名或拼音" v-model="keyWord"/>
    </div>
    <div class="search-content" ref="search" v-show="keyWord">
      <ul>
        <li v-for="item of list" :key="item.id" class="search-item border-bottom" @click="handleCityClick(item.name)">{{item.name}}</li>
        <li class="search-item border-bottom" v-show="hasNoData">没有找到匹配数据</li>
      </ul>
    </div>
  </div>
</template>

<script>
import BScoll from 'better-scroll'
import { mapMutations } from 'vuex'
export default {
  name: 'CitySearch',
  props: {
    cities: Object
  },
  data () {
    return {
      keyWord: '',
      list: [],
      timer: null
    }
  },
  methods: {
    handleCityClick (city) {
      this.changeCity(city)
      this.keyWord = ''
      this.$router.push('/')
    },
    ...mapMutations(['changeCity'])
  },
  computed: {
    hasNoData () {
      return !this.list.length
    }
  },
  watch: {
    keyWord () {
      if (this.timer) {
        clearTimeout(this.timer)
      }
      if (!this.keyWord) {
        this.list = []
        return
      }
      this.timer = setTimeout(() => {
        const result = []
        for (let i in this.cities) {
          this.cities[i].forEach((item) => {
            if (item.spell.includes(this.keyWord) || item.name.includes(this.keyWord)) {
              result.push(item)
            }
          })
        }
        this.list = result
      })
    }
  },
  mounted () {
    this.scroll = new BScoll(this.$refs['search'])
  }
}
</script>

<style lang="stylus" scoped>
@import '~styles/variables.styl'
  .search
    height: .72rem
    background: $bgColor
    padding: .15rem .1rem .05rem
    .search-input
      box-sizing: border-box
      padding: 0 .2rem
      height: .62rem
      line-height: .62rem
      width: 100%
      border-radius: .06rem
      color: #666
      text-align: center
  .search-content
    overflow: hidden
    position: absolute
    top: 1.78rem
    left: 0
    right: 0
    bottom: 0
    z-index: 1
    background: #eee
    .search-item
      line-height: .62rem
      padding-left: .2rem
      background: #fff
      color: #666
</style>
