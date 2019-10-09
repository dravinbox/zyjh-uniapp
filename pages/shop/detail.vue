<template>
	<view id="movementDetail" class="movementDetail_id">
		<view id="title" class="title_id">
			<view class="return" @click="pageherf('/pages/shop/shop')"></view>时时彩
		</view>
		<view id="main" class="main_id">
			<view class="screen">
				<scroll-view scroll-x scroll-y="false" class="bg-white nav cate-bar">
					<view class="number">
						<view class="item" v-for="(item,index) in [20,30,60,90]" @click="qishu=index" :class="qishu==index?'you':'wu'">最近{{item}}期数</view>
					</view>
				</scroll-view>
				<scroll-view scroll-x scroll-y="false" class="nav cate-bar">
					<view class="click">
						<view class="item" v-for="(item,index) in ['第一位','第二位','第三位','第四位','第五位','第六位']" @click="wei=index" :class="wei==index?'you':''">{{item}}</view>
					</view>
				</scroll-view>
			</view>
			<view class="contents">
				<view class="tiaoxings">
					<view class="tiaoxing" v-for="(item,index) in data">
						<view style="padding:0 5px;">{{index}}</view>
						<view :style="'flex:'+item.tiao/big+' 0 0%;background:'+item.color"></view>
						<view style="padding:0 5px;">{{item.tiao}}次</view>
					</view>
				</view>
				<view class="table">
					<view class="header">第一位</view>
					<view class="body">
						<view class="column one">
							<view class="row">热号</view>
							<view class="row">温号</view>
							<view class="row">冷号</view>
						</view>
						<view class="column">
							<view class="row">12</view>
							<view class="row">12</view>
							<view class="row">345</view>
						</view>
					</view>
					<view class="footer">
						<p>20期以上为热号，2-3次为温号，1次或一下为冷号；</p>
						<p>20期以上为热号，2-3次为温号，1次或一下为冷号；</p>
						<p>20期以上为热号，2-3次为温号，1次或一下为冷号；</p>
						<p>20期以上为热号，2-3次为温号，1次或一下为冷号；</p>
					</view>
				</view>
			</view>
		</view>

		<!-- 底部 -->
<!-- 		<view class="cu-bar tabbar bg-white shadow foot">
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
		</view> -->
	</view>
</template>

<script>
	export default {
		data() {
			return {
				screen: [],
				data: [{
					tiao: 0,
					color: 'yellow'
				}, {
					tiao: 1,
					color: '#5d9df4'
				}, {
					tiao: 2,
					color: 'rgb(3,144,218)'
				}, {
					tiao: 3,
					color: 'rgb(72,72,72)'
				}, {
					tiao: 4,
					color: 'rgb(253,118,0)'
				}, {
					tiao: 5,
					color: 'rgb(79,51,246)'
				}, {
					tiao: 6,
					color: 'rgb(191,191,191)'
				}, {
					tiao: 7,
					color: 'rgb(252,40,2)'
				}, {
					tiao: 8,
					color: 'rgb(121,10,0)'
				}, {
					tiao: 9,
					color: 'rgb(3,191,0)'
				}],
				big: 9,
				wei: 0,
				qishu: 0,
				type: 1,
				PageCur: 'shop',
			}
		},
		computed: {

		},
		watch: {
			screen() {
				console.log(this.screen)
			}
		},
		methods: {
			pageherf(url) {
				this.$emit('pagechage',{pagecur:2,pagetab:2})
			},
			typetext(it) {
				var type = this.type
				var str = type == 1 ? it : type == 2 ? (it % 2 == 1 ? '单' : '双') : (it >= 5 ? '大' : '小')
				return str
			},
			typeclass(it) {
				var type = this.type
				var str = type == 1 ? 'number' : type == 2 ? (it % 2 == 1 ? 'dan' : 'shuang') : (it >= 5 ? 'dan' : 'shuang')
				return str
			},
			moduleclick(arr, claass) {
				var s = this.screen
				// 判断是否存在数组。
				if (arr.every((item, index) => s.indexOf(item) >= 0)) {
					if (!claass) {
						for (let k in arr) {
							s.splice(s.indexOf(arr[k]), 1)
						}
					}
					return true
				} else {
					if (!claass) {
						for (let k in arr) {
							s.push(arr[k])
						}
					}
					return false
				}
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
	.movementDetail_id {
		height: 100%;

		.title_id {
			text-align: center;
			border-bottom: 1px solid #bfbfbf;
			line-height: 50px;
			font-size: 17px;
			background: #f4f4f4;
			height: 50px;
			position: relative;

			.return {
				position: absolute;
				left: 17px;
				width: 16px;
				height: 16px;
				top: 17px;
				transform: rotateZ(-45deg);
				border-top: 2px solid #777;
				border-left: 2px solid #777;
			}
		}

		.main_id {
			height: calc(100% - 50px);
			// padding: 0 10px;
		padding-bottom: 50px;
			overflow: auto;
		}
	}
</style>


<style lang="scss">
	.main_id {
		.screen {
			// background: #fff;
			// padding: 20px 15px;

			.number {
				padding: 5px;
				border-bottom: 1px solid #ccc;

				.item {
					width: 25%;
					display: inline-block;
					height: 30px;
					margin: 0 5px;
					text-align: center;
					line-height: 30px;
					color: #555;
				}

				.you {
					background: #2ad0ea;
					color: #fff;
				}
			}

			.click {
				.item {
					width: 20%;
					height: 50px;
					color: #777;
					text-align: center;
					line-height: 50px;
					display: inline-block;
				}

				.you {
					color: #39B54A;
				}
			}
		}

		.contents {
			height: calc(100% - 101px);
			margin-top: 10px;
			background: #fff;
			
			.tiaoxings{
				.tiaoxing{
					margin: 6px 0;
					display: flex;
				    height: 20px;
				    line-height: 20px;
				    width: 70%;
					uni-view{
						height: 100%;
					}
				}
			}
			.table {

				.header {
					height: 30px;
					text-align: center;
					background: #cee8ea;
					line-height: 30px;

				}

				.body {
					display: flex;

					.column {
						flex: 1;

						.row {
							height: 30px;
							line-height: 30px;
							border-left: 1px solid #ccc;
							border-bottom: 1px solid #ccc;
							padding-left: 10px;
						}
					}

					.one {
						flex: 0 0 80px;
						text-align: right;

						.row {
							border-left: none !important;
							padding-right: 10px;
							padding-left: 0px !important;
						}
					}
				}

				.footer {
					background: #f4f4f4;
					padding: 10px;
					line-height: 30px;
				}
			}
		}
	}
</style>
