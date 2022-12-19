<template>
	<div class="search">
		<input type="text" class="searchbar" placeholder="     搜索目的地/折扣/关键字">
	</div>
</template>

<script>
// import Ling from './vc'
export default {
	name: "searchbar",
	components: {
		// Ling,
	},
}
</script>

<style lang="less" scoped>
.search {
	width: 100%;

	input {
		outline: none;
		border: 0;
	}
	input::-webkit-input-placeholder {
		color: rgba(255,255,255,0.7);
		font-size: 12px;
		}
}

.searchbar {
	width: 89%;
	height: 5%;
	margin: 0 auto;
	background: rgba(0, 0, 0, 0.20);
	border: 0 solid rgba(0, 0, 0, 0.10);
	box-shadow: 0 5px 10px 0 rgba(0, 0, 0, 0.05);
	border-radius: 27.5px;

}
</style>
