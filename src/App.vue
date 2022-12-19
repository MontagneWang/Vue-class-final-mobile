<template>
	<div id="app">
		<tabbar/>
	</div>
</template>

<style lang="less">

#app {
	text-align: center;
	max-width: 768px;
	min-width: 320px;
	margin: 0 auto;
	padding-bottom: 6.8vh;
	overflow: hidden;
	background-color: #f5f5f5;
	height: 100vh;
	overflow-y: scroll;
}
</style>
<script>
import Tabbar from "@/components/tabbar";

export default {
	components: {Tabbar}
}
</script>