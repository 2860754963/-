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
				<u-tabs :list="tabslist" :scrollable='false' :lineWidth='40' @click="changeresult"></u-tabs>
				<view class="userrank">
					<view class="uranktop">
						<view class="uranktoptop">
							<view class="uranktoptitle">
								站内月度排名
							</view>
							<view class="">
								<view class="" data-name="0" @click="changeresult"
									style="display: flex;color: #a1a1a1;">
									切换为省市排名 <u-icon name="arrow-right" color="#2979ff" size="19"></u-icon>
								</view>
								<view class="" data-name="1" @click="changeresult" style="display: flex;color: #ccc;"
									v-if="false">
									切换为分公司排名 <u-icon name="arrow-right" color="#2979ff" size="19"></u-icon>
								</view>
							</view>
						</view>
					</view>
					<view class="grand">
						<view class="mygrand">
							<view class="grandleft">
								<view class="grandlefttitle">
									我的成绩
								</view>
								<view class="">
									<u-avatar :src="src"></u-avatar>
								</view>
								<view class="">
									张三
								</view>
							</view>

							<view class="grandright">
								<view class="grandrightRink">
									第15名
								</view>
								<view class=""
									style="	display: inline-block;height: 60rpx;width: 2rpx;background-color: #a1a1a1;">
								</view>
								<view class="">
									372.80
								</view>
							</view>
						</view>
					</view>
					<view class="rankitemtitle">
						<view class="itemtitleleft">
							<view class="">
								排名
							</view>
							<view class="">
								姓名
							</view>
						</view>
						<view class="itemtitleright">
							销量
						</view>
					</view>
				</view>
			</u-sticky>
		</template>
		<view class="rankresultlist" style="" v-for="(item,index) in list" :key="index"
			:class="index==0?'firstaddpadding':''">

			<view class="" style="display: flex;justify-content: space-between;align-items: center;width: 55%;">
				<view class="" style="width: 60rpx;text-align: center;margin-left: 5rpx;">
					{{index+1}}
				</view>
				<view class="" style="display: flex;width: 80%; align-items: center;">
					<view class="" style="margin-right: 20rpx;">
						<u-avatar :src="src"></u-avatar>
					</view>
					<view class="">
						周芳
					</view>
				</view>
			</view>
			<view class="">
				18739.34
			</view>
		</view>

	</view>
</template>

<script>
	import moment from 'moment'
	export default {
		data() {
			return {
				src: '',
				list: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20],
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
			changeresult(e) {
				console.log(e, "重新请求");
			}
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
	.firstaddpadding {
		margin-top: 174rpx !important;
	}

	.rankresultlist {
		display: flex;
		height: 128rpx;
		background-color: #fff;
		padding-left: 20rpx;
		padding-right: 20rpx;
		align-items: center;
		justify-content: space-between;
	}


	.rankitemtitle {
		background-color: #fff;
		// display: flex;
		// align-items: center;
		width: 100%;
		height: 90rpx;
		font-size: 29rpx;
		color: #a1a1a1;

		.itemtitleleft {
			float: left;
			display: flex;
			line-height: 90rpx;
			width: 35%;
			justify-content: space-around;
		}

		.itemtitleright {
			float: right;
			line-height: 90rpx;
			margin-right: 48rpx;
		}
	}

	.mygrand {
		position: relative;
		width: 90%;
		left: 50%;
		transform: translateX(-50%);
		display: flex;
		justify-content: space-between;
		align-items: center;
		height: 120rpx;
		background-color: #fff;
		border: 1px solid #e2e2e2;
		box-sizing: border-box;
		padding: 30rpx 20rpx;
		font-weight: 600;
		border-radius: 15rpx;

		.grandleft {
			display: flex;
			align-items: center;
			width: 50%;
			justify-content: space-evenly;

			.grandlefttitle {
				// height: 120rpx;
				// width: 120rpx;
				width: 75rpx;
				font-size: 35rpx;

				color: #6889fb;
			}
		}

		.grandright {
			display: flex;
			justify-content: space-evenly;
			color: #6889fb;
			width: 43%;
			align-items: center;


		}
	}



	.grand {
		width: 100%;
		height: 120rpx;
		background-color: #fff;
	}

	.uranktoptop {
		display: flex;
		justify-content: space-between;
		width: 100%;
	}

	.userrank {
		height: 160rpx;
		background-color: #fff;

		.uranktop {
			display: flex;
			// justify-content: space-between;
			align-items: center;
			height: 60rpx;
			line-height: 60rpx;
			font-size: 29rpx;
			padding: 20rpx 10rpx;
			text-align: center;

			.uranktoptitle {
				text-align: center;
				line-height: 60rpx;
				height: 60rpx;
				color: #6889fb;
			}


		}
	}

	.uranktop::before {
		content: '';
		display: inline-block;
		height: 36rpx;
		width: 10rpx;
		margin-left: 20rpx;
		margin-right: 10rpx;
		background-color: #6889fb;
		text-align: center;
	}

	/deep/.u-sticky {
		background-color: #fff !important;
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
		height: 279rpx;
		background-color: #5b89fd;
	}
</style>