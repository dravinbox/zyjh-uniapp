<template>
	<view class="item">
		<view class="flex padding-xs justify-between">
			<view class="flex  padding-xs justify-start align-center">
				<view class="bg-white padding-sm margin-xs radius text-lg text-bold">{{title}}</view>
				<view class="bg-gray padding-xs margin-xs radius text-sm" @click="showModal" data-target="RadioModal">{{selectedRadio}}<text
					 class="cuIcon-unfold"></text></view>
			</view>
			<view class="bg-white padding-sm margin-xs radius" @click="refresh">换一批</view>
		</view>

		<view class="padding-xs">

			<view class="flex  padding-xs justify-between bg-gray">
				<view class="bg-gray padding-sm margin-xs radius">计划名称</view>
				<view class="bg-gray padding-sm margin-xs radius">码数</view>
				<view class="bg-gray padding-sm margin-xs radius">期数</view>
				<view class="bg-gray padding-sm margin-xs radius">中奖率</view>
			</view>

			<view>
				<view class="flex solid-bottom padding-xs justify-between bg-white"
					v-for="(item,index) in tableList" :key="index"
					>
					<view class="bg-white padding-sm margin-xs radius" @click="openPlanDetail">{{item.planName}}</view>
					<view class="bg-white padding-sm margin-xs radius">{{item.codeNum}}</view>
					<view class="bg-white padding-sm margin-xs radius">第{{item.nper}}期</view>
					<view class="bg-white padding-sm margin-xs radius text-red">{{item.rate}}%</view>
				</view>
				
			</view>
		</view>

		<view class="flex padding-sm margin-xs text-lg justify-center align-center" @click="toDetail"><text>更多</text> <text class="cuIcon-roundright"></text></view>

		<view class="cu-modal" :class="modalName=='RadioModal'?'show':''" @tap="hideModal">
			<view class="cu-dialog" @tap.stop="">
				<radio-group class="block" @change="RadioChange">
					<view class="cu-list menu text-left">
						<view class="cu-item" v-for="(item,index) in radioList" :key="index">
							<label class="flex justify-between align-center flex-sub">
								<view class="flex-sub">{{item}}</view>
								<radio class="round" 
									:class="radio==index?'checked':''" 
									:checked="radio==index?true:false"
									:value="''+index">
								</radio>
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

		props: {
			title: {
				type: String,
				default: 'value'
			},
			radioList: {
				type: Array,
				default: () => ['无']
			},
			tableList: {
				type: Array,
				default: () => [
					
				]
			},
		},
		computed:{
			selectedRadio(){
				return this.radioList[this.radio];
			}
		},

		data() {
			return {
				modalName: null,
				radio: '1',

			}
		},
		methods: {
			openPlanDetail(){
				uni.navigateTo({
					url: '/pages/index/detail1'
				});
			},
			showModal(e) {
				console.log(e)
				this.modalName = e.currentTarget.dataset.target
				console.log(this.modalName)
			},
			hideModal(e) {
				this.modalName = null
			},
			RadioChange(e) {
				// 改变选中值
				this.radio = e.detail.value
				// 隐藏选择框
				this.hideModal()
				
			},
			refresh(){
				console.log("请求api，换一批")
			},
			toDetail(){
				uni.navigateTo({
					url: '/pages/index/detail'
				});
				
			}
		}
	}
</script>

<style scoped lang="scss">
	.item {
		margin-top: 25rpx;
		background-color: #fff;


	}
</style>
