<template>
	<view class="content">
		<u-navbar height="50" placeholder bgColor="#4989ff">
			<view slot="left" style="color: white;">{{ userSite }}</view>
		</u-navbar>
		<view class="topinfo">
			<u-cell-group>
				<u-cell rightIconStyle="color:white" @click='topage' name='/pages/userinfo/userinfo'>
					<view slot="title">
						<view class="userInfo">
							<view class="useravater">
								<u-avatar :src="userAvater" size="80"></u-avatar>
							</view>
							<view class="username">
								<view style="display: flex;">
									<view style="font-size: 40rpx;margin-right: 10rpx;">张三</view>
									<view class="userpost">
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
			<view class="panelitem">
				<view class="itemtitle">2023-07</view>
				<view style="font-size: 40rpx;">8373.8元</view>
			</view>
			<view class="panelitem">
				<view class="itemtitle">今日</view>
				<view style="font-size: 40rpx;">278.5元</view>
			</view>
		</view>
		<view class="middleoil">
			<view class="left_youpin">
				<view class="youpinlianliang" style="display: flex;justify-content: space-between;">
					<view style="font-size: 25rpx; margin-left: 25rpx;">
						油品联量
					</view>
					<view style="font-size: 28rpx;color: #4987ff;line-height: 28rpx;" @click="topageDetail"
						data-name='/pages/oilDetails/oilDetails'>
						明细
					</view>
				</view>
				<view style="margin-top: 30rpx;">
					<view class="oiltitle">
						<view style="color: #888888;">
							今日(元)
						</view>
						<view style="font-size: 30rpx;">
							175.80
						</view>
					</view>
					<view class="oiltitle">
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
					<view style="font-size: 28rpx;color: #4987ff;line-height: 28rpx;" @click="topageDetail"
						data-name='/pages/noOilDetails/noOilDetails'>
						明细
					</view>
				</view>
				<view style="margin-top: 30rpx;">
					<view class="oiltitle">
						<view style="color: #888888;">
							今日(元)
						</view>
						<view style="font-size: 30rpx;">
							175.80
						</view>
					</view>
					<view class="oiltitle">
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
					titleStyle='font-size:26rpx' @click='topage' name='/pages/Payroll/Payroll'></u-cell>
				<u-cell size="large" title="评比排名" icon="thumb-up" isLink iconStyle='margin-right:10rpx;'
					titleStyle='font-size:26rpx' @click='topage' name='/pages/rank/rank'></u-cell>
				<u-cell size="large" title="招聘信息" icon="chat" isLink iconStyle='margin-right:10rpx;'
					titleStyle='font-size:26rpx' @click='topage'
					name='/pages/recruitmentInformation/recruitmentInformation'></u-cell>
				<u-cell size="large" title="团队成员" icon="account" isLink iconStyle='margin-right:10rpx;'
					titleStyle='font-size:26rpx' @click='topage' name='/pages/teamMembers/teamMembers'></u-cell>
				<u-cell class="lastchildcell" size="large" title="部门切换" icon="setting" isLink
					iconStyle='margin-right:10rpx;' titleStyle='font-size:26rpx' @click='topage'
					name='/pages/depSwitch/depSwitch'></u-cell>
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
				// userAvater: require('../../static/logo.png')
				userAvater: '123'

			};
		},
		onLoad() {},
		methods: {
			topageDetail(e) {
				uni.navigateTo({
					url: e.currentTarget.dataset.name
				})
			},
			topage(e) {
				uni.navigateTo({
					url: e.name
				})
			}
		}
	};
</script>

<style lang="scss" scoped>
	.content .topinfo /deep/.u-cell-group .u-cell-group__wrapper .u-line {
		display: none !important;
		// background-color: pink !important;
	}



	.bottomBtnG /deep/.u-cell-group .u-cell-group__wrapper .u-line:first-child {
		display: none !important;
		// background-color: pink !important;
	}

	.bottomBtnG /deep/.u-cell-group .u-cell-group__wrapper .u-cell:last-child .u-line {
		display: none !important;
		// background-color: pink;
	}

	.u-cell__bd {
		border: none;
	}

	.u-cell__ft {
		border: none;
	}

	.topinfo {
		width: 100%;
		background-color: #4987ff;
		margin-top: -2px;
		border-radius: 0 0 60rpx 60rpx;
	}

	.bottomBtnG {
		position: relative;
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
		top: -72rpx;
		left: 50%;
		transform: translateX(-50%);
		display: flex;
		justify-content: space-evenly;
		background-color: #fff;
		width: 90%;
		height: 190rpx;
		border-radius: 20rpx;

		.panelitem {
			display: flex;
			flex-direction: column;
			justify-content: center;

			.itemtitle {
				text-align: center;
				font-size: 25rpx;
				color: #888888;
				margin-bottom: 15rpx;
			}
		}

	}

	.oiltitle {
		font-size: 25rpx;
		display: flex;
		justify-content: space-between;
		margin-top: 15rpx;
		padding-left: 20rpx;
	}

	.middleoil {
		margin-top: -45rpx;
		width: 95%;
		display: flex;
		justify-content: space-around;
		padding: 0 15rpx 0 15rpx;
	}

	.userInfo {
		display: flex;
		height: 290rpx;
		color: #fff;

		.useravater {
			height: 190rpx;
			display: flex;
			flex-direction: column;
			justify-content: center;
		}

		.username {
			height: 190rpx;
			display: flex;
			flex-direction: column;
			justify-content: space-evenly;
			margin-left: 20rpx;

			.userpost {
				text-align: center;
				background-color: #7aafff;
				width: 100rpx;
				height: 50rpx;
				line-height: 50rpx;
				border-radius: 30%;
				margin-top: 4rpx;
			}
		}
	}

	.content {
		position: relative;
		background-color: #f4f4f4;
		height: 100vh;
	}
</style>