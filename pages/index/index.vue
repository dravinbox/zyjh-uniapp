<template>
	<view>

		<!-- 首页顶部菜单 -->
		<scroll-view scroll-x scroll-y="false" class="bg-white nav fixed">
			<view class="flex text-center">
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
			<IndexItem></IndexItem>
			<IndexItem></IndexItem>
			<IndexItem @tap="showModal"></IndexItem>
		</scroll-view>

		<!-- 首页底部 -->
		<view class="cu-bar tabbar bg-white shadow foot">
			<view class="action" :class="PageCur=='dynamic'?'new-text-blue':'new-text-black'" @click="NavChange" data-cur="dynamic">
				<view :class="PageCur=='dynamic'?'cuIcon-homefill':'cuIcon-home'"></view>
				<view>首页</view>
			</view>
			<view class="action " :class="PageCur=='release'?'new-text-blue':'new-text-black'" @click="NavChange" data-cur="release">
				<view :class="PageCur=='release'?'cuIcon-rank':'cuIcon-rankfill'"></view>
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
				PageCur: 'dynamic',
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
			
			tabSelect(e) {
				this.TabCur = e.currentTarget.dataset.id;
				this.scrollLeft = (e.currentTarget.dataset.id - 1) * 60
			},
			NavChange: function(e) {
				this.PageCur = e.currentTarget.dataset.cur

				// if(PageCur=='me'){
				// 	uni.navigateTo({
				// 		url: '../category/personal?classItem=me'
				// 	});
				// }else if(PageCur=='release'){
				// 	uni.navigateTo({
				// 		url: '../category/release?classItem=release'
				// 	});
				// }
			},


		}
	}
</script>

<style>
	.item-list {
		position: absolute;
		top: 180upx;
		bottom: 90upx;
	}
</style>
