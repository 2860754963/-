<template>
	<view>
		<view id="navbarcus">
			<u-navbar height="50" placeholder bgColor="#4989ff" left-text="详情 " left-text-color='#fff' autoBack
				leftIconColor='#fff'>
			</u-navbar>
		</view>
		<view class="content" :style="{'--navbarcusheight':navbarcusheight}">
			<view class="title" id="title">
				<view class="" style="font-size: 40rpx;">
					标题管理员
				</view>
				<view style="margin: 20rpx 0;">
					<view style="display: inline-block;margin-right: 20rpx;font-size: 25rpx;">
						万州加油站
					</view>
					<view class="tags" v-for="(item,index) in tagslist" :key="index">
						{{item}}
					</view>
				</view>
				<view class="" style="font-size: 23rpx; color: #ababab;">
					发布时间：23-07-02 10:20:10
				</view>
			</view>
			<view class="contentdatail" :style="{'--titleheight':titleheight,'--navbarcusheight':navbarcusheight}">
				<scroll-view scroll-y="true" style="height: 100%;">
					<view>
						详情
						标题设备管理员
						万州加油站
						1-3年
						设备管理员
						本科
						内容：
						万州加油站急需设备管理员2名
						1、负责每日设定期巡回检查，维护设备非专业性的一般设备故障，属于专业维修故障能做出判断，并及时报告。
						1、负责每日设定期巡回检查，维护设备非专业性的一般设备故障，属于专业维修故障能做出判断，并及时报告。
						1、负责每日设定期巡回检查，维护设备非专业性的一般设备故障，属于专业维修故障能做出判断，并及时报告。
						1、负责每日设定期巡回检查，维护设备非专业性的一般设备故障，属于专业维修故障能做出判断，并及时报告。1、负责每日设定期巡回检查，维护设备非专业性的一般设备故障，属于专业维修故障能做出判断，并及时报告。
					</view>
					<view>
						详情
						标题设备管理员
						万州加油站
						1-3年
						设备管理员
						本科
						内容：
						万州加油站急需设备管理员2名
						1、负责每日设定期巡回检查，维护设备非专业性的一般设备故障，属于专业维修故障能做出判断，并及时报告。
						1、负责每日设定期巡回检查，维护设备非专业性的一般设备故障，属于专业维修故障能做出判断，并及时报告。
						1、负责每日设定期巡回检查，维护设备非专业性的一般设备故障，属于专业维修故障能做出判断，并及时报告。
						1、负责每日设定期巡回检查，维护设备非专业性的一般设备故障，属于专业维修故障能做出判断，并及时报告。1、负责每日设定期巡回检查，维护设备非专业性的一般设备故障，属于专业维修故障能做出判断，并及时报告。
					</view>
				</scroll-view>
			</view>
			<view class="" style="margin-top: 20rpx;">
				<u-button type="primary" text="投递"></u-button>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				tagslist: ['设备管理员', '本科', '1-3年经验', '硕士', '国际奖牌', '奖金', '奖学金', '啥都要', '啥都要'],
				navbarcusheight: 0,
				titleheight: 0
			}
		},
		methods: {},
		onLoad(option) {
			const eventChannel = this.getOpenerEventChannel();
			eventChannel.on('resultItem', function(data) {
				console.log(data, "接收参数，接收参数")
			})
		},
		mounted() {
			const query = wx.createSelectorQuery()
			query.select('#navbarcus').boundingClientRect((result) => {
				this.navbarcusheight = result.height + 'px'
			}).exec()
			query.select('#title').boundingClientRect((result) => {
				this.titleheight = result.height + 'px'
			}).exec()
		}
	}
</script>

<style scoped lang="scss">
	.contentdatail {
		font-size: 26rpx;
		margin-top: 20rpx;
		// background-color: seagreen;
		height: calc(100vh - var(--navbarcusheight) - var(--titleheight) - 180rpx);
	}

	.tags {
		font-size: 20rpx;
		padding: 5rpx 10rpx;
		height: 30rpx;
		line-height: 30rpx;
		background-color: #f2f2f2;
		margin-right: 10rpx;
		border-radius: 10rpx;
		display: inline-block;
	}

	.title {
		padding-bottom: 25rpx;
		border-bottom: 1px solid #ccc;
	}

	.content {
		// background-color: pink;
		box-sizing: border-box;
		padding: 40rpx 40rpx;
		height: calc(100vh - var(--navbarcusheight));
	}
</style>