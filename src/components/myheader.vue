<template>
	<div class="myheader">
		<!--	  页面向下滚动后出现透明绿色背景条-->
		<searchbar/>
	</div>
</template>

<script>
import searchbar from './searchbar'

export default {
	name: "myheader",
	components: {
		searchbar
	},
}
</script>

<style lang="less" scoped>
.myheader{
	position: fixed;
	top: 0;
	left: 0;
	width: 100%;
	height: 8.6%;
	margin: 0 auto;
	background-color: rgba(164, 193, 89,0.7);
	display: flex;
	justify-content: center;
	align-items: center;
	z-index: 2;
}
</style>
