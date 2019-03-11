<template>
  <div>
    <detail-banner
      ref="banner"
      :sightName="sightName"
      :bannerImg="bannerImg"
      :bannerImgs="gallaryImgs">
    </detail-banner>
    <detail-header :banner="bannerElement"></detail-header>
    <div class="list"></div>
  </div>
</template>

<script>
import DetailBanner from './component/Banner'
import DetailHeader from './component/Header'
import axios from 'axios'

export default {
  name: 'Detail',
  components: {
    DetailBanner,
    DetailHeader
  },
  data () {
    return {
      sightName: '',
      bannerImg: '',
      gallaryImgs: [],
      list: [],
      bannerElement: null
    }
  },
  updated () {
    this.bannerElement = this.$refs.banner
    console.log(this.bannerElement)
  },
  methods: {
    getDetailInfo () {
      axios.get('/api/detail.json', {
        params: {
          id: this.$route.params.id
        }
      }).then(this.handleDetailInfoSucc)
    },
    handleDetailInfoSucc (res) {
      res = res.data
      if (res.ret && res.data) {
        const data = res.data
        this.sightName = data.sightName
        this.bannerImg = data.bannerImg
        this.gallaryImgs = data.gallaryImgs
        this.list = data.categoryList
      }
    }
  },
  mounted () {
    this.getDetailInfo()
  }
}
</script>

<style lang="stylus" scoped>
  .list
    height 2500px
</style>
