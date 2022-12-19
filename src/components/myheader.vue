<template>
	<div>
		<!--	  页面向下滚动后出现透明绿色背景条-->
		这里是 header 组件
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
	data() {
		return {};
	},
	computed: {},
	watch: {},
	methods: {},
	mounted() {
	},       // 挂载完成 DOM可访问 模板已渲染
	beforeUpdate() {
	},  // 数据已更新但模板未更新
	updated() {
	},       // 数据 + 模板已更新
	beforeDestroy() {
	}, // 销毁之前
	activated() {
	},     // 如有 keep-alive 缓存功能，此函数会触发
}
</script>

<style lang="less" scoped>

</style>
