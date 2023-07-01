<template>
	<view class="content">
		<u-navbar height="50" placeholder bgColor="#4989ff" left-text="团队成员" left-text-color='#fff' autoBack
			leftIconColor='#fff'>
		</u-navbar>
		<scroll-view scroll-y style="height: 90vh;padding-left: 40rpx;padding-right: 40rpx;"
			@scrolltolower='scrolltolower' show-scrollbar>
			<view style="display: flex;height: 180rpx;border-bottom: 1px solid #ccc;" v-for="item in list " :key="item">
				<view style="margin-right: 40rpx;margin-top: 30rpx;">
					<u-avatar :src="userAvater" shape="square" size='60'></u-avatar>
				</view>
				<view style="display: flex; flex-direction: column; justify-content: center;">
					<view style="margin-bottom: 5rpx;font-size: 35rpx;">
						{{username}}
					</view>
					<view style="color: #8d8d8d;">
						{{usertel}}
					</view>
				</view>
			</view>

		</scroll-view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				userAvater: '123',
				// userAvater: require('../../static/logo.png'),
				username: '张三',
				usertel: '13838916593',
				list: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14]
			};
		},
		methods: {
			scrolltolower() {
				console.log('滚动到底部');
			},
			clickSelect(e) {
				console.log(e, "e===========");
			},
			refre() {
				console.log('被下拉');
			}
		},

	}
</script>

<style lang="scss" scoped>
	.-webkit-scrollbar {
		color: red;
	}

	.list-cell {
		display: flex;
		box-sizing: border-box;
		width: 100%;
		padding: 10px 24rpx;
		overflow: hidden;
		color: #323233;
		font-size: 14px;
		line-height: 24px;
		background-color: #fff;
	}

	.content {
		position: relative;
		background-color: #fff;
		height: 100vh;
	}
</style>