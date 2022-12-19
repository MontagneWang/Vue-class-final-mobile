<template>
	<div>
		<p>这里是 about 组件</p>
		<p>写入版权信息的说明</p>
		<p>姓名：</p>
		<p>学号：</p>
		<p>本项目使用 Vue 构建</p>
		<p>打包好的文件在 dist 文件夹中</p>
		<p>由于打包文件中的 index.html 需要放在服务器上</p>
		<p>所以您可以通过网页链接进行访问查看</p>
		<p>地址：</p>
		<p>（前八位是我的学号）</p>
	</div>
</template>

<script>
// import Ling from './vc'
export default {
	name: "about",
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

</style>
