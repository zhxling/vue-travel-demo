<template>
  <ul class="list">
    <li
      class="item"
      v-for="(item, index) of letters"
      :key="index"
      :ref="item"
      @touchstart.prevent="handleTouchStart"
      @touchmove="handleTouchMove"
      @touchend="handleTouchEnd"
      @click="handleLetterClick">
      {{item}}
    </li>
  </ul>
</template>

<script>
export default {
  name: 'CityAlphabet',
  props: {
    cities: Object
  },
  data () {
    return {
      touchStatus: false,
      startY: 0,
      alphabetHeight: 0,
      timer: null
    }
  },
  computed: {
    letters () {
      const letters = []
      for (let key in this.cities) {
        letters.push(key)
      }
      return letters
    }
  },
  updated () {
    const rect = this.$refs['A'][0].getBoundingClientRect()
    this.startY = rect.top
    this.alphabetHeight = rect.bottom - rect.top
  },
  methods: {
    handleLetterClick (e) {
      this.$emit('change', e.target.innerText)
    },
    handleTouchStart () {
      this.touchStatus = true
    },
    handleTouchMove (e) {
      if (this.touchStatus) {
        const disY = e.touches[0].clientY - this.startY
        const index = Math.floor(disY / this.alphabetHeight)
        if (index >= 0 && index < this.letters.length) {
          const letter = this.letters[index]
          this.$emit('change', letter)
        }
      }
    },
    handleTouchEnd () {
      this.touchStatus = false
    }
  }
}
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl'
.list
  display flex
  flex-direction column
  justify-content center
  position fixed
  top 1.68rem
  bottom 0
  right: 0
  z-index 3
  width .4rem
  text-align center
  .item
    line-height .4rem
    color: $bgColor
</style>
