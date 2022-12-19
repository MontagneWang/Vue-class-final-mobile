<template>
	<div class="backtop-layout">
		<!--返回顶部-->
<!--		这里是 backtop 组件-->
	</div>
</template>

<script>
// import Ling from './vc'
export default {
	name: "backtop",
	components: {
		// Ling,
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
.backtop-layout {
	position: fixed;
	right: 10px;
	bottom: 60px;
	z-index: 1100;
	background-color: red;
}
</style>
