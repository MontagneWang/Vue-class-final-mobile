<template>
	<div class="count">
		<div>
			精选折扣
		</div>
		<ul>
			<li class="insideBox" v-for="item in items">
				<a href="#">
					<img :src="item.url" width="100%" alt="">
					<span class="title">{{ item.title }}</span>
					<span class="price">{{ item.price }}</span>
				</a>
			</li>
		</ul>
	</div>
</template>

<script>
export default {
	name: "count",
	data() {
		return {
			items: [],
		};
	},
	computed: {},
	watch: {},
	methods: {},
	mounted() {
		this.$axios.get('https://www.imooc.com/api/mall-wepApp/index/product?icode=J351519BC12ED655F')
				.then(({data: {data}}) => {
					for (let i = 0; i < data.length; i++) {
						this.items.push({url: data[i]['url'], title: data[i]['title'], price: data[i]['price']})
					}
				})
				.catch(err => {
					console.dir(err)
				})
	},
}
</script>

<style lang="less" scoped>
.count {
	width: 100%;
	background-color: #fff;
	margin-top: 1.4vh;
	padding-top: 8.4vh;
	position: relative;

	div{
		position: absolute;
		top: 2.8vh;
		left: 5.3%;
		font-family: PingFangSC-Medium;
		font-size: 16px;
		color: #191919;
		letter-spacing: 0;
	}

	ul{
		display: flex;
		justify-content: space-evenly;
		flex-wrap: wrap;
	}

	.insideBox {
		width: 42.1%;
		margin: 0;

		span.title {
			height: 40px;
			line-height: 20px;
			margin-bottom: 4px;
			color: #333;
			font-size: 14px;
			overflow: hidden;
			text-overflow: ellipsis;
			display: -webkit-box;
			-webkit-line-clamp: 2;
			-webkit-box-orient: vertical;
		}
	}
}
</style>
