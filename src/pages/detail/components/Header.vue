<template>
  <div>
    <router-link class="header-abs" tag="div" to="/" v-show="showAbs">
      <div class="iconfont back-icon">&#xe65b;</div>
    </router-link>
    <div class="header-fixed" v-show="!showAbs" :style="opacityStyle">
      <span>景点详情</span>
      <router-link to="/">
        <div class="iconfont header-fixed-back">&#xe65b;</div>
      </router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DetailHeader',
  data () {
    return {
      showAbs: true,
      opacityStyle: {
        opacity: 0
      }
    }
  },
  methods: {
    handleScroll () {
      const top = document.documentElement.scrollTop
      if (top > 52) {
        let opacity = top / 140
        opacity = opacity > 1 ? 1 : opacity
        this.opacityStyle = {
          opacity
        }
        this.showAbs = false
      } else {
        this.showAbs = true
      }
    }
  },
  activated () {
    window.addEventListener('scroll', this.handleScroll)
  },
  deactivated () {
    window.removeEventListener('scroll', this.handleScroll)
  }
}
</script>

<style lang="stylus" scoped>
@import '~styles/variables.styl'
  .header-abs
    position: absolute
    left: .2rem
    top: .2rem
    width: .8rem
    height: .8rem
    line-height: .8rem
    border-radius: .4rem
    text-align: center
    background: rgba(0,0,0,.5)
    .back-icon
      color: #fff
  .header-fixed
    position: fixed
    z-index: 2
    top: 0
    left: 0
    right: 0
    height: $headerHeight
    line-height: $headerHeight
    color: #fff
    background: $bgColor
    font-size: .32rem
    text-align: center
    .header-fixed-back
      width: .64rem
      text-align: center
      font-size: .4rem
      position: absolute
      top: 0
      left: 0
      color: #ffffff
</style>
