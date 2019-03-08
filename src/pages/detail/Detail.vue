<template>
  <detail-banner
    :sightName="sightName"
    :bannerImg="bannerImg"
    :bannerImgs="gallaryImgs">
  </detail-banner>
</template>

<script>
import DetailBanner from './component/Banner'
import axios from 'axios'

export default {
  name: 'Detail',
  components: {
    DetailBanner
  },
  data () {
    return {
      sightName: '',
      bannerImg: '',
      gallaryImgs: [],
      list: []
    }
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

</style>
