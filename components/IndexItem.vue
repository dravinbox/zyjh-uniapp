<template>
	<view class="item">
		<view class="flex padding-xs justify-between">
			<view class="flex  padding-xs justify-start align-center">
				<view class="bg-white padding-sm margin-xs radius text-lg text-bold">{{title}}</view>
				<view class="bg-gray padding-xs margin-xs radius text-sm Drop-down-Wrapper" @click="showclick" data-target="RadioModal">{{selectedRadio}}<text
					 class="cuIcon-unfold"></text>
					<view class="mask" v-show="show" @click.stop="showclick"></view>
					<view class="Drop-down" v-show="show">
						<li class="li">{{selectedRadio}}</li>
						<li class="li">定位个胆</li>
						<li class="li">定位个胆</li>
						<li class="li">定位个胆</li>
						<li class="li">定位个胆</li>
					</view>
				</view>
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
				<view class="flex solid-bottom padding-xs justify-between bg-white" v-for="(item,index) in tableList" :key="index">
					<view class="bg-white padding-sm margin-xs radius" @click="openPlanDetail">{{item.planName}}</view>
					<view class="bg-white padding-sm margin-xs radius">{{item.codeNum}}</view>
					<view class="bg-white padding-sm margin-xs radius">第{{item.nper}}期</view>
					<view class="bg-white padding-sm margin-xs radius text-red">{{item.rate}}%</view>
				</view>

			</view>
		</view>

		<view class="flex padding-sm margin-xs text-lg justify-center align-center" @click="toDetail"><text>更多</text> <text
			 class="cuIcon-roundright"></text></view>

		<view class="cu-modal" :class="modalName=='RadioModal'?'show':''" @tap="hideModal">
			<view class="cu-dialog" @tap.stop="">
				<radio-group class="block" @change="RadioChange">
					<view class="cu-list menu text-left">
						<view class="cu-item" v-for="(item,index) in radioList" :key="index">
							<label class="flex justify-between align-center flex-sub">
								<view class="flex-sub">{{item}}</view>
								<radio class="round" :class="radio==index?'checked':''" :checked="radio==index?true:false" :value="''+index">
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
			index:{
				type:Number,
				default:0,
			},
			show: {
				type: Boolean,
				default: true
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
		computed: {
			selectedRadio() {
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
			showclick(){
				// this.show = !this.show
				this.$emit('sendChildData',{show:!this.show,index:this.index})
			},
			openPlanDetail() {
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
			refresh() {
				console.log("请求api，换一批")
			},
			toDetail() {
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


	.Drop-down-Wrapper {
		position: relative;

		.mask {
			position: fixed;
			background: red;
			width: 100%;
			height: 100%;
			top: 0;
			left: 0;
			z-index: 9999;
			opacity: 0;
		}
	}

	.Drop-down {
		// display: none;
		position: absolute;
		z-index: 19999;
		background: #fff;
		white-space: nowrap;
		left: -5px;
		margin-top: 14px;
		box-shadow: 0px 3px 9px 0px #555;

		.li {
			height: 20px;
			padding: 10px 20px;
			border-bottom: 1px solid #ccc;
			list-style: none;
			line-height: 20px;
		}
	}
</style>
