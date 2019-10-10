<template>
	<view>
		<cu-custom bgColor="bg-white" :isBack="true">
			<block slot="content">定位胆11</block>
		</cu-custom>
		
		<view class="head-menu">
			
		
		<view class=" bg-white flex justify-around align-center solid-bottom">
			<view>
				<view class="flex justify-between align-center ">

					<view class="flex justify-start align-center">
						<view>
							玩法：
						</view>
						<view class="bg-gray padding-xs margin-xs radius text-sm Drop-down-Wrapper" @click="select1 = !select1" data-target="RadioModal">定胆个位<text
							 class="cuIcon-unfold"></text>
							 <view class="mask" v-show="select1" @click.stop="select1 = !select1"></view>
							 <view class="Drop-down" v-show="select1">
							 	<li class="li">玩法</li>
							 	<li class="li">玩法</li>
							 	<li class="li">玩法</li>
							 	<li class="li">玩法</li>
							 </view>
						</view>
					</view>


					<view class="flex justify-start align-center">
						<view>
							中奖：
						</view>
						<view class="bg-gray padding-xs margin-xs radius text-sm Drop-down-Wrapper" @click="select2 = !select2" data-target="RadioModal">不限<text
							 class="cuIcon-unfold"></text>
							 <view class="mask" v-show="select2" @click.stop="select2 = !select2"></view>
							 <view class="Drop-down" v-show="select2">
							 	<li class="li">中奖</li>
							 	<li class="li">中奖</li>
							 	<li class="li">中奖</li>
							 	<li class="li">中奖</li>
							 </view>
						</view>
					</view>


				</view>
				<view class="flex justify-between align-center">
					<view class="flex justify-start align-center">
						<view>
							码数：
						</view>
						<view class="bg-gray padding-xs margin-xs radius text-sm Drop-down-Wrapper" @click="select3 = !select3" data-target="RadioModal">5<text
							 class="cuIcon-unfold"></text>
							 <view class="mask" v-show="select3" @click.stop="select3 = !select3"></view>
							 <view class="Drop-down" v-show="select3">
							 	<li class="li">码数</li>
							 	<li class="li">码数</li>
							 	<li class="li">码数</li>
							 	<li class="li">码数</li>
							 </view>
						</view>
					</view>
					<view class="flex justify-start align-center">
						<view>
							期数：
						</view>
						<view class="bg-gray padding-xs margin-xs radius text-sm Drop-down-Wrapper" @click="select4 = !select4" data-target="RadioModal">3<text
							 class="cuIcon-unfold"></text>
							 <view class="mask" v-show="select4" @click.stop="select4 = !select4"></view>
							 <view class="Drop-down" v-show="select4">
							 	<li class="li">期数</li>
							 	<li class="li">期数</li>
							 	<li class="li">期数</li>
							 	<li class="li">期数</li>
							 </view>
						</view>
					</view>
					<view class="flex justify-start align-center">
						<view>
							公式数：
						</view>
						<view class="bg-gray padding-xs margin-xs radius text-sm Drop-down-Wrapper" @click="select5 = !select5" data-target="RadioModal">150<text
							 class="cuIcon-unfold"></text>
							 <view class="mask" v-show="select5" @click.stop="select5 = !select5"></view>
							 <view class="Drop-down" v-show="select5">
							 	<li class="li">公式数</li>
							 	<li class="li">公式数</li>
							 	<li class="li">公式数</li>
							 	<li class="li">公式数</li>
							 </view>
						</view>
					</view>
				</view>
			</view>
			<view class="">
				<button class="cu-btn round bg-green">确定</button>
			</view>
		</view>
		
		<view class="bg-white text-center text-xs flex justify-around align-center padding-xs">
			<view>
				期号:222222 
			</view>
			
			<view>
				开奖号码<span class="text-red">4,4,4,2,1 </span>
			</view>
			
			<view>
				开奖时间 2000-01-01 10:10:00
			</view>
			
			
		</view>
		
		</view>
		

		<!-- 首页列表 -->
		<scroll-view scroll-y scroll-with-animation :scroll-top="scrollTop" class="item-list">


			<view class="flex  padding-xs justify-between bg-white">
				<view class="bg-white padding-sm margin-xs radius">计划名称</view>
				<view class="bg-white padding-sm margin-xs radius">码数</view>
				<view class="bg-white padding-sm margin-xs radius">期数</view>
				<view class="bg-white padding-sm margin-xs radius">中奖率</view>
			</view>

			<view class="flex solid-bottom padding-xs justify-between bg-white" v-for="(item,index) in tableList" :key="index">
				<view class="bg-white padding-sm margin-xs radius" @click="openPlanDetail">{{item.planName}}</view>
				<view class="bg-white padding-sm margin-xs radius">{{item.codeNum}}</view>
				<view class="bg-white padding-sm margin-xs radius">第{{item.nper}}期</view>
				<view class="bg-white padding-sm margin-xs radius text-red">{{item.rate}}%</view>
			</view>

		</scroll-view>

	</view>
