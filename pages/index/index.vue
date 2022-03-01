<template>
	<view class="container">
		<uni-list>
			<uni-list-item v-for="(item,index) in Data" :key="index" :title="item.title" note="Dcloud 128评论 21 赞">
				       <template v-slot:header>
				            <view class="uni-thumb">
								<image class="uni-media-list-logo" :src="item.author_avatar" style="width: 120upx;height: 120upx;margin-right: 20upx;"></image>
								</view>
				        </template>
			</uni-list-item>
		</uni-list>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				Data: [],
			}
		},
		onLoad() {
			uni.showLoading({
							title:"加载中...."
						})
			var requestTask = uni.request({
				url: 'https://unidemo.dcloud.net.cn/api/news',
				method: 'GET',
				data: {},
				success: res => {
					this.Data = res.data;
					uni.hideLoading();
				},
				fail: () => {},
				complete: () => {}
			});
			// requestTask.abort()   可终止请求任务
		},
		methods: {

		}
	}
</script>

<style>
	.container {
		padding: 20px;
		font-size: 14px;
		line-height: 24px;
	}
</style>
