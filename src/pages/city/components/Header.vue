<template>
  <div class="header">
    <router-link to="/">
      <div class="iconfont header-back">&#xe605;</div>
    </router-link>
    <div class="header-title">城市选择</div>
  </div>
</template>

<script>
export default {
  name: 'CityHeader'
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  .header
    height: $headerHeight
    background: $bgColor
    line-height $headerHeight
    text-align center
    color: #fff
    .header-back
      float left
      padding-left .2rem
      color: #fff
</style>
