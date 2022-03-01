<template>
	<view>
		<view class="page-section page-section-gap">
		<map :latitude="latitude" :longitude="longitude" style="width: 100%;height: 600upx;"></map>
						</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				latitude: 39.7,
				longitude: 116.7,
			}
		},
		onLoad() {
			//谷歌浏览器获取位置会有延迟  20几秒执行一次   但是edge浏览器可以直接获取到
			//腾旭地图服务   https://lbs.qq.com/dev/console/application/mine   1104497887@qq.com    
			uni.getLocation({
				type: 'gcj02',
				success: res => {
					console.log(12345)
					console.log(res)
					this.latitude = res.latitude
					this.longitude = res.longitude
				},
				fail: () => {
					console.log(44444)
					uni.showToast({
										    title: '获取地址失败，将导致部分功能不可用',
											icon:'none'
										});
				},
				complete: () => {
					console.log(5555)
				}
			});
		},
		methods: {
			
		}
	}
</script>

<style>

</style>
