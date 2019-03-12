<template>
  <div>
    <router-link
      to="/"
      tag="div"
      v-show="showAbs">
      <div ref="header" class="iconfont header-abs-back">&#xe605;</div>
    </router-link>
    <div class="detail-header-fixed" v-show="!showAbs" :style="opacityStyle">
      <router-link to="/">
        <div class="iconfont back-icon">&#xe605;</div>
      </router-link>
      景点详情
    </div>
  </div>
</template>

<script>
export default {
  name: 'DetailHeader',
  props: {
    banner: Object
  },
  data () {
    return {
      showAbs: true,
      bannerHeight: 0,
      headerHeight: 60,
      opacityStyle: {
        opacity: 0
      }
    }
  },
  methods: {
    handleScroll (event) {
      console.log('dd')
      const scrollTop = document.documentElement.scrollTop
      if (scrollTop > this.headerHeight) {
        let opacity = scrollTop / (this.bannerHeight - this.headerHeight)
        opacity = opacity > 1 ? 1 : opacity
        this.opacityStyle = { opacity }
        this.showAbs = false
      } else {
        this.showAbs = true
      }
    }
  },
  mounted () {
    window.addEventListener('scroll', this.handleScroll)

    setTimeout(() => {
      this.headerHeight = this.$refs.header.offsetHeight
      this.bannerHeight = this.banner.$refs.banner.offsetHeight
    }, 1000)
  },
  destroyed () {
    window.removeEventListener('scroll', this.handleScroll)
  }
}
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl';
  .header-abs-back
    position fixed
    top 0
    left .2rem
    line-height $headerHeight
  .detail-header-fixed
    position fixed
    top 0
    left 0
    right 0
    text-align center
    line-height $headerHeight
    background $bgColor
    color #fff
    z-index 2
    .back-icon
      position absolute
      left 0
      top 0
      padding: 0 .2rem
      color #fff
</style>
