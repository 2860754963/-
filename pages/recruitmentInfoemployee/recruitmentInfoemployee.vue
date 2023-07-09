<template>
	<view class="main">
		<view id="navbarcus">
			<u-navbar height="50" placeholder bgColor="#4989ff" left-text="招聘信息(员工)" left-text-color='#fff' autoBack
				leftIconColor='#fff'>
			</u-navbar>
		</view>
		<view class="topsearch" id="topsearch">
			<u-search placeholder="请输入标题" :clearabled="true" v-model="searchvalue" :showAction="true" actionText="搜索"
				bgColor='#fff' borderColor='#ccc'
				:actionStyle='{"background-color": "#5b89fd;","margin-left": "20rpx;","color":"#fff;","width":"140rpx;","height":"65rpx;","line-height":"65rpx","text-align":"center;","border-radius":"40rpx;"}'></u-search>
		</view>
		<view class="bottombody">
			<view class="utabs" id="utabs">
				<u-tabs :list="tabslist" @click="click"></u-tabs>
			</view>
			<view class="resultlist"
				:style="{'--navbarcusheight':navbarcusheight,'--topsearchheight':topsearchheight,'--utabsheight':utabsheight}">
				<scroll-view scroll-y="true" style="height: 100%;" @scrolltolower='loadingMore'>
					<view class="resultItem" v-for="(item,index) in tagslist " :key='index'>
						<view class="" style="display: flex;justify-content: space-between;">
							<view class="" style="font-size: 31rpx;margin-bottom: 8rpx;">
								标题设备管理员
							</view>
							<view class="" style="font-size: 20rpx;color: red;line-height: 40rpx;">
								报名时间：4天24：30：10
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
				searchvalue: '',
				tabslist: [{
					name: '最新'
				}, {
					name: '最热'
				}],
				navbarcusheight: '',
				topsearchheight: '',
				utabsheight: ''
			};
		},
		methods: {
			click() {
				console.log('点击');
			},
			loadingMore() {
				console.log('触底加载更多');
			}
		},
		mounted() {
			const query = wx.createSelectorQuery()
			query.select('#navbarcus').boundingClientRect((result) => {
				this.navbarcusheight = result.height + 'px'
			}).exec()
			query.select('#topsearch').boundingClientRect((result) => {
				this.topsearchheight = result.height + 'px'
			}).exec()
			query.select('#topsearch').boundingClientRect((result) => {
				this.utabsheight = result.height + 'px'
			}).exec()
		}
	}
</script>

<style lang="scss" scoped>
	.itemContent {
		white-space: nowrap;
		overflow: hidden;
		text-overflow: ellipsis;
		height: 50rpx;
		line-height: 50rpx;
		font-size: 24rpx;

	}

	.resultItem {
		display: flex;
		flex-direction: column;
		justify-content: space-evenly;
		padding: 18rpx 20rpx;
		background-color: #fff;
		margin-bottom: 10rpx;
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

	.resultlist {
		height: calc(100vh - var(--navbarcusheight) - var(--topsearchheight) - var(--utabsheight));
		background-color: #ccc;
	}

	.bottombody {
		margin: 10rpx 20rpx;
		padding: 0 20rpx;
		background-color: #fff;
	}

	.topsearch {
		padding: 40rpx 20rpx;
		background-color: #fff;
	}

	.main {
		width: 100vw;
		height: 100vh;
		background-color: #f9f9f9;
	}
</style>