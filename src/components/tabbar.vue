<template>
	<div class="tabbar">
		<!--底部切换路由-->
		这里是 tabbar 组件
		<router-view/>
		<nav>
			<router-link to="/">首页</router-link>
			&emsp;|&emsp;
			<router-link to="/about">我的</router-link>
		</nav>
	</div>
</template>

<script>
// import Ling from './vc'
export default {
	name: "tabbar",
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
.tabbar {
	nav {
		margin: 0 auto;
		width: 100%;
		height: 48px;
		line-height: 48px;
		position: fixed;
		bottom: 0;
		left: 0;
		background-color: #66ccff;
	}
}

nav {
	a {
		font-weight: bold;
		text-decoration:none;
		color: #2c3e50;

		&.router-link-exact-active {
			color: #42b983;
		}
	}
}
</style>