</template>

<script>
	import IndexItem from '@/components/IndexItem.vue'
	export default {
		components: {
			IndexItem
		},
		data() {
			return {
				ItemList: [],
				select5:false,
				select4:false,
				select3:false,
				select2:false,
				select1:false,
				scrollTop: 0,
				tableList: [{
						'planName': '桃花计划',
						'codeNum': 5,
						'nper': 1,
						'rate': 100
					},
					{
						'planName': '桃花计划',
						'codeNum': 5,
						'nper': 1,
						'rate': 100
					},
					{
						'planName': '桃花计划',
						'codeNum': 5,
						'nper': 1,
						'rate': 100
					},
					{
						'planName': '桃花计划',
						'codeNum': 5,
						'nper': 1,
						'rate': 100
					},
					{
						'planName': '桃花计划',
						'codeNum': 5,
						'nper': 1,
						'rate': 100
					}, {
						'planName': '桃花计划',
						'codeNum': 5,
						'nper': 1,
						'rate': 100
					},
					{
						'planName': '桃花计划',
						'codeNum': 5,
						'nper': 1,
						'rate': 100
					},
					{
						'planName': '桃花计划',
						'codeNum': 5,
						'nper': 1,
						'rate': 100
					},
					{
						'planName': '桃花计划',
						'codeNum': 5,
						'nper': 1,
						'rate': 100
					}, {
						'planName': '桃花计划',
						'codeNum': 5,
						'nper': 1,
						'rate': 100
					},
					{
						'planName': '桃花计划',
						'codeNum': 5,
						'nper': 1,
						'rate': 100
					},
					{
						'planName': '桃花计划',
						'codeNum': 5,
						'nper': 1,
						'rate': 100
					},
					{
						'planName': '桃花计划',
						'codeNum': 5,
						'nper': 1,
						'rate': 100
					}, {
						'planName': '桃花计划',
						'codeNum': 5,
						'nper': 1,
						'rate': 100
					},
					{
						'planName': '桃花计划',
						'codeNum': 5,
						'nper': 1,
						'rate': 100
					},
					{
						'planName': '桃花计划',
						'codeNum': 5,
						'nper': 1,
						'rate': 100
					},
					{
						'planName': '桃花计划',
						'codeNum': 5,
						'nper': 1,
						'rate': 100
					},
				],
			}
		},
		methods: {
			openPlanDetail(){
				uni.navigateTo({
					url: '/pages/index/detail1'
				});
			},

		}
	}
</script>

<style lang="scss">
	.head-menu{
		position: fixed;
		width: 100%;
		z-index: 1024;
	}
	.item-list {
		position: absolute;
		top: 330rpx;

	}
	
	.Drop-down-Wrapper{
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
	.Drop-down{
		// display: none;
		position: absolute;
		z-index: 102;
		background: #fff;
		white-space: nowrap;
		left: -5px;
		margin-top: 14px;
		box-shadow: 0px 3px 9px 0px #555;
		.li {
			    // height: 20px;
			    padding: 10px 20px;
			    border-bottom: 1px solid #ccc;
			    list-style: none;
			    line-height: 20px;
		}
	}
</style>
