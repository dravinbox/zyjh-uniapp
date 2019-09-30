<template>
	<view id="movement">
		<view id="title">走势</view>
		<view id="main">
			<div class="Wrapper" v-for="(items,ind) in datazzz">
				<p class="title">{{items.title}}</p>
				<view class="items">
					<view v-for="(item,index) in items.data" class="item" :style="index%3==1?'margin:auto 3.3%':''" @click="pagee">
						{{item}}-{{index%3}}
					</view>
				</view>
			</div>
		</view>
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
				datazzz: [{
					title: '时时彩',
					data: ['重庆时时彩', '腾讯', '北京', '11', '22']
				}, {
					title: '时时彩',
					data: ['重庆时时彩', '腾讯', '北京', '11', '22']
				}, {
					title: '时时彩',
					data: ['重庆时时彩', '腾讯', '北京', '11', '22']
				}, {
					title: '时时彩',
					data: ['重庆时时彩', '腾讯', '北京', '11', '22']
				}]
			}
		},
		methods: {
			pagee: function(e) {
				uni.navigateTo({
					url: '/pages/movement/detail'
				});
			},
			NavChange: function(e) {
				let PageCur = e.currentTarget.dataset.cur


				if (PageCur == 'me') {
					uni.navigateTo({
						url: '/pages/me/me'
					});
				} else if (PageCur == 'shop') {
					uni.navigateTo({
						url: '/pages/shop/shop'
					});
				} else if (PageCur == 'movements') {
					uni.navigateTo({
						url: '/pages/movement/movement'
					});
				} else {
					uni.navigateTo({
						url: '/pages/index/index'
					});
				}

			},
		}
	}
</script>

<style lang="scss">
	#movement {
		height: 100%;

		#title {
			text-align: center;
			border-bottom: 1px solid #bfbfbf;
			line-height: 50px;
			font-size: 17px;
			background: #f4f4f4;
			height: 50px;
		}

		#main {
			height: calc(100% - 50px);
			padding: 0 10px;
			overflow: auto;

			.Wrapper {
				width: 100%;
				border-bottom: 1px solid #ccc;
				padding: 20px 0;

				.title {
					font-size: 18px;
					font-weight: bold;
					margin-bottom: 5px;
				}

				.items {
					display: flex;
					flex-wrap: wrap;

					.item {
						width: 30%;
						margin: 5px 0;
						background: #fff;
						text-align: center;
						border: 1px solid #ddd;
						height: 40px;
						line-height: 40px;
					}
				}
			}
		}
	}
</style>
