<template>
  <div class="header">
    <div class="header-left">
      <div class="iconfont back-icon">&#xe65b;</div>
    </div>
    <div class="header-input">
      <span class="iconfont">&#xe608;</span>
      <span>输入城市景点/游玩主题</span>
    </div>
    <router-link to="/city">
      <div class="header-right">
        <span>{{this.city}}</span>
        <span class="iconfont arrow-icon">&#xe605;</span>
      </div>
    </router-link>
  </div>
</template>

<script>
import { mapState } from 'vuex'
export default {
  name: 'HomeHeader',
  computed: {
    ...mapState(['city'])
  }
}
</script>

<style lang="stylus" scoped>
@import '~styles/variables.styl'
.header
  line-height: .86rem;
  display: flex;
  background: $bgColor;
  color: #fff;
  font-size:16px;
  .header-left
    width: .64rem;
    float: left;
    .back-icon
      text-align: center;
  .header-input
    flex: 1;
    background: #fff;
    padding-left: 7px;
    border-radius: 5px;
    height:.62rem;
    line-height: .62rem
    margin-top: .12rem;
    margin-left: .2rem;
    color: #ccc;
  .header-right
    min-width: 1.04rem;
    padding: .1rem;
    float: right;
    text-align: center;
    color: white;
    .arrow-icon
      font-size: .2rem;
      margin-left: -0.04rem;
</style>
