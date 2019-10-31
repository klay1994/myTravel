<template>
  <div class="recommend">
    <div class="recommend-title">周末去哪儿</div>
    <ul>
      <li class="item border-bottom" v-for="item of list" :key="item.id">
        <div class="item-image-wrapper">
          <img :src="item.imgUrl" class="item-image"/>
        </div>
        <div class="item-info">
          <p class="item-title">{{item.title}}</p>
          <p class="item-desc">{{item.desc}}</p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HomeWeekend',
  props: {
    list: Array
  }
}
</script>

<style lang="stylus" scoped>
@import '~styles/mixins.styl'
.recommend
  font-size: 16px;
  .recommend-title
    line-height: .8rem;
    background: #eee;
    text-indent: .2rem;
  .item-image-wrapper
    height: 0;
    overflow: hidden;
    padding-bottom: 37.09%;
    .item-image
      width: 100%;
      border-radius: .1rem;
  .item-info
    padding: .1rem;
    min-width: 0;
    .item-title
      line-height: .4rem;
      height: .4rem;
      font-size: .32rem;
      ellipsis()
    .item-desc
      line-height: .5rem;
      height: .5rem;
      color: #ccc;
      ellipsis()
</style>
