<template>
	<view>
		<view id="navbarcus">
			<u-navbar height="50" placeholder bgColor="#5b89fd" left-text="招聘信息" left-text-color='#fff' autoBack
				leftIconColor='#fff'>
			</u-navbar>
		</view>
		<view class="">
			<view class="" id="tabs">
				<u-tabs :list="list1" @click="toggletabs" :scrollable='false'></u-tabs>
			</view>
			<view class="resultlist" :style="{'--navbarcusheight':navbarcusheight,'--tabsheight':tabsheight}">
				<scroll-view scroll-y="true" style="height: 100%;" @scrolltolower='loadingMore'>
					<view class="resultItem" v-for="(item,index) in tagslist " :key='index' @click="toDetails(item)">
						<view class="">
							<view class="" style="font-size: 31rpx;margin-bottom: 8rpx;">
								标题设备管理员
							</view>
						</view>
						<view class="" style="font-size: 26rpx;color: #878787;margin-bottom: 8rpx;">
							万州加油站
						</view>
						<view class="">
							<view class="tags" v-for="(item,index) in tagslist" :key="index">
								{{item}}
							</view>
						</view>
						<view class="itemContent">
							内容：万州加油站急需管理员2命万州加油站急需管理员2命万州加油站急需管理员2命万州加油站急需管理员2命
						</view>
					</view>

				</scroll-view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				tagslist: ['设备管理员', '本科', '1-3年经验', '硕士', '国际奖牌', '奖金', '奖学金', '啥都要', '啥都要'],
				list1: [{
					name: '待审核'
				}, {
					name: '待确认'
				}, {
					name: '已通过'
				}, {
					name: '未通过'
				}],
				navbarcusheight: 0,
				tabsheight: 0
			}
		},
		methods: {
			toDetails(item) {
				let data = {
					a: '测试数据',
					b: [1, 2, 3, 4, 5, 6],
					c: {
						c1: '测试数据',
						c2: '测试数据2'
					}
				}
				uni.navigateTo({
					url: '/pages/recuitDetails/recuitDetails',
					success: function(res) {
						res.eventChannel.emit('resultItem', {
							data
						})
					}
				})
			},
			loadingMore() {
				console.log('触底加载更多');
			},
			toggletabs(e) {
				console.log(e, 'e');
			}
		},
		mounted() {
			const query = wx.createSelectorQuery()
			query.select('#navbarcus').boundingClientRect((result) => {
				this.navbarcusheight = result.height + 'px'
			}).exec()
			query.select('#tabs').boundingClientRect((result) => {
				this.tabsheight = result.height + 'px'
			}).exec()
		}
	}
</script>

<style scoped lang="scss">
	.itemContent {
		white-space: nowrap;
		overflow: hidden;
		text-overflow: ellipsis;
		height: 50rpx;
		line-height: 50rpx;
		font-size: 24rpx;

	}

	.tags {
		font-size: 20rpx;
		padding: 5rpx 10rpx;
		height: 30rpx;
		line-height: 30rpx;
		background-color: #ccc;
		margin-right: 10rpx;
		border-radius: 10rpx;
		display: inline-block;
	}

	.resultItem {
		display: flex;
		flex-direction: column;
		justify-content: space-evenly;
		padding: 18rpx 20rpx;
		background-color: #fff;
		margin-bottom: 10rpx;
		border-bottom: 10rpx solid #ccc;
	}

	.resultlist {
		box-sizing: border-box;
		background-color: #fff;
		height: calc(100vh - var(--navbarcusheight) - var(--tabsheight));
		padding: 10rpx 30rpx 10rpx 30rpx;
	}
</style>