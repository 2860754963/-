<template>
	<view>
		<view id="navbarcus">
			<u-navbar height="50" placeholder bgColor="#4989ff" left-text="油品联量明细" left-text-color='#fff' autoBack
				leftIconColor='#fff'>
			</u-navbar>
		</view>
		<view class="main" :style="{'--height':height}">
			<view class="top">
				<view class="toptop">
					<view style="display: flex;">
						<u-icon name="order" color="#74b4b3" style="line-height: 80rpx;margin-right: 10rpx;"></u-icon>
						<view>
							油品联量明细统计
						</view>
					</view>
					<view style="display: flex;">
						<view style="margin-right: 20rpx;">
							累计：<text style="color:#4989ff ;">6173.80</text>
						</view>
						<view class="">
							今日：<text style="color:#4989ff ;">6173.80</text>
						</view>
					</view>
				</view>
				<view class="topbottom">
					<u-scroll-list indicatorColor="#ccc" indicatorActiveColor="#4989ff">
						<view class="scroll-list" style="flex-direction: row;">
							<view class="topbottomlist" v-for="(item, index) in goodsArr" :key="index">
								<view> {{ item.price }}#</view>
								<view style="color:#4989ff ;">{{item.thumbnail }}</view>
							</view>
						</view>
					</u-scroll-list>
				</view>
			</view>
			<view class="bottomlist">
				<view class="bottomtop">

				</view>
				<view class="resultlist">

				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				height: 0,
				goodsArr: [{
						price: '230.5',
						thumbnail: '121'
					},
					{
						price: '74.1',
						thumbnail: '26574'
					},
					{
						price: '8457',
						thumbnail: '9802.2'
					},
					{
						price: '1442',
						thumbnail: '86712'
					},
					{
						price: '541',
						thumbnail: '1289'
					},
					{
						price: '234',
						thumbnail: '9852'
					},
					{
						price: '562',
						thumbnail: '25'
					},
					{
						price: '251.5',
						thumbnail: '12.365'
					},

				],
			};
		},
		mounted() {


		},

		onLoad: function() {
			// 获取顶部navbar的高度 用于css计算
			const query = wx.createSelectorQuery()
			query.select('#navbarcus').boundingClientRect((result) => {
				this.height = result.height + 'px'
			}).exec()


		}
	}
</script>

<style lang="scss" scoped>
	.bottomlist {
		position: relative;
		top: 20rpx;
		height: 70%;
		left: 50%;
		transform: translateX(-50%);
		background-color: #fff;
		width: 92%;

		.bottomtop {
			border-bottom: 1px dashed #ccc;
		}
	}

	.toptop {
		display: flex;
		justify-content: space-between;
		height: 80rpx;
		line-height: 80rpx;
		border-bottom: 1px solid #ccc;
		font-size: 26rpx;
	}

	.top {
		background-color: #fff;
		padding-left: 40rpx;
		padding-right: 40rpx;
	}

	.main {
		background-color: pink;
		height: calc(100vh - var(--height));
	}




	.topbottomlist:last-child {
		border-right: none !important;
	}

	.scroll-list {
		@include flex(column);

		&__goods-item {
			margin-right: 20px;
		}

		.topbottomlist {
			width: 140rpx;
			height: 140rpx;
			text-align: center;
			display: flex;
			flex-direction: column;
			justify-content: space-around;
			border-right: 1px solid #ccc;
			margin-top: 20rpx;
			margin-right: 10rpx;
		}


	}
</style>