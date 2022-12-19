<template v-if="picList">
	<swiper
			class="my_swiper"
			:options="swiperOption"
			@mouseover.native="handleAuto(true)"
			@mouseleave.native="handleAuto(false)"
	>
		<swiper-slide v-for="(item,index) in picList" :key="index">
			<img :src="item.pic_src" alt="" :data-path="item.pic_src" data-yaya="图片">
		</swiper-slide>

		<div class="swiper-pagination" slot="pagination"></div>
	</swiper>
</template>

<script>
// import Ling from './vc'

export default {
	name: "myswiper",
	components: {
		// Ling,
	},
	data() {
		return {
			// 图片数据
			picList: [],
			// Swiper 配置项
			swiperOption: {
				direction: 'horizontal', // Swiper的滑动方向,可设置为水平方向切换 horizontal（默认） 或垂直方向切换 vertical
				slidesPerView: 1, // Swiper的列数
				// spaceBetween: 30, //板块间距
				// 设置分页器
				pagination: {
					el: ".swiper-pagination",
					type: 'bullets',//将分页的类型改为圆点（默认)
					clickable: true,// 点击可切换
					// hideOnClick :true, // 点击swiper-slide显隐
				},
				// 设置自动轮播
				autoplay: {
					delay: 1000, // n秒切换一次
					disableOnInteraction: false, // 用户操作swiper之后，是否禁止autoplay。默认为true：停止。
				},
				loop: false, //无缝轮播
				grabCursor: true, // 覆盖Swiper 时指针会变成手掌形状，拖动时指针会变成抓手形状
			},
		};
	},
	methods: {
		// 鼠标覆盖停止自动切换,鼠标离开开始自动切换
		handleAuto(status) {
			//如果你初始化时没有定义Swiper实例，后面也可以通过Swiper的HTML元素来获取该实例
			let mysSwiper = document.querySelector('.my_swiper').swiper;
			status ? (mysSwiper.autoplay.stop()) : (mysSwiper.autoplay.start());
		},
	},
	mounted() {
		this.$axios.get('https://www.imooc.com/api/mall-wepApp/index/slider')
				.then(({data: {data}}) => {
					for (let i = 0; i < data.length; i++) {
						this.picList.push({pic_src: data[i]['url']})
					}
				})
				.catch(err => {
					console.dir(err)
				})
	}
}
</script>

<style lang="less" scoped>
.my_swiper {
	width: 100%;
	height: 25.6%;

	.swiper-slide {
		height: 100%;
	}

	img {
		display: block;
		width: 100%;
		height: 100%;
		object-fit: cover;
		object-position: center;
	}
}
</style>
