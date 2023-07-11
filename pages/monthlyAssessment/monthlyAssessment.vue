<template>
	<view>
		<view class="">
			<u-navbar height="50" placeholder bgColor="#4989ff" left-text="月度考核" left-text-color='#fff' autoBack
				leftIconColor='#fff'>
			</u-navbar>
		</view>
		<view class="content">
			<view class="topbgc">
			</view>
			<view class="toppannel">
				<view class="panneltop">
					<view class="" style="display: inline-block;">
						考核月份：
					</view>
					<view class="" style="display: inline-block;float: right;">
						月份选择器
					</view>
				</view>
				<view class=""
					style="display: flex;flex-direction: column;justify-content: space-evenly;height: 190rpx;text-align: center;">
					<view class="" style="font-size: 25rpx;height: 20rpx;">
						月度考核薪酬
					</view>
					<view class="" style="margin-bottom: 20rpx;font-size: 40rpx;">
						603.5元
					</view>
				</view>
			</view>
			<view class="bottomcontent">
				<view class="contentitem" v-for="(item,index) in list " :key="index">
					考核项循环
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list: [0, 1, 2, 3, 4, 5]
			};
		}
	}
</script>

<style lang="scss" scoped>
	.bottomcontent {
		padding-top: 120rpx;
		background-color: bisque;
		padding-left: 65rpx;
		padding-right: 65rpx;

		.contentitem {
			height: 80rpx;
			line-height: 80rpx;
			border-bottom: 1px solid #ccc;
		}
	}

	.panneltop {
		font-size: 20rpx;
		height: 60rpx;
		background-color: aquamarine;
		line-height: 60rpx;
		box-sizing: border-box;
		padding: 0 40rpx;
		border-bottom: 2px dashed #ccc;
		border-radius: 14rpx 14rpx 0 0;
	}

	.toppannel {
		position: absolute;
		top: 40rpx;
		left: 50%;
		transform: translateX(-50%);
		height: 230rpx;
		background-color: pink;
		width: 80%;
		box-shadow: 2rpx 2rpx 2rpx 2rpx rgba(0, 0, 0, 0.2);
		border-radius: 14rpx;
	}

	.content {
		position: relative;
	}

	.topbgc {
		height: 160rpx;
		background-color: #ccc;
	}
</style>