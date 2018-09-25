<template>
	<div>
		<div class="recommend-title">
			热销推荐
		</div>
		<ul>
			<li class="item" v-for="item of recommendList">
				<div class="item-img-wrapper">
					<img :src="item.imgUrl" alt="" class="item-img">
				</div>
				<div class="item-info">
					<p class="item-title">{{item.title}}</p>
					<p class="item-desc">{{item.desc}}</p>
					<button class="item-button">查看详情</button>
				</div>
			</li>
		</ul>
	</div>
</template>
<script>
export default{
	name:'HomeRecommend',
	props:{
		recommendList:Array
	},
	data () {
		return{
			
		}
	}
}
</script>
<style lang="stylus" scoped> 
	.recommend-title
		line-height:.8rem
		background:#eee
		text-indent:.2rem
	.item
		overflow:hidden
		display:flex
		height:1.9rem
		.item-img
			width:1.7rem
			height:1.7rem
			padding:0.1rem
		.item-info
			flex:1
			min-width:0
			padding:0.1rem
			.item-title
				line-height:0.54rem
				font-size:0.32rem
			.item-desc
				line-height:0.4rem
				color:#ccc
			.item-button
				background:#ff9300
				padding:0 0.1rem
				margin-top:0.16rem
				padding:0 0.2rem
				border-radius:0.06rem
				color:#fff
</style>