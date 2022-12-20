<template>
	<div class="home">
		<myheader/>
		<index/>
		<backtop/>
	</div>
</template>

<script>
import myheader from "@/components/myheader";
import myswiper from "@/components/myswiper";
import index from '@/components/index'
import backtop from "@/components/backtop";
import tabbar from "@/components/tabbar";

export default {
	name: 'HomeView',
	components: {myheader, index, backtop, tabbar, myswiper},

}
</script>

<style lang="less">

</style>
