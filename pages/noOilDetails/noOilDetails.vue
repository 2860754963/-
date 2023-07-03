<template>
	<view id="oilMain">
		<view id="navbarcus">
			<u-navbar height="50" placeholder bgColor="#4989ff" left-text="非油品联量明细" left-text-color='#fff' autoBack
				leftIconColor='#fff'>
			</u-navbar>
		</view>
		<view class="main" :style="{'--navbarcusheight':navbarcusheight}">
			<view class="top" id="top">
				<view class="toptop">
					<view style="display: flex;">
						<u-icon name="order" color="#74b4b3" style="line-height: 80rpx;margin-right: 10rpx;"></u-icon>
						<view>
							非油品联量明细统计
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
				<view class="bottomtop" id="bottomtop">
					<view class="leftyuan"></view>
					<view class="rightyuan"></view>
					<view style="display: flex;justify-content: space-evenly;">
						<ytdatepicker @datePickerConfirm='e=>starTime=e' inputPlaceholder='开始时间'></ytdatepicker>
						<ytdatepicker @datePickerConfirm='e=>endTime=e' inputPlaceholder='结束时间'></ytdatepicker>
					</view>
					<button type="primary" class="buttonSearch">查询 </button>
				</view>
				<view class="resultlist"
					:style="{'--topheight':topheight,'--bottomtopheight':bottomtopheight,'--navbarcusheight':navbarcusheight}">
					<scroll-view scroll-y="true" style="height: 100%;" @scrolltolower='loadingMore'>
						<view class="resultItem" v-for="(item,index) in resultitem" :key='index'
							:class="{ 'no-border': isLastItem(index) }">
							<view style="display: flex;flex-direction: column;justify-content: space-evenly;">
								<view style="display: flex;justify-content: space-around; width: 260rpx;">
									<view>
										0#
									</view>
									<view class="">
										枪号：8
									</view>
								</view>
								<view class="">
									2023-06-20 13:20:31
								</view>
							</view>
							<view style="display: flex;flex-direction: column;justify-content: space-evenly;">
								<view class="">
									销量：139.34
								</view>
								<view class="">
									计提：1939.34
								</view>
							</view>
						</view>
						<view style="height: 50rpx;line-height: 50rpx;padding-bottom: 40rpx;">
							<u-divider text="我是有底线的" textColor="#2979ff" lineColor="#2979ff"></u-divider>
						</view>
					</scroll-view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import ytdatepicker from 'components/yt-datepicker.vue'
	export default {
		components: {
			ytdatepicker
		},
		data() {
			return {
				bottomlistheight: 0,
				bottomtopheight: 0,
				navbarcusheight: 0,
				topheight: 0,
				starTime: '',
				endTime: '',
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
				resultitem: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21]
			};
		},
		methods: {
			loadingMore(e) {
				console.log('到达底部加载更多');
			},
			datePickerConfirm(e) {
				console.log(e, "eeeeee");
			},
			isLastItem(index) {
				return index === this.resultitem.length - 1;
			},
		},
		mounted() {
			const query = wx.createSelectorQuery()
			query.select('#navbarcus').boundingClientRect((result) => {
				this.navbarcusheight = result.height + 'px'
			}).exec()
			query.select('#top').boundingClientRect((result) => {
				this.topheight = result.height + 'px'
			}).exec()

			query.select('#bottomtop').boundingClientRect((result) => {
				this.bottomtopheight = result.height + 'px'
			}).exec()

		},

	}
</script>

<style lang="scss" scoped>
	.no-border {
		border-bottom: none !important;
	}

	.resultlist {
		height: calc(100vh - var(--navbarcusheight) - var(--topheight) - var(--bottomtopheight) - 20px);
	}

	.resultItem {
		height: 140rpx;
		background-color: #fff;
		display: flex;
		justify-content: space-between;
		padding: 0 40rpx;
		border-bottom: 1px solid #ccc;
	}

	.resultlist .resultItem:last-child {
		border-bottom: none;
	}

	.rightyuan {
		position: absolute;
		width: 30rpx;
		height: 30rpx;
		border-radius: 50%;
		background-color: #f4f4f4;
		right: -16rpx;
		bottom: -18rpx;
		z-index: 9999;
	}

	.leftyuan {
		position: absolute;
		width: 30rpx;
		height: 30rpx;
		border-radius: 50%;
		background-color: #f4f4f4;
		left: -16rpx;
		top: 184rpx;
		z-index: 9999;
	}

	.buttonSearch {
		width: 97%;
		background-color: #4989ff;
		// height: 76rpx;
		// line-height: 76rpx;
		font-size: 30rpx;
		margin-top: 10rpx;
	}

	.bottomlist {
		position: relative;
		top: 20rpx;
		height: calc(100vh - var(--topheight) - var(--navbarcusheight) - 20px);
		left: 50%;
		transform: translateX(-50%);
		background-color: #fff;
		width: 92%;

		.bottomtop {
			position: relative;
			display: flex;
			flex-direction: column;
			justify-content: space-evenly;
			border-bottom: 1px dashed #ccc;
			height: 200rpx;
			width: 100%;
			box-sizing: border-box;
			padding: 40rpx;
			padding-bottom: 20rpx;

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
		background-color: #f4f4f4;
		height: calc(100vh - var(--navbarcusheight));
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