<template>
	<div>
		<home-header></home-header>
		<home-swiper :list="swiperList"></home-swiper>
		<home-icons :iconList="iconList"></home-icons>
		<home-recommend :recommendList="recommendList"></home-recommend>
	</div>
</template>
<script>
import axios from 'axios'
import HomeHeader from './components/Header.vue'
import HomeSwiper from './components/Swiper.vue'
import HomeIcons from './components/icons.vue'
import HomeRecommend from './components/Recommend.vue'
import { mapState } from 'vuex'
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
			swiperList:[],
			iconList:[],
			recommendList:[],
			lastCity:''
		}
	},
	computed:{
		...mapState(['city'])
	},

	methods:{
		getHomeInfo () {
			axios.get('/static/mock/index.json?city=' + this.city)
			.then(this.getHomeInfoSucc)
		},
		getHomeInfoSucc (res) {
			res = res.data
			if(res.data && res.ret){
				this.swiperList = res.data.swiperList
				this.iconList = res.data.iconList
				this.recommendList = res.data.recommendList
			}
		}
	},
	mounted () {
		this.lastCity = this.city
		this.getHomeInfo()
	},
	activated () {
		// 如果两次请求城市不相同，则重新发送ajax请求
		if(this.lastCity !== this.city){
			this.lastCity = this.city
			this.getHomeInfo()
		}
	}
}
</script>

<style>

</style> 