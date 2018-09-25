<template>
	<div>
		<home-header :city="city"></home-header>
		<home-swiper :list="swiperList"></home-swiper>
		<home-icons :iconList="iconList"></home-icons>
	</div>
</template>
<script>

	import HomeHeader from './components/Header.vue'
	import HomeSwiper from './components/Swiper.vue'
	import HomeIcons from './components/icons.vue'
	import axios from 'axios'

	export default{
		name:'home',
		components:{
		 	HomeHeader:HomeHeader,
			HomeSwiper:HomeSwiper,
			HomeIcons:HomeIcons
		},
		data () {
			return {
				city:'',
				swiperList:[],
				iconList:[]
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