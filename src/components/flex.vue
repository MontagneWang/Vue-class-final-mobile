<template>
	<div class="flex">
		<ul>
			<li class="insideBox" v-for="item in items">
				<a href="#">
					<img :src="item.url" width="100%" alt="">
					<span>{{ item.text }}</span>
				</a>
			</li>
		</ul>
	</div>
</template>

<script>
// import Ling from './vc'
export default {
	name: "flex",
	data() {
		return {
			items: []
		}
	},
	mounted() {
		this.$axios.get('https://www.imooc.com/api/mall-wepApp/index/nav')
				.then(({data: {data}}) => {
					for (let i = 0; i < data.length; i++) {
						this.items.push({url: data[i]['url'], text: data[i]['text']})
					}
				})
				.catch(err => {
					console.dir(err)
				})
	}
}
</script>

<style lang="less" scoped>
@media screen and (max-width: 370px) {
	#app > div > div > div.index > div.flex > ul  a > span{
		display: none;
	}
}
@media screen and (min-width: 425px) {
	#app > div > div > div.index > div.flex > ul  a > span{
		font-size: 14px;
	}
}
@media screen and (min-width: 525px) {
	#app > div > div > div.index > div.flex > ul  a > span{
		font-size: 16px;
	}
}
@media screen and (min-width: 625px) {
	#app > div > div > div.index > div.flex > ul  a > span{
		font-size: 20px;
	}
}

.flex {
	width: 100%;
	background: #fff;
	padding: 2% 2% 4% 2%;
	display: flex;
	justify-content: space-around;
	flex-wrap: wrap;

	.insideBox {
		font-size: 12px;
		display: inline-block;
		width: 11.7%;
		height: 9.5vh;
		margin: 4.9% 6%;

		span {
			display: inline-block;
			margin-top: 2vh;
			zoom: 0.85;
		}
	}
}
</style>
