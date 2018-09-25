<template>
<div class="header">
	<div class="header-left">
		<span class="iconfont icon-back">&#xe624;</span>
	</div>
	<div class="header-input">
		<span class="iconfont icon-search">&#xe632;</span>
	城市/景点/游玩主题
	</div>
	<router-link to="/city">
		<div class="header-right">
			{{this.city}}
			<span class="iconfont icon-b">&#xe64a;</span>

		</div>
	</router-link>
</div>
</template>
<script>

export default{
	name:'homeHeader',
	props:{
		city:String
	}
	
}
</script>

<style lang="stylus" scoped>
	@import '~styles/varibles.styl'
	.header
		display:flex
		height:.86rem
		background-color:$bgColor
		line-height:0.86rem
		color:#fff
		.header-left
			width:0.64rem
			float:left
			.icon-back{
				font-size:0.4rem
				text-align:center
			}
		.header-input
			flex:1
			margin-top:0.12rem
			height:0.64rem
			margin-left:0.2rem;
			background-color:#fff
			border-radius:0.1rem
			color:#ccc
			line-height:0.64rem
			.icon-search{
				margin-left:0.1rem
			}
		.header-right
			width:1.24rem
			float:right
			text-align:center
			line-height:0.86rem
			color:#fff
			.icon-b{
				font-size:0.24rem
			}
			
</style>