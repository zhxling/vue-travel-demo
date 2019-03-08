<template>
  <div>
    <div class="title">热销榜单</div>
    <ul class="list">
      <router-link
        tag="li"
        class="item border-bottom"
        v-for="item of recommendList"
        :key="item.id"
        :to="'/detail/' + item.id">
        <img class="item-img" :src="item.imgUrl" :alt="item.title">
        <div class="item-info">
          <div class="item-title">{{item.title}}</div>
          <div class="item-desc">{{item.desc}}</div>
          <button class="item-button">查看详情</button>
        </div>
      </router-link>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HeadeRecommend',
  props: {
    recommendList: Array
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/mixins.styl';
  .title
    line-height .6rem
    background #ccc
    padding-left .2rem
  .item
    padding .2rem
    display flex
    align-items center
    .item-img
      width 2rem
      height 2rem
    .item-info
      padding-left .2rem
      min-width 0
      .item-title
        font-size .34rem
        padding-bottom .2rem
      .item-desc
        color: #d8d7d7
        padding-bottom .2rem
        ellipsis()
      .item-button
        width 2rem
        height .4rem
        line-height .4rem
        background red
        text-align center
</style>
