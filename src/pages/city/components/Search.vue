<template>
  <div>
    <div class="search">
      <input type="text" v-model="keyword" class="search-input" placeholder="输入城市名或者拼音">
    </div>
    <div class="search-content" ref="wrapper" v-show="keyword">
      <ul>
        <li v-for="item of list" class="search-item" @click="changeCity(item.name)">{{item.name}}</li>
        <li  class="search-item" v-show="!list.Length">没有找到匹配数据</li>
      </ul>
    </div>
  </div>
</template>
<script>
import BScroll from 'better-scroll'
export default{
	name:'CitySearch',
  props:{
    cities:Object
  },
  data () {
    return {
      keyword:'',
      list:[],
      timer:null
    }
  },
  mounted () {
    this.scroll = new BScroll(this.$refs.wrapper,{
      click:true
    })
  },
  methods :{
    changeCity (city) {
      this.$store.commit('changeCity',city)
      this.$router.push('/') 
      // 跳转到首页
    }
  },
  watch: {
    keyword () {
      if(this.timer){
        clearTimeout(this.timer)
      }
      if(!this.keyword){
        this.list = []
        return 
      }
      this.timer = setTimeout(() => {
        const result = []
        for(let i in this.cities){
          this.cities[i].forEach((value) => {
            if(value.name.indexOf(this.keyword)>-1 || value.spell.indexOf(this.keyword)>-1){
              result.push(value)
            }
          })
        }
        this.list = result
      },100)

      
    }
  }
}
</script>
<style lang="stylus" scoped>
 @import '~styles/varibles.styl'
 .search
    height: .72rem
    padding: 0.1rem
    background: $bgColor
  .search-input
    box-sizing: border-box
    width: 100%
    height: .56rem
    // margin-bottom:0.2rem
    padding: 0 .1rem
    line-height: .52rem
    text-align: center
    border-radius: .06rem
    color: #666
.search-content
  z-index:1
  overflow:hidden
  position:absolute
  top:1.58rem
  left:0
  right:0
  bottom:0
  background:#eee
  .search-item
    line-height:0.62rem
    padding-left:0.2rem
    color:#666
    background:#fff
	
</style>