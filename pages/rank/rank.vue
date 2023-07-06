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
		<view class="bottomPannel" style="width: 100%;">
			<!-- table begin -->
			<uni-table border stripe emptyText="暂无更多数据">
				<!-- 表头行 -->
				<uni-tr>
					<uni-th align="center">日期</uni-th>
					<uni-th align="center">姓名</uni-th>
					<uni-th align="left">地址</uni-th>
				</uni-tr>
				<!-- 表格数据行 -->
				<uni-tr>
					<uni-td>2020-10-1231231123122312312312320</uni-td>
					<uni-td>Jeso1231231212312312312312312312312312n</uni-td>
					<uni-td>北京123123123123123123123123123123123市海淀区</uni-td>
				</uni-tr>
				<uni-tr>
					<uni-td>2020-10-21</uni-td>
					<uni-td>HanMeiMei</uni-td>
					<uni-td>北京市海淀区</uni-td>
				</uni-tr>
				<uni-tr>
					<uni-td>2020-10-22</uni-td>
					<uni-td>LiLei</uni-td>
					<uni-td>北京市海淀区</uni-td>
				</uni-tr>
				<uni-tr>
					<uni-td>2020-10-23</uni-td>
					<uni-td>Danner</uni-td>
					<uni-td>北京市海淀区</uni-td>
				</uni-tr>

			</uni-table>
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
			// query.select('#navbarcus').boundingClientRect((result) => {
			// 	this.navbarcusheight = result.height + 'px'
			// }).exec()
		}
	}
</script>

<style lang="scss" scoped>
	/deep/.uni-table-scroll {
		overflow: visible;
	}

	/deep/.uni-table {
		// background-color: pink !important;
		// display: block !important;
		width: 100vw !important;
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
		height: 361rpx;
		// background: linear-gradient(to right );
		background-color: #5b89fd;
	}
</style>