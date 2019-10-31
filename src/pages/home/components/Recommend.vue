<template>
  <div class="recommend">
    <div class="recommend-title">热销推荐</div>
    <ul>
      <router-link
        tag="li"
        :to="'/detail/'+ item.id"
        class="item border-bottom"
        v-for="item of list"
        :key="item.id"
      >
        <img :src="item.imgUrl" class="item-image"/>
        <div class="item-info">
          <p class="item-price">{{item.price}}</p>
          <p class="item-desc">{{item.desc}}</p>
          <button class="item-button">查看详情</button>
        </div>
      </router-link>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HomeRecommend',
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
    margin-top: .2rem;
    line-height: .8rem;
    background: #eee;
    text-indent: .2rem;
  .item
    overflow: hidden;
    display: flex;
    height: 1.9rem;
    .item-image
      width: 1.7rem;
      height:1.7rem;
      padding: .1rem;
      border-radius: .1rem;
    .item-info
      flex: 1;
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
      .item-button
        background: #00bff0;
        padding: .2rem;
        border-radius: .06rem;
        margin-top: .1rem;
        line-height: .2rem;
</style>
