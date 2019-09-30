<template>
	<view class="item">
		<view class="flex  padding-xs justify-between">
			<view class="flex  padding-xs justify-start align-center">
				<view class="bg-white padding-sm margin-xs radius text-lg text-bold">定位胆</view>
				<view class="bg-gray padding-xs margin-xs radius text-sm" @click="showModal" data-target="RadioModal">定胆个位<text class="cuIcon-unfold"></text></view>
			</view>
			<view class="bg-white padding-sm margin-xs radius">换一批</view>
		</view>

		<view class="padding-xs">

			<view class="flex  padding-xs justify-between bg-gray">
				<view class="bg-gray padding-sm margin-xs radius">计划名称</view>
				<view class="bg-gray padding-sm margin-xs radius">码数</view>
				<view class="bg-gray padding-sm margin-xs radius">期数</view>
				<view class="bg-gray padding-sm margin-xs radius">中奖率</view>
			</view>

			<view>
				<view class="flex solid-bottom padding-xs justify-between bg-white">
					<view class="bg-white padding-sm margin-xs radius">桃花计划</view>
					<view class="bg-white padding-sm margin-xs radius">5</view>
					<view class="bg-white padding-sm margin-xs radius">第1期</view>
					<view class="bg-white padding-sm margin-xs radius text-red">100%</view>
				</view>
				<view class="flex solid-bottom padding-xs justify-between bg-white">
					<view class="bg-white padding-sm margin-xs radius">桃花计划</view>
					<view class="bg-white padding-sm margin-xs radius">5</view>
					<view class="bg-white padding-sm margin-xs radius">第1期</view>
					<view class="bg-white padding-sm margin-xs radius text-red">100%</view>
				</view>
				<view class="flex solid-bottom padding-xs justify-between bg-white">
					<view class="bg-white padding-sm margin-xs radius">桃花计划</view>
					<view class="bg-white padding-sm margin-xs radius">5</view>
					<view class="bg-white padding-sm margin-xs radius">第1期</view>
					<view class="bg-white padding-sm margin-xs radius text-red">100%</view>
				</view>
				<view class="flex solid-bottom padding-xs justify-between bg-white">
					<view class="bg-white padding-sm margin-xs radius">桃花计划</view>
					<view class="bg-white padding-sm margin-xs radius">5</view>
					<view class="bg-white padding-sm margin-xs radius">第1期</view>
					<view class="bg-white padding-sm margin-xs radius text-red">100%</view>
				</view>
				<view class="flex solid-bottom padding-xs justify-between bg-white">
					<view class="bg-white padding-sm margin-xs radius">桃花计划</view>
					<view class="bg-white padding-sm margin-xs radius">5</view>
					<view class="bg-white padding-sm margin-xs radius">第1期</view>
					<view class="bg-white padding-sm margin-xs radius text-red">100%</view>
				</view>
			</view>
		</view>

		<view class="flex padding-sm margin-xs text-lg justify-center align-center" ><text>更多</text> <text
			 class="cuIcon-roundright"></text></view>

		<view class="cu-modal"  :class="modalName=='RadioModal'?'show':''" @tap="hideModal">
			<view class="cu-dialog" @tap.stop="">
				<radio-group class="block" @change="RadioChange">
					<view class="cu-list menu text-left">
						<view class="cu-item" v-for="(item,index) in radioList" :key="index">
							<label class="flex justify-between align-center flex-sub">
								<view class="flex-sub">{{item}}</view>
								<radio class="round" :class="radio=='radio' + index?'checked':''" :checked="radio=='radio' + index?true:false"
								 :value="'radio' + index"></radio>
							</label>
						</view>
					</view>
				</radio-group>
			</view>
		</view>
	</view>
</template>

<script>
	export default {

		data() {
			return {
				modalName: null,
				radio: 'radio1',
				radioList:[
					'定胆个位',
					'定胆十位',
					'定胆百位',
					'定胆千位',
					'定胆万位',
				]
			}
		},
		methods: {
			showModal(e) {
				console.log(e)
				this.modalName = e.currentTarget.dataset.target
				console.log(this.modalName)
			},
			hideModal(e) {
				this.modalName = null
			},
			RadioChange(e) {
							this.radio = e.detail.value
						},
		}
	}
</script>

<style scoped lang="scss">
	.item {
		margin-top: 25rpx;
		background-color: #fff;


	}
</style>
