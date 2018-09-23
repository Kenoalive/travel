<template>
	<div class="wrapper">
		<swiper :options="swiperOption" >
			<!-- slides -->
			<swiper-slide v-for="item of swiperList" :key="item.id">
				<img class="swiper-img" :src="item.imgUrl" alt="">
			</swiper-slide>
			
			<!-- Optional controls -->
			<div class="swiper-pagination"  slot="pagination"></div>
		</swiper>
	</div>
</template>


<script>
	export default{
		name:'HomeSwiper',
		data:function(){
			return{
				swiperOption:{
					pagination: '.swiper-pagination',
					loop:true
				},
				swiperList:[{
					id:'001',
					imgUrl:'https://imgs.qunarzz.com/p/p60/1809/f4/d19e9608d2d1a002.jpg_256x160_539f2e86.jpg'
				},{
					id:'002',
					imgUrl:'https://imgs.qunarzz.com/p/p70/1809/e7/4941057a6aae702.jpg_256x160_9fee6ccb.jpg'
				},{
					id:'003',
					imgUrl:'https://imgs.qunarzz.com/p/p29/201302/28/3d20251a1b60350a93835fbb.jpg_256x160_e8f468b0.jpg'
				}]
			}
		}
	}

</script>

<style lang="stylus" scoped>
.wrapper >>> .swiper-pagination-bullet-active  
	background-color:#fff !important
	// 三个箭头表示穿透
.wrapper
	overflow:hidden
	width:100%
	height:0
	padding-bottom:62.5%
	
	.swiper-img
		width:100%

</style>