<template>
	<view>
		<view>
			<u-navbar height="50" placeholder bgColor="#5b89fd" left-text="评比排名" left-text-color='#fff' autoBack
				leftIconColor='#fff'>
			</u-navbar>
		</view>
		<view class="topbg">
			<view class="ranktext">排行榜</view>
			<view class="ranktime">
				<view style="margin-right: 5rpx;">
					更新时间：
				</view>
				<view>
					2023-06-20
				</view>
			</view>
			<view class="topimage">
				<img src="https://s1.ax1x.com/2023/07/05/pCyEnWq.png" alt="pCyEnWq.png" border="0"
					style="width: 350rpx;height: 250rpx;" />
			</view>
		</view>
		<view class="bottomPannel">

		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			};
		},
		mounted() {
			const query = wx.createSelectorQuery()
			query.select('#navbarcus').boundingClientRect((result) => {
				this.navbarcusheight = result.height + 'px'
			}).exec()
		}
	}
</script>

<style lang="scss" scoped>
	.topimage {
		float: right;
		margin-top: -210rpx;

	}

	.ranktime {
		display: flex;
		padding-left: 50rpx;
		color: #fff;
		font-size: 30rpx;
	}

	.ranktext {
		padding: 50rpx;
		margin-bottom: 10rpx;
		color: #fff;
		font-size: 90rpx;
		line-height: 80rpx;
		font-weight: 800;
	}

	.topbg {
		width: 100%;
		height: 361rpx;
		// background: linear-gradient(to right );
		background-color: #5b89fd;
	}
</style>