<template>
	<view>
		<view id="navbarcus">
			<u-navbar height="50" placeholder bgColor="#4989ff" left-text="油品联量明细" left-text-color='#fff' autoBack
				leftIconColor='#fff'>
			</u-navbar>
		</view>
		<view class="main" :style="{'--height':height}">
			<view style="display: flex; justify-content: space-between;">
				<view class="">
					油品联量明细统计
				</view>
				<view style="display: flex;">
					<view style="margin-right: 10rpx;">
						累计：<text>6173.80</text>
					</view>
					<view class="">
						今日：<text>6173.80</text>
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
				height: 0
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
	.main {
		background-color: pink;
		height: calc(100vh - var(--height));
	}
</style>