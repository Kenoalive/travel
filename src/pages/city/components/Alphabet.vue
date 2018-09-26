<template>
  <ul class="list" >
    <li 
    class="item" 
    v-for='item of letters' 
    :key="item" 
    @click="handleLetterClick"
    @touchstart="handleTouchStart"
    @touchmove="handleTouchMove"
    @touchend="handleTouchEnd"
    >
      {{item}}
    </li>
  </ul>
</template>

<script>
export default {
  name: 'CityAlphabet',
  props:{
    cities:Object
  },
  computed:{
    letters () {
      const letters = []
      for (let i in this.cities) {
        letters.push(i)
      }
      return letters
    }
  },
  data () {
    return {
      touchStatus : false,
      timer:null
    }
  },
  methods:{
    handleLetterClick (e) {
      this.$emit('change', e.target.innerText)
    },
    handleTouchStart () {
      this.touchStatus = true
    },
    handleTouchMove (e) {
      if(this.touchStatus){
        const startY = 74 //A字母到父组件距离
        const touchY = e.touches[0].clientY - 79 //当前触摸位置-79 即当前字母到顶部A字母的位置
        const index = Math.floor((touchY-startY) / 20) //计算当前字母的index
        if(index >= 0 && index < this.letters.length){
          this.$emit('change', this.letters[index])// 触发change事件

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
    display: flex
    flex-direction: column
    justify-content: center
    position: absolute
    top: 1.58rem
    right: 0
    bottom: 0
    width: .4rem
    .item
      line-height: .4rem
      text-align: center
      color: $bgColor
</style>
