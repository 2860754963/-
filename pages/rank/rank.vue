<template>
	<view>
		<view id="navbarcus">
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
					{{moment().format('YYYY-MM-DD')}}
				</view>
			</view>
			<view class="topimage">
				<img src="https://s1.ax1x.com/2023/07/05/pCyEnWq.png" alt="pCyEnWq.png" border="0"
					style="width: 350rpx;height: 250rpx;" />
			</view>
		</view>
		<template v-if="navbarcusheight" style="position: relative;">
			<u-sticky :customNavHeight='navbarcusheight' style="background-color: pink;">
				<u-tabs :list="tabslist" :scrollable='false' :lineWidth='40'></u-tabs>
			</u-sticky>
		</template>
		<view style="height: 240rpx;background-color: pink;" v-for="(item,index) in list" :key="index">
			123456
		</view>

	</view>
</template>

<script>
	import moment from 'moment'
	export default {
		data() {
			return {
				list: [1, 2, 3, 4, 5, 6, 7, 8],
				tabslist: [{
					name: '油品销量排名'
				}, {
					name: '非油品销量排名'
				}],
				navbarcusheight: 0,
			};
		},
		methods: {
			moment,
		},
		mounted() {
			const query = wx.createSelectorQuery()
			query.select('#navbarcus').boundingClientRect((result) => {
				this.navbarcusheight = result.height
			}).exec()
		},
		computed: {
			stickyoffsetTop() {
				return this.navbarcusheight + 45
			}
		},
	}
</script>

<style lang="scss" scoped>
	/deep/.u-sticky {
		background-color: pink !important;
	}

	.bottomPannel {
		position: absolute;
		width: 100%;
		top: 413rpx;
		background-color: #fff;
		border-radius: 20rpx 20rpx 0 0;
	}

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
		height: 348rpx;
		background-color: #5b89fd;
	}
</style>