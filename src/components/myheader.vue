<template>
	<div class="myheader" :class="classname">
		<!--	  页面向下滚动后出现透明绿色背景条-->
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
		return {
			classname: ''
		}
	},
	// 滚动监听
	mounted() {
		window.addEventListener('scroll', this.throttle(this.handleScroll, 200)) // 监听页面滚动
	},
	methods: {
		/**
		 * 节流函数
		 * @param method 事件触发的操作
		 * @param mustRunDelay 间隔多少毫秒需要触发一次事件
		 */
		throttle(method, mustRunDelay) {
			let timer,
					args = arguments,
					start;
			return function loop() {
				let self = this;
				let now = Date.now();
				if (!start) {
					start = now;
				}
				if (timer) {
					clearTimeout(timer);
				}
				if (now - start >= mustRunDelay) {
					method.apply(self, args);
					start = now;
				} else {
					timer = setTimeout(function () {
						loop.apply(self, args);
					}, 50);
				}
			}
		},
		// 获取页面滚动距离
		handleScroll() {
			let scrollTop = document.body.scrollTop || document.documentElement.scrollTop;
			if (scrollTop > 300) {
				this.classname = 'active'
			} else {
				this.classname = ''
			}
		}
	},
	// 滚动重置
	beforeDestroy() {
		window.removeEventListener('scroll', this.handleScroll)
	}
}
</script>

<style lang="less" scoped>
.myheader {
	position: fixed;
	top: 0;
	left: 0;
	right: 0;
	width: 100vw;
	height: 8.6%;
	margin: 0 auto;
	background-color: rgba(0, 0, 0, 0);
	display: flex;
	justify-content: center;
	align-items: center;
	z-index: 2;
	transition: all 0.7s;
}

.active {
	transition: all 0.7s;
	background-color: rgba(164, 193, 89, 0.7);
}
</style>
