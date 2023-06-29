<template>
	<view class="content">
		<u-navbar height="50" placeholder bgColor="#4989ff">
			<view slot="left" style="color: white;">{{ userSite }}</view>
		</u-navbar>
		<view style="width: 100%; background-color: #4987ff; margin-top: -2px; border-radius:0 0 60rpx 60rpx;  ">
			<u-cell-group>
				<u-cell rightIconStyle="color:white" @click='rightClick'>
					<view slot="title">
						<view class="userInfo">
							<view
								style="height: 190rpx; display: flex; flex-direction: column; justify-content: center;">
								<u-avatar :src="userAvater" size="80"></u-avatar>
							</view>
							<view
								style="height: 190rpx;display: flex;  flex-direction: column; justify-content: space-evenly; margin-left: 20rpx; ">
								<view style="display: flex;">
									<view style="font-size: 40rpx;margin-right: 10rpx;">张三</view>
									<view
										style="text-align: center; background-color: #7aafff;width: 100rpx;height: 50rpx;line-height: 50rpx; border-radius: 30%;margin-top: 4rpx;">
										站长</view>
								</view>
								<view style="font-size: 30rpx;">ID:115213</view>
							</view>
						</view>
					</view>
					<view slot="right-icon" class="rightICON"><u-icon name="arrow-right" color="#ffffff"
							size="28"></u-icon></view>
				</u-cell>
			</u-cell-group>
		</view>
		<view class="middlePanel">
			<view style="display: flex;flex-direction: column; justify-content: center;">
				<view style="text-align: center;font-size: 25rpx;color: #888888;margin-bottom: 15rpx;">2023-07</view>
				<view style="font-size: 40rpx;">8373.8元</view>
			</view>
			<view style="display: flex;flex-direction: column; justify-content: center;">
				<view style="text-align: center;font-size: 25rpx;color: #888888;margin-bottom: 15rpx;">今日</view>
				<view style="font-size: 40rpx;">278.5元</view>
			</view>
		</view>
		<view
			style=" margin-top: -20rpx; width: 95%; display: flex; justify-content: space-around; padding: 0 15rpx 0 15rpx;">
			<view class="left_youpin">
				<view class="youpinlianliang" style="display: flex;justify-content: space-between;">
					<view style="font-size: 25rpx; margin-left: 25rpx;">
						油品联量
					</view>
					<view style="font-size: 28rpx;color: #4987ff;line-height: 28rpx;" @click="bottomBtnG" name='youpin'>
						明细
					</view>
				</view>
				<view style="margin-top: 30rpx;">
					<view
						style="font-size:25rpx ; display: flex; justify-content: space-between; margin-top: 15rpx;padding-left: 20rpx;">
						<view style="color: #888888;">
							今日(元)
						</view>
						<view style="font-size: 30rpx;">
							175.80
						</view>
					</view>
					<view
						style="font-size:25rpx ; display: flex; justify-content: space-between; margin-top: 10rpx;padding-left: 20rpx;">
						<view style="color: #888888;">
							累计(元)
						</view>
						<view style="font-size: 30rpx;">
							6173.80
						</view>
					</view>
				</view>
			</view>
			<view class="right_ffeiyoupin">
				<view class="youpinlianliang" style="display: flex;justify-content: space-between;">
					<view style="font-size: 25rpx; margin-left: 25rpx;">
						非油品联量
					</view>
					<view style="font-size: 28rpx;color: #4987ff;line-height: 28rpx;" @click="bottomBtnG"
						name='feiyoupin'>
						明细
					</view>
				</view>
				<view style="margin-top: 30rpx;">
					<view
						style="font-size:25rpx ; display: flex; justify-content: space-between; margin-top: 15rpx;padding-left: 20rpx;">
						<view style="color: #888888;">
							今日(元)
						</view>
						<view style="font-size: 30rpx;">
							175.80
						</view>
					</view>
					<view
						style="font-size:25rpx ; display: flex; justify-content: space-between; margin-top: 10rpx;padding-left: 20rpx;">
						<view style="color: #888888;">
							累计(元)
						</view>
						<view style="font-size: 30rpx;">
							6173.80
						</view>
					</view>
				</view>
			</view>
		</view>
		<view class="bottomBtnG">
			<u-cell-group>
				<u-cell size="large" title="工资单" icon="order" isLink iconStyle='margin-right:10rpx;'
					titleStyle='font-size:26rpx' @click='bottomBtnG' name='gongzi'></u-cell>
				<u-cell size="large" title="评比排名" icon="thumb-up" isLink iconStyle='margin-right:10rpx;'
					titleStyle='font-size:26rpx' @click='bottomBtnG' name='paiming'></u-cell>
				<u-cell size="large" title="团队成员" icon="account" isLink iconStyle='margin-right:10rpx;'
					titleStyle='font-size:26rpx' @click='bottomBtnG' name='chengyaun'></u-cell>
				<u-cell size="large" title="部门切换" icon="setting" isLink iconStyle='margin-right:10rpx;'
					titleStyle='font-size:26rpx' @click='bottomBtnG' name='bumen'></u-cell>
			</u-cell-group>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello',
				userSite: '万州加油站',
				userAvater: require('../../static/logo.png')
			};
		},
		onLoad() {},
		methods: {
			rightClick() {
				console.log('右侧点击');
			},
			bottomBtnG(e) {
				console.log(e, '点困了');
			}
		}
	};
</script>

<style scoped lang="scss">
	.bottomBtnG {
		position: relative;
		// top: 850rpx;
		top: 20rpx;
		left: 50%;
		transform: translateX(-50%);
		background-color: #fff;
		width: 90%;
		border-radius: 20rpx;
	}

	.youpinlianliang::before {
		content: '';
		width: 7rpx;
		height: 30rpx;
		background-color: #1879ff;
		position: absolute;
	}

	.left_youpin {
		width: 40%;
		height: 140rpx;
		border-radius: 20rpx;
		background-color: #fff;
		padding: 30rpx 20rpx;
	}

	.right_ffeiyoupin {
		width: 40%;
		height: 140rpx;
		border-radius: 20rpx;
		background-color: #fff;
		padding: 30rpx 20rpx;
	}

	/deep/.rightICON .uicon-arrow-right.u-icon__icon {
		top: -45rpx !important;
	}

	.middlePanel {
		position: relative;
		top: -50rpx;
		left: 50%;
		transform: translateX(-50%);
		display: flex;
		justify-content: space-evenly;
		background-color: #fff;
		width: 90%;
		height: 190rpx;
		border-radius: 20rpx;

	}

	.userInfo {
		display: flex;
		height: 290rpx;
		color: #fff;
	}

	.content {
		position: relative;
		background-color: #f4f4f4;
		height: 100vh;
	}
</style>