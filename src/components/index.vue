<template>
	<div class="index">
		<myswiper/>
		<flex/>
		<count/>
	</div>
</template>

<script>
import myswiper from "@/components/myswiper";
import flex from "@/components/flex";
import count from "@/components/count";

export default {
	name: 'index',
	components:{myswiper,flex,count}
}
</script>

<style scoped lang="less">

</style>
