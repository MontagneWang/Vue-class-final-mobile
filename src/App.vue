<template>
	<div id="app">
		<tabbar/>
	</div>
</template>

<style lang="less">


#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
}

body {
	max-width: 768px;
	margin: 0 auto;
	padding-bottom: 60px;
}

</style>
<script>
import Tabbar from "@/components/tabbar";

export default {
	components: {Tabbar}
}
</script>