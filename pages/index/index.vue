<template>
	<view>
		<view id="title" class="flex justify-between align-center padding-sm">
			
				<image src="../../static/logo-zy.png" style="width: 30px;height: 30px;"></image>
				<view class="flex justify-end text-df padding-sm">
					<view class="cuIcon-favor" style="margin-right: 20rpx;" @click="openCollection">收藏</view>
					<view class="cuIcon-newshot" @click="openTutorial">教程</view>
				</view>
			
		</view>
	<!-- 	<cu-custom bgColor="bg-gray fix" >
			<block slot="content">
				<view class="flex justify-between">
					<image src="../../static/logo-zy.png" style="width: 30px;height: 30px;"></image>
					<image src="../../static/logo-zy.png" style="width: 30px;height: 30px;"></image>
				</view>
				
			</block>
		</cu-custom>	 -->
		
		
		<!-- 首页顶部菜单 -->
		<scroll-view scroll-x scroll-y="false" class="bg-white nav fixed cate-bar">
			<view class="flex text-center solid-bottom">
				<view class="cu-item flex-sub" :class="index==TabCur?'text-orange cur':''" v-for="(item,index) in oneCategory" :key="index"
				 @tap="tabSelect" :data-id="index">
					{{item}}
				</view>
			</view>
			<scroll-view scroll-x scroll-y="false" class="bg-white nav  " scroll-with-animation :scroll-left="scrollLeft">
				<view class="cu-item" :class="index==TabCur?'text-green cur':''" v-for="(item,index) in twoCategory" :key="index"
				 @tap="tabSelect" :data-id="index">
					{{item}}
				</view>
			</scroll-view>
		</scroll-view>

		<!-- 首页列表 -->
		<scroll-view scroll-y scroll-with-animation :scroll-top="scrollTop" class="item-list">
			<IndexItem v-for="(item,index) in indexItemList" :key="index" :title="item.title" :radioList="item.radioList"
			 :tableList="item.tableList"></IndexItem>

		</scroll-view>

		<!-- 底部 -->
		<view class="cu-bar tabbar bg-white shadow foot">
			<view class="action" :class="PageCur=='home'?'new-text-blue':'new-text-black'" @click="NavChange" data-cur="home">
				<view :class="PageCur=='home'?'cuIcon-homefill':'cuIcon-home'"></view>
				<view>首页</view>
			</view>
			<view class="action " :class="PageCur=='movements'?'new-text-blue':'new-text-black'" @click="NavChange" data-cur="movements">
				<view :class="PageCur=='movements'?'cuIcon-rank':'cuIcon-rankfill'"></view>
				<view>走势</view>
			</view>
			<view class="action " :class="PageCur=='shop'?'new-text-blue':'new-text-black'" @click="NavChange" data-cur="shop">
				<view :class="PageCur=='shop'?'cuIcon-cart':'cuIcon-cartfill'"></view>
				<view>购买</view>
			</view>
			<view class="action" :class="PageCur=='me'?'new-text-blue':'new-text-black'" @click="NavChange" data-cur="me">
				<view :class="PageCur=='me'?'cuIcon-myfill':'cuIcon-my'">
				</view>
				<view>我的</view>
			</view>
		</view>



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
				indexItemList: [{
						'title': '定位胆',
						'radioList': [
							'定胆个位',
							'定胆十位',
							'定胆百位',
							'定胆千位',
							'定胆万位',
						],
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
							},
						]
					},
					{
						'title': '定位胆',
						'radioList': [
							'个位大小',
							'十位大小',
							'百位大小',
							'千位大小',
							'万位大小',
						],
						tableList: [{
								'planName': '水星计划',
								'codeNum': 5,
								'nper': 1,
								'rate': 100
							},
							{
								'planName': '水星计划',
								'codeNum': 5,
								'nper': 1,
								'rate': 100
							},
							{
								'planName': '水星计划',
								'codeNum': 5,
								'nper': 1,
								'rate': 100
							},
							{
								'planName': '水星计划',
								'codeNum': 5,
								'nper': 1,
								'rate': 100
							},
							{
								'planName': '水星计划',
								'codeNum': 5,
								'nper': 1,
								'rate': 100
							},
						]
					}


				],

				PageCur: 'home',
				oneCategory: [
					'时时彩',
					'PK10',
					'11选5',
					'快三',
					'快乐十分',
					'更多'
				],
				twoCategory: [
					'重庆时时彩',
					'腾讯分分彩',
					'北京时时彩',
					'黑龙江时时彩',
				],
				TabCur: 0,
				title: 'Hello',
				scrollLeft: 0,
				scrollTop: 0,


			}
		},
		onLoad() {

		},
		methods: {
			openCollection(){
				uni.navigateTo({
					url: '/pages/index/collection'
				});
			},
			openTutorial(){
				uni.navigateTo({
					url: '/pages/index/tutorial'
				});
			},
			tabSelect(e) {
				console.log(this.CustomBar)
				this.TabCur = e.currentTarget.dataset.id;
				this.scrollLeft = (e.currentTarget.dataset.id - 1) * 60
			},
			NavChange: function(e) {
				let PageCur = e.currentTarget.dataset.cur
				

				if(PageCur=='me'){
					uni.navigateTo({
						url: '/pages/me/me'
					});
				}else if(PageCur=='shop'){
					uni.navigateTo({
						url: '/pages/shop/shop'
					});
				}else if(PageCur=='movements'){
					uni.navigateTo({
						url: '/pages/movement/movement'
					});
				}else {
					uni.navigateTo({
						url: '/pages/index/index'
					});
				}
				
			},


		}
	}
</script>

<style lang="scss">
	#title {
		text-align: center;
		border-bottom: 1px solid #bfbfbf;
		line-height: 50px;
		font-size: 17px;
		background: #f4f4f4;
		height: 50px;
		
		
		
	}

	.cate-bar{
		top: 50px;
		
	}
	.item-list {
		position: absolute;
		top: 280rpx;
		bottom: 90rpx;
	}
</style>
