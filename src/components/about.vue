<template>
	<div class="about">
		<div class="intro">
			<b><p>姓名：王翱&emsp;&emsp;学号：21331225</p></b>
			<br/>
			<b><p>项目说明：</p></b>
			<p>项目使用 Vue 构建，已完成包括组件化开发在内的全部要求</p>
			<p>已适配移动端设备，响应式尺寸在最小的 320 px 到最大的 768 px</p>
			<p>源码在 source 文件夹中</p>
			<p>进入该文件夹后您可以在命令行工具中执行 npm run start</p>
			<p>项目将自动在浏览器中打开</p>
			<p>（为了避免 npm 库的下载问题，请原谅我把 node_modules 也放在了源码里一并上交）</p>
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
			<b><p>下方内容是作业里的“自主设计”部分</p></b>
			<p>由于需要包含Ajax网络请求与数据获取渲染</p>
			<p>所以决定设计一个“天气预报”界面</p>
			<p>已完成包括响应式界面在内的所有需求</p>
			<p>响应式尺寸在最小的 320 px 到最大的 1980 px</p>
			<p>注：</p>
			<p>天气预报需要定位与网络，而移动端可能由于权限问题导致定位失败</p>
			<p>因此在定位失败时默认为杭州钱塘区；定位成功则修改为最新地区</p>
			<hr/>

			<nav class="topInfo">
				<Info :info="weatherInfo[0]"/>
				<Map/>
			</nav>

			<footer class="future">
				<Abbr :info="weatherInfo[1]"/>
				<Abbr :info="weatherInfo[2]"/>
				<Chart :info="chartInfo"/>
			</footer>

		</div>

	</div>
</template>

<script>
import Info from './Info'
import Map from './Map'
import Abbr from './Abbr'
import Chart from './Chart'
import {mapState} from "vuex";

export default {
	name: "about",
	components: {Info, Map, Abbr, Chart},
	data() {
		return {
			weatherInfo: [],
			chartInfo: [],
		}
	},
	computed: {
		...mapState(['geoLocation']),
	},
	watch: {
		geoLocation: {
			handler() {
				this.send()
			}
		}
	},
	methods: {
		send() {
			this.$axios.get(`https://devapi.qweather.com/v7/weather/3d?location=${this.geoLocation}&key=2175cc3e56c3447bb9476001f1513df0`)
					.then(({data: {daily: weatherInfo}}) => {
						this.weatherInfo = weatherInfo
						this.chartInfo = [weatherInfo[0].tempMax, weatherInfo[1].tempMax, weatherInfo[2].tempMax, weatherInfo[0].tempMin, weatherInfo[1].tempMin, weatherInfo[2].tempMin]
					})
					.catch((err) => {
						console.log("请求失败，Api 接口请求次数已达今日上限")
						console.dir(err)
					})
		}
	},
	mounted() {
		console.log("地图接口使用 [高德] ，天气接口使用 [和风天气] 。\n" +
				"您可以点击 [🔄更新天气] 按钮获取最新数据，也可以点击右下角的 [🌓] 按钮进行模式切换。")
		this.send()
	},
}
</script>

<style lang="less">
.about {
	margin-top: 12%;

	b{
		font-size: 16px;
	}
	.intro {
		text-align: left;
		margin: 5% 7%;
	}
}

@media screen and (max-width: 720px) {
	.map {
		display: none;
	}

	.topInfo {
		margin-top: 10%;
	}

	.mainInfo {
		width: 100% !important;
	}

	#weatherIcon span {
		font-size: 1em;
	}

	#location {
		width: 60% !important;
	}
}

@media screen and (max-width: 900px) {
	#currentTime, #tomorrow, #twoDays {
		display: none;
	}

	#weatherIcon span {
		font-size: .8em;
	}

	#chart {
		margin: 0 !important;
		width: 100% !important;
	}
}

@media screen and (max-width: 1200px) {
	#feelLike {
		display: none;
	}
}

.border {
	border-radius: 25px;
	border: 1px #66ccff solid;
	overflow: hidden;
	box-shadow: 7px 7px 7px #ccc;
}


.topInfo {
	display: flex;
	justify-content: space-between;
	margin: 2.5% 3%;
}

.future {
	display: flex;
	margin: -1% 3%;
	width: 94%;
	height: 200px;
	text-align: center;
	vertical-align: center;
	line-height: 40px;
}
</style>
