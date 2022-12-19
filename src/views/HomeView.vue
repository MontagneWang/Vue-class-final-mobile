<template>
	<div class="home">
		路由已切换至 home index
		<hr />
		<myheader/>
		<index msg="Welcome to Your Vue.js App"/>
		<backtop/>
	</div>
</template>

<script>
import myheader from "@/components/myheader";
import index from '@/components/index'
import backtop from "@/components/backtop";
import tabbar from "@/components/tabbar";

export default {
	name: 'HomeView',
	components: {myheader, index, backtop, tabbar},
}
</script>
