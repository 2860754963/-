<template>
	<view class="content">
		<u-navbar height="50" placeholder bgColor="#4989ff" left-text="个人信息 " left-text-color='#fff' autoBack
			leftIconColor='#fff'>
		</u-navbar>
		<view class="pannel">
			<view class="avater">
				<u-avatar :src="userAvater" size="80"></u-avatar>
				<view style="text-align: center; margin-top: 10rpx;font-size: 40rpx;">
					{{username}}
				</view>
			</view>
			<view style="padding-top: 170rpx;margin-left: 60rpx;margin-right: 60rpx;height: 780rpx;">
				<view style="font-size: 38rpx;margin-bottom: 40rpx;">
					基本信息
				</view>
				<view>
					<view v-for="(item,index) in userinfo" :key='index'
						style="border-bottom: 1px solid #ccc;height: 90rpx;line-height: 90rpx;display: flex;">
						<view style="width: 190rpx;color: #333333;">{{item.useritem}}:</view>
						<view>{{item.uservalue}}</view>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				userAvater: require('../../static/logo.png'),
				username: '张三',
				userinfo: [{
						useritem: '用户账号',
						uservalue: 'Zhangsan'
					},
					{
						useritem: '员工服务号',
						uservalue: '849282'
					},
					{
						useritem: '职务',
						uservalue: '营业员'
					},
					{
						useritem: '角色',
						uservalue: '普通员工'
					},
					{
						useritem: '所属部门',
						uservalue: '万州加油站'
					},
					{
						useritem: '手机号',
						uservalue: '18321869380'
					},
					{
						useritem: '邮箱',
						uservalue: '17719215834@cqsy.com'
					},

				]
			};
		}
	};
</script>

<style lang="less" scoped>
	.avater {
		position: absolute;
		top: -80rpx;
		left: 50%;
		transform: translateX(-50%);

	}

	.pannel {
		width: 90%;
		background-color: #fff;
		position: relative;
		top: 160rpx;
		left: 50%;
		transform: translateX(-50%);

		// padding-left: 30rpx;
		// padding-right: 30rpx;

	}

	.content {
		position: relative;
		background-color: #f4f4f4;
		height: 100vh;
	}
</style>