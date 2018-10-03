<template>
  <div class="list" ref="wrapper">
    <div>
      <div class="area">
        <div class="title">当前城市</div>
        <div class="button-list">
          <div class="button-wrapper" >
            <div class="button">{{this.currentCity}}</div>
          </div>
          
        </div>
      </div>
      <div class="area">
        <div class="title">热门城市</div>
        <div class="button-list">

          <div class="button-wrapper" v-for='item of hotCities' :key="item.id" 
          @click='handleCityClick(item.name)'
          >
            <div class="button">{{item.name}}</div>
          </div>
        </div>
      </div>
      <div class="area" v-for="(item,key) of cities" :key='key' :ref='key'> 
        <!-- 对象也可以循环 用键值来当index-->
        <div class="title">{{key}}</div>
        <!-- 取出item继续循环 内部item是数组-->
        <div class="item-list" v-for="innerItem of item" :key="innerItem.id" @click="handleCityClick(innerItem.name)">
          <div class="item">{{innerItem.name}}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import BScroll from 'better-scroll'
import {mapState} from 'vuex'
export default {
  name: 'CityList',
  props:{
    hotCities:Array,
    cities:Object,
    letter:String
  },
  computed:{
    ...mapState({
      currentCity:'city'
    })
  },
  methods:{
    handleCityClick (city) {
      this.$store.commit('changeCity',city)
      this.$router.push('/')
    }

  },
  mounted () {
    this.scroll = new BScroll(this.$refs.wrapper,{
      click:true
    })
  },
  watch: {  
    letter () {
      // this.$refs[this.letter]得到的是数组
      // this.$refs[this.letter][0]得到的是对象
      const element = this.$refs[this.letter][0]
      this.scroll.scrollToElement(element)

    }
  }
}
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl'
.list
  position: absolute
  top:1.63rem
  left:0
  right:0
  bottom:0
  overflow:hidden
  .title
    line-height: .54rem
    background: #eee
    padding-left: .2rem
    color: #666
    font-size: .26rem
  .button-list
    overflow: hidden
    padding: .1rem .6rem .1rem .1rem
    .button-wrapper
      float: left
      width: 33.33%
      .button
        margin: .1rem
        padding: .1rem 0
        text-align: center
        border: .02rem solid #ccc
        border-radius: .06rem
  .item-list
      .item
        line-height: .76rem
        padding-left: .2rem
        border-bottom:1px solid #ccc
        
</style>
