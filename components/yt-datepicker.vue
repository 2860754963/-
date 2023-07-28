<template>
	<view class="main" :style="{'--width':width,'--height':height}" @click="show = true">
		<view style="display: flex;height: 100%;">
			<u-icon name="calendar" :size="iconSize" color="#ccc" size='23'></u-icon>
			<view style="display: flex;flex-direction: column;justify-content: center;">
				<input :placeholder="inputPlaceholder" :value="inputValue" disabled style="font-size: 26rpx;"></input>
			</view>
		</view>
		<u-datetime-picker id="datePicker" :show="show" v-model="value1" :mode="datetimeMode" :title='dateTitle'
			@confirm='dateConfirm' @cancel='dateCancel' @change='dateChange'></u-datetime-picker>

	</view>
</template>

<script>
	export default {
		props: {

			datetimeMode: {
				type: String,
				default: 'date',
				required: false
			},
			inputPlaceholder: {
				type: String,
				default: '请选择',
				required: false
			},
			dateTitle: {
				type: String,
				default: '选择时间',
				required: false
			},
			iconSize: {
				type: Number,
				default: 30,
				required: false
			},
			width: {
				type: String,
				default: '240rpx',
				required: false
			},
			height: {
				type: String,
				default: '55rpx',
				required: false
			}
		},
		data() {
			return {
				show: false,
				value1: Number(new Date()),
				inputValue: ''
			}
		},
		methods: {

			dateConfirm(e) {
				let dateRes = this.result(e.value, e.mode)
				this.inputValue = dateRes
				this.$emit('datePickerConfirm', this.inputValue)
				this.show = false

			},
			dateCancel() {
				this.show = false
			},
			dateChange(value, mode) {
				console.log('值改变了', value);
			},
			result(time, mode) {
				const timeFormat = uni.$u.timeFormat
				switch (mode) {
					case 'datetime':
						return timeFormat(time, 'yyyy-mm-dd hh:MM')
					case 'date':
						return timeFormat(time, 'yyyy-mm-dd')
					case 'year-month':
						return timeFormat(time, 'yyyy-mm')
					case 'time':
						return time
					default:
						return ''
				}
			},
			appendDomToRoot(el, selector) {
				const query = this.createSelectorQuery()
				let container = query.select(selector)
				container.appendChild(el);
			}
		},
		mounted() {
			// const query = this.createSelectorQuery()
			// this.appendDomToRoot(query.select("#datePicker"), "#oilMain");
		},
	}
</script>

<style lang="scss" scoped>
	.main {
		border: 1px solid #ccc;
		background-color: #fff;
		width: var(--width);
		height: var(--height);
	}
</style>