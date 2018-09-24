<template>
	<div>
		<home-header></home-header>
		<home-swiper></home-swiper>
		<home-icons></home-icons>
	</div>
</template>
<script>

	import HomeHeader from './components/Header.vue'
	import HomeSwiper from './components/Swiper.vue'
	import HomeIcons from './components/icons.vue'
	export default{
		name:'home',
		components:{
			HomeHeader:HomeHeader,
			HomeSwiper:HomeSwiper,
			HomeIcons:HomeIcons
		}
	}
</script>

<style>

</style>