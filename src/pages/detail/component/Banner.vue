<template>
  <div class="banner">
    <img class="banner-img" :src="bannerImg" :alt="sightName">
    <div class="banner-info">
      <div class="title">{{sightName}}</div>
      <div class="number-warpper">
        <span class="iconfont">&#xe61b;</span>
        <span class="number">{{bannerImgs.length}}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DetailBanner',
  props: {
    sightName: String,
    bannerImg: String,
    bannerImgs: Array
  }
}
</script>

<style lang="stylus" scoped>
  .banner
    position relative
    padding-bottom 55%
    background #ccc
    .banner-img
      position absolute
      top 0
      width 100%
    .banner-info
      position absolute
      left 0
      right 0
      bottom .2rem
      display flex
      justify-content space-between
      padding 0 .2rem
      color #fff
</style>
