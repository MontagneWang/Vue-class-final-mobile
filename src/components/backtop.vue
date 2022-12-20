<template>
	<button class="backtop-layout" :class="classname" :disabled="!classname" @click="backtop">
		<span>顶</span>
	</button>
</template>

<script>
// import Ling from './vc'
export default {
	name: "backtop",
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
		},
		backtop() {
			let top = document.documentElement.scrollTop || document.body.scrollTop
			// 实现滚动效果
			let set = 1
			const timeTop = setInterval(() => {
				document.body.scrollTop = document.documentElement.scrollTop = top -= set
				set += 2
				if (top <= 0) {
					clearInterval(timeTop)
				}
			}, 10)
		},
	},
	// 滚动重置
	beforeDestroy() {
		window.removeEventListener('scroll', this.handleScroll)
	}
}
</script>

<style lang="less" scoped>
.backtop-layout {
	position: fixed;
	width: 10vw;
	height: 10vw;
	right: 3vw;
	bottom: 9vh;
	z-index: 2;
	opacity: 0;
	background-color: rgba(102, 204, 255, 0.7);
	-webkit-border-radius: 100%;
	transition: all 0.7s !important;
}

.active {
	transition: all 0.7s !important;
	opacity: 1;
}
</style>
