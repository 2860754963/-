<template>
	<view>
		<view class="">
			<u-navbar height="50" placeholder bgColor="#4989ff" left-text="月度考核" left-text-color='#fff' autoBack
				leftIconColor='#fff'>
			</u-navbar>
		</view>
		<view class="content">
			<view class="topbgc">
				<view class="leftcir">
				</view>
				<view class="rightcir">
				</view>
			</view>
			<view class="toppannel">
				<view class="panneltop">
					<view class="" style="display: inline-block;">
						考核月份：
					</view>
					<view class="" style="display: inline-block;float: right;">
						<!-- 月份选择器  默认显示上个月信息-->
						<view class="">
							<monthpicker @monthchange='monthchange'></monthpicker>
						</view>
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
					<view class="" style="display: inline-block;">
						考核项循环
					</view>
					<view class="" style="display: inline-block;float: right;">
						1950
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import monthpicker from 'components/month-picker.vue'
	export default {
		components: {
			monthpicker
		},
		data() {
			return {
				list: [0, 1, 2, 3, 4, 5]
			};
		},
		methods: {
			monthchange(month) {
				console.log('月份改变重新请求', month);
			}
		},
	}
</script>

<style lang="scss" scoped>
	.bottomcontent {
		padding-top: 130rpx;
		// background-color: bisque;
		padding-left: 65rpx;
		padding-right: 65rpx;

		.contentitem {
			font-size: 25rpx;
			height: 80rpx;
			line-height: 80rpx;
			border-bottom: 1px solid #ccc;
			padding-right: 70rpx;
			padding-left: 60rpx;
		}
	}

	.panneltop {
		font-size: 20rpx;
		height: 60rpx;
		background-color: #fff;
		line-height: 60rpx;
		box-sizing: border-box;
		padding: 0 40rpx;
		border-bottom: 1px dashed #ccc;
		border-radius: 14rpx 14rpx 0 0;
	}

	.toppannel {
		position: absolute;
		top: 40rpx;
		left: 50%;
		transform: translateX(-50%);
		height: 230rpx;
		background-color: #fff;
		width: 80%;
		box-shadow: 2rpx 2rpx 2rpx 2rpx rgba(0, 0, 0, 0.2);
		border-radius: 14rpx;
	}

	.content {
		position: relative;
	}

	.topbgc {
		height: 160rpx;
		background-color: #f4f4f4;
		position: relative;

		.leftcir {
			top: 80rpx;
			left: 60rpx;
			z-index: 9999;
			position: absolute;
			height: 30rpx;
			width: 30rpx;
			background-color: #f4f4f4;
			border-radius: 50%;

		}

		.rightcir {
			top: 80rpx;
			right: 60rpx;
			z-index: 9999;
			position: absolute;
			height: 30rpx;
			width: 30rpx;
			background-color: #f4f4f4;
			border-radius: 50%;
		}
	}
</style>