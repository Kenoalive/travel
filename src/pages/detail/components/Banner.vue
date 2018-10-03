<template>
	<div class="banner">
		<img class="banner-img"  src="//img1.qunarzz.com/sight/p0/1606/4a/4ae2bbafcc977a54e2.water.jpg_600x330_616ff41d.jpg" alt="">
		<div class="banner-info">
			<div class="banner-tit">合肥海洋世界</div>
		</div>
	</div>
</template>
<script>
export default{
	name:'DetailBanner'
}
</script>
<style lang="stylus" scoped>
 .banner
 	position: relative
 	overflow:hidden
 	height:0
 	padding-bottom:55%
 	width:100%
 	.banner-img
 		width:100%
 	.banner-info
 		display:flex
 		position: absolute
 		left:0
 		right:0
 		bottom:0
 		line-height:0.6rem
 		color : #fff
 		.banner-tit
 			flex:1
 			font-size:0.32rem
 			padding:0 0.2rem
 			
 		

</style>