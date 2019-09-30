<template>
	<view>
		<cu-custom bgColor="bg-white" :isBack="true">
			<block slot="content">定位胆</block>
		</cu-custom>
		
		<view class="head-menu">
			
		
		<view class=" bg-white flex justify-around align-center solid-bottom">
			<view>
				<view class="flex justify-between align-center ">

					<view class="flex justify-start align-center">
						<view>
							玩法：
						</view>
						<view class="bg-gray padding-xs margin-xs radius text-sm" @click="showModal" data-target="RadioModal">定胆个位<text
							 class="cuIcon-unfold"></text></view>
					</view>


					<view class="flex justify-start align-center">
						<view>
							中奖：
						</view>
						<view class="bg-gray padding-xs margin-xs radius text-sm" @click="showModal" data-target="RadioModal">不限<text
							 class="cuIcon-unfold"></text></view>
					</view>


				</view>
				<view class="flex justify-between align-center">
					<view class="flex justify-start align-center">
						<view>
							码数：
						</view>
						<view class="bg-gray padding-xs margin-xs radius text-sm" @click="showModal" data-target="RadioModal">5<text
							 class="cuIcon-unfold"></text></view>
					</view>
					<view class="flex justify-start align-center">
						<view>
							期数：
						</view>
						<view class="bg-gray padding-xs margin-xs radius text-sm" @click="showModal" data-target="RadioModal">3<text
							 class="cuIcon-unfold"></text></view>
					</view>
					<view class="flex justify-start align-center">
						<view>
							公式数：
						</view>
						<view class="bg-gray padding-xs margin-xs radius text-sm" @click="showModal" data-target="RadioModal">150<text
							 class="cuIcon-unfold"></text></view>
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
				<view class="bg-white padding-sm margin-xs radius">{{item.planName}}</view>
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

		}
	}
</script>

<style>
	.head-menu{
		position: fixed;
		width: 100%;
		z-index: 1024;
	}
	.item-list {
		position: absolute;
		top: 330rpx;

	}
</style>
