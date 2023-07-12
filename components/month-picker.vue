<template>
	<view class="main">
		<u-icon name="arrow-left" color="#2979ff" size="18" @click='leftclick'></u-icon>
		<view style="color: #2979ff;">
			{{nowmonth}}
		</view>
		<u-icon name="arrow-right" color="#2979ff" size="18" @click='rightclick'></u-icon>
	</view>
</template>

<script>
	import moment from 'moment'
	export default {
		name: 'monthpicker',
		props: {
			format: {
				type: String,
				default: 'YYYY-MM'
			},
		},
		data() {
			return {
				nowmonth: null
			}
		},
		methods: {
			moment,
			getmonth() {
				//默认上个月
				this.nowmonth = this.moment().subtract(1, 'months').format(this.format)
			},
			leftclick() {
				console.log('leftclick');
				this.nowmonth = this.moment(this.nowmonth).subtract(1, 'months').format(this.format)
				this.$emit('monthchange', this.nowmonth)
			},
			rightclick() {
				console.log('rightclick');
				this.nowmonth = this.moment(this.nowmonth).add(1, 'months').format(this.format)
				this.$emit('monthchange', this.nowmonth)
			}
		},
		created() {
			this.getmonth()
		}
	}
</script>

<style scoped lang="scss">
	.main {
		// background-color: pink;
		display: flex;
	}
</style>