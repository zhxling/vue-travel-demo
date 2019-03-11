<template>
  <div>
    <div class="banner" ref="banner" @click="handleBannerClick">
      <img class="banner-img" :src="bannerImg" :alt="sightName">
      <div class="banner-info">
        <div class="title">{{sightName}}</div>
        <div class="number-warpper">
          <span class="iconfont">&#xe61b;</span>
          <span class="number">{{bannerImgs.length}}</span>
        </div>
      </div>
    </div>
    <fade-animation>
      <common-gallary
        :imgs="bannerImgs"
        v-show="showGallary"
        @close="handleGallaryClose">
      </common-gallary>
    </fade-animation>
  </div>
</template>

<script>
import CommonGallary from '@/common/gallary/Gallary'
import FadeAnimation from '@/common/fade/FadeAnimation'

export default {
  name: 'DetailBanner',
  props: {
    sightName: String,
    bannerImg: String,
    bannerImgs: Array
  },
  data () {
    return {
      showGallary: false
    }
  },
  components: {
    CommonGallary,
    FadeAnimation
  },
  methods: {
    handleBannerClick () {
      this.showGallary = true
    },
    handleGallaryClose () {
      this.showGallary = false
    }
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
