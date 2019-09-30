<template>
	<view>
		走势
		
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
	export default {
		data() {
			return {
				PageCur: 'movements',
			}
		},
		methods: {
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

<style>

</style>
