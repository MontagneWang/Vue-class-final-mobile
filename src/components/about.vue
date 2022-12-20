<template>
	<div class="about">
		<div class="intro">
			<p>姓名：王翱&emsp;&emsp;学号：21331225&emsp;&emsp;专业：数字媒体技术</p>
			<br/>
			<p>项目说明：</p>
			<p>项目使用 Vue 构建，已完成包括组件化开发在内的全部要求</p>
			<p>源码在 source 文件夹中</p>
			<p>进入该文件夹后您可以在命令行工具中执行 npm run start</p>
			<p>项目将自动在浏览器中打开</p>
			<br/>
			<p>打包好的文件在 dist 文件夹中</p>
			<p>由于 Vue 打包后的文件需要放在服务器上运行</p>
			<p>您也可以通过网页链接进行访问查看（前八位是我的学号）</p>
			<p>网址：
				<a href="https://21331225.frontend.montagnewang.com" target="_blank">
					21331225.frontend.montagnewang.com
				</a>
			</p>
			<br/>
			<p>下方内容是作业里的“自主设计”部分</p>
			<p>由于需要包含Ajax网络请求与数据获取渲染</p>
			<p>所以决定设计一个“天气预报”界面</p>
			<p>已完成包括响应式界面在内的所有需求</p>
			<hr />
		</div>


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
}
</script>

<style lang="less" scoped>
.about {
	margin-top: 12%;

	.intro {
		text-align: left;
		margin: 5% 7%;
	}
}
</style>
