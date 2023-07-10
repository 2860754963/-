<template>
	<view class="content">
		<view id="navbarcus">
			<u-navbar height="50" placeholder bgColor="#4989ff" left-text="团队成员" left-text-color='#fff' autoBack
				leftIconColor='#fff'>
			</u-navbar>
		</view>
		<scroll-view scroll-y style="padding-left: 40rpx;" @scrolltolower='scrolltolower' show-scrollbar
			:style="{'--navbarcusheight':navbarcusheight}" class="scrollview">

			<view class="scrolItem" v-for="(item,index) in list " :key="item"
				:class="{ 'no-border': isLastItem(index) }">
				<view style="margin-right: 40rpx;margin-top: 30rpx;">
					<u-avatar :src="userAvater" shape="square" size='60'></u-avatar>
				</view>
				<view style="display: flex; flex-direction: column; justify-content: center;">
					<view style="margin-bottom: 5rpx;font-size: 30rpx;">
						{{username}}
					</view>
					<view style="color: #8d8d8d;font-size: 25rpx;">
						{{usertel}}
					</view>
				</view>
			</view>
			<view style="width: 650rpx;padding-bottom: 40rpx;">
				<!-- <u-loadmore :status="loadStatus" /> -->
				<u-divider :text="loadStatus" textColor="#2979ff" lineColor="#2979ff"></u-divider>
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
				list: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14],
				navbarcusheight: 0,
				loadStatus: '这里有更多',

			};
		},
		methods: {
			isLastItem(index) {
				return index === this.list.length - 1;
			},
			async scrolltolower() {
				console.log('滚动到底部');
				await this.loadingdata()

			},
			clickSelect(e) {
				console.log(e, "e===========");
			},
			refre() {
				console.log('被下拉');
			},
			loadingdata() {
				this.loadStatus = '正在加载中'
				if (this.list.length === 17) {
					this.loadStatus = '我是有底线的'
					return
				}
				setTimeout(() => {
					this.list.push(1)
					this.loadStatus = '我是有底线的'
				}, 5000)

				// setTimeout(() => {
				// 	this.list.push(1)
				// }, 5000)
				// this.loadStatus = '我是有底线的'
			}
		},
		mounted() {
			const query = wx.createSelectorQuery()
			query.select('#navbarcus').boundingClientRect((result) => {
				this.navbarcusheight = result.height + 'px'
				console.log(this.navbarcusheight, "this.navbarcusheightthis.navbarcusheight");
			}).exec()
		}
	}
</script>

<style lang="scss" scoped>
	.scrollview {
		height: calc(100vh - var(--navbarcusheight));
	}

	.scrolItem {
		display: flex;
		height: 180rpx;
		border-bottom: 1px solid #ccc;
	}

	.no-border {
		border-bottom: none;
		height: 168rpx;
	}

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