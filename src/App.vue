<template>
	<div id="app">
		<keep-alive>
			<!-- 把路由放到内存之中，重新渲染的时候不需要重新加载这个组件 -->
			<router-view/>
		</keep-alive>
	</div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>

</style>
