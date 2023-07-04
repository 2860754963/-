<template>
	<view>
		<view>
			<u-navbar height="50" placeholder bgColor="#4989ff" left-text="评比排名" left-text-color='#fff' autoBack
				leftIconColor='#fff'>
			</u-navbar>
		</view>
		<view class="topbg" style="background-image: url('../../static/rankbg.png');">
			<view>排行榜</view>
			<view>
				<view>
					更新时间
				</view>
				<view>
					2023-06-20
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			};
		}
	}
</script>

<style lang="scss" scoped>
	.topbg {
		width: 100%;
		height: 20%;
		background-color: #4989ff;
	}
</style>