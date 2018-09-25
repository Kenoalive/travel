<template>
	<div>
		<home-header :city="city"></home-header>
		<home-swiper :list="swiperList"></home-swiper>
		<home-icons :iconList="iconList"></home-icons>
		<home-recommend :recommendList="recommendList"></home-recommend>
	</div>
</template>
<script>

	import HomeHeader from './components/Header.vue'
	import HomeSwiper from './components/Swiper.vue'
	import HomeIcons from './components/icons.vue'
	import axios from 'axios'
	import HomeRecommend from './components/Recommend.vue'

	export default{
		name:'home',
		components:{
		 	HomeHeader:HomeHeader,
			HomeSwiper:HomeSwiper,
			HomeIcons:HomeIcons,
			HomeRecommend:HomeRecommend
		},
		data () {
			return {
				city:'',
				swiperList:[],
				iconList:[],
				recommendList:[]
			}
		},

		methods:{
			getHomeInfo () {
				axios.get('/static/mock/index.json')
				.then(this.getHomeInfoSucc)
			},
			getHomeInfoSucc (res) {
				res = res.data
				if(res.data && res.ret){
					this.city = res.data.city
					this.swiperList = res.data.swiperList
					this.iconList = res.data.iconList
					this.recommendList = res.data.recommendList
				}
			}
		},
		mounted () {
			this.getHomeInfo()
		}
	}
</script>

<style>

</style>