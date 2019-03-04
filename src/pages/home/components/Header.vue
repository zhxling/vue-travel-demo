<template>
  <div class="header">
    <div class="header-left">
      <div class="iconfont back-icon">&#xe605;</div>
    </div>
    <div class="header-input">
      <div class="header-input-box">
        <span class="iconfont">&#xe61b;</span>
        <span>输入城市/景点/游玩主题</span>
      </div>
    </div>
    <router-link to='/city'>
      <div class="header-right">
          <span>{{this.city}}</span>
          <span class="iconfont">&#xe65c;</span>
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
  },
  mounted () {
    console.log(mapState(['city']))
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  .header
    display:flex
    flex-wrap: nowrap
    height: $headerHeight
    background: $bgColor
    align-items: center
    color: #fff
    .header-left
      width: 0.4rem
      padding: 0 .2rem
      font-size: 0.36rem
      text-align: center
    .header-input
      flex-grow: 1
      .header-input-box
        height: .6rem
        line-height: .6rem
        border-radius: 3px
        background: #fff
        color: #e4e7ea
    .header-right
      padding-left .2rem
      padding-right .1rem
      text-align: center
      color #fff
</style>
