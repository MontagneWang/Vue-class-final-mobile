<template>
	<aside class="map border">
		<div id='container'></div>
	</aside>
</template>

<script>
import AMapLoader from '@amap/amap-jsapi-loader';
import {mapMutations} from "vuex";

export default {
	name: "Map",
	methods: {
		...mapMutations(['CHANGE']),
		initMap() {
			AMapLoader.load({
				key: "0f680fc17ef03445c8e5548cc28a7225",             // 申请好的Web端开发者Key，首次调用 load 时必填
				version: "2.0",      // 指定要加载的 JSAPI 的版本，缺省时默认为 1.4.15
				plugins: ['AMap.Geolocation'],       // 需要使用的的插件列表，如比例尺'AMap.Scale'等
			}).then((AMap) => {
				// this.map = new AMap.Map("container", {  //设置地图容器id
				//   viewMode: "3D",    //是否为3D地图模式
				//   zoom: 15,           //初始化地图级别
				//   center: [120, 28], //初始化地图中心点位置
				// });

				// 创建小点标记
				// let marker = new AMap.Marker({
				//   position: [120.699242, 27.99375] // 基点坐标
				// });
				// // 地图添加标记
				// this.map.add(marker);

				let map = new AMap.Map('container', {
					resizeEnable: true
				})
				AMap.plugin('AMap.Geolocation',  ()=> {
					let geolocation = new AMap.Geolocation({
						enableHighAccuracy: true,// 高精度定位
						timeout: 10000,          // 超过10秒后停止定位
						buttonPosition: 'RB',    // 按钮停靠位置
						buttonOffset: new AMap.Pixel(10, 20),
						zoomToAccuracy: true,    // 定位成功后调整地图视野
					})
					map.addControl(geolocation)
					geolocation.getCurrentPosition( (status, geoResult)=> {
						// 通过 computed 将 state 中要监视的数据取出来，然后通过 watch监视属性监视其变化
						this.$store.commit('CHANGE',[geoResult.position.lng,geoResult.position.lat])
					})
				})
			}).catch(e => {
				console.log(e);
			})
		},
	},
	//DOM初始化完成进行地图初始化
	mounted() {
		this.initMap();

	},
}
</script>

<style lang="less">
.map {
	width: 40%;
}

#container {
	height: 100%;

	a, div.amap-copyright {
		display: none !important;
	}
}

</style>
