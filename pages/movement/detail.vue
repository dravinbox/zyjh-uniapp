<template>
	<view id="movementDetail">
		<view id="title"> <view class="return" @click="pageherf('/pages/movement/movement')"></view>时时彩</view>
		<view id="main">
			<view class="screen">
				<scroll-view scroll-x scroll-y="false" class="bg-white nav cate-bar">
					<view class="number">
						<view class="item" v-for="(item,index) in 10" @click="screen.indexOf(item-1)>=0?screen.splice(screen.indexOf(item-1),1):screen.push(item-1)"
						 :class="screen.indexOf(item-1)>=0?'you':'wu'">{{item-1}}</view>
					</view>
				</scroll-view>
				<view class="click">
					<view class="item" @click="moduleclick([5,6,7,8,9])" :class="moduleclick([5,6,7,8,9],true)?'you':'wu'">大</view>
					<view class="item" @click="moduleclick([0,1,2,3,4])" :class="moduleclick([0,1,2,3,4],true)?'you':'wu'">小</view>
					<view class="item" @click="moduleclick([1,3,5,7,9])" :class="moduleclick([1,3,5,7,9],true)?'you':'wu'">单</view>
					<view class="item" @click="moduleclick([0,2,4,6,8])" :class="moduleclick([0,2,4,6,8],true)?'you':'wu'">双</view>
					<view class="clear" @click="screen=[]">清除</view>
				</view>
			</view>
			<view class="contents">
				<view class="title">
					<view class="item datenumber">期数</view>
					<view class="item date">日期</view>
					<view class="item Number" @click="type=1"><span :class="type==1?'you':''">号码</span></view>
					<view class="item SingleDouble" @click="type=2"><span :class="type==2?'you':''">单双</span></view>
					<view class="item Size" @click="type=3"><span :class="type==3?'you':''">大小</span></view>
				</view>
				<view class="content">
					<view class="DataWrapper" v-for="item in data">
						<view class="datenumber">{{item.datenumber}}</view>
						<view class="date">{{item.date}}</view>
						<view class="Content">
							<view class="item" v-for="it in item.Number" :class="screen.indexOf(it)>=0 || screen.length==0?typeclass(it):'wu'">{{typetext(it)}}</view>
						</view>
					</view>
				</view>
			</view>
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
				screen: [],
				type: 1,
				PageCur: 'movements',
				data: [{
					datenumber: '9301073',
					date: '17:53',
					Number: [5, 0, 8, 5, 2]
				}, {
					datenumber: '9301073',
					date: '17:53',
					Number: [5, 0, 8, 5, 2]
				}, {
					datenumber: '9301073',
					date: '17:53',
					Number: [5, 0, 8, 5, 2]
				}, {
					datenumber: '9301073',
					date: '17:53',
					Number: [5, 0, 8, 5, 2]
				}, {
					datenumber: '9301073',
					date: '17:53',
					Number: [5, 0, 8, 5, 2]
				}, {
					datenumber: '9301073',
					date: '17:53',
					Number: [5, 0, 8, 5, 2]
				}, {
					datenumber: '9301073',
					date: '17:53',
					Number: [5, 0, 8, 5, 2]
				}, {
					datenumber: '9301073',
					date: '17:53',
					Number: [5, 0, 8, 5, 2]
				}, {
					datenumber: '9301073',
					date: '17:53',
					Number: [5, 0, 8, 5, 2]
				}, {
					datenumber: '9301073',
					date: '17:53',
					Number: [5, 0, 8, 5, 2]
				}]
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
			pageherf(url){
				uni.navigateTo({url: url});
			},
			typetext(it){
				var type = this.type
				var str = type==1?it:type==2?(it%2==1?'单':'双'):(it>=5?'大':'小')
				return str
			},
			typeclass(it){
				var type = this.type
				var str = type==1?'number':type==2?(it%2==1?'dan':'shuang'):(it>=5?'dan':'shuang')
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
	#movementDetail {
		height: 100%;

		#title {
			text-align: center;
			border-bottom: 1px solid #bfbfbf;
			line-height: 50px;
			font-size: 17px;
			background: #f4f4f4;
			height: 50px;
			position: relative;
			.return{
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

		#main {
			height: calc(100% - 50px);
			// padding: 0 10px;
			overflow: auto;
		}
	}
</style>


<style lang="scss">
	#main {
		.screen {
			background: #fff;
			padding: 20px 15px;

			.number {
				.item {
					width: 30px;
					display: inline-block;
					height: 30px;
					margin: 0 5px;
					text-align: center;
					line-height: 30px;
				}

				.you {
					background: #39B54A;
				}

				.wu {
					background: #eee;
				}
			}

			.click {
				.item {
					width: 40px;
					height: 30px;
					background: #eeeeee;
					margin: 15px 5px 0px 5px;
					text-align: center;
					line-height: 30px;
					border-radius: 2px;
					display: inline-block;
				}

				.you {
					background: #39B54A;
				}

				.wu {
					background: #eee;
				}

				.clear {
					width: 70px;
					height: 30px;
					background: #fff;
					margin: 15px 5px 0px 5px;
					text-align: center;
					line-height: 28px;
					display: inline-block;
					float: right;
					border: 2px solid #ddd;
				}
			}
		}

		.contents {
			overflow: auto;
			height: calc(100% - 125px);
			margin-top: 10px;
			background: #fff;

			.title {
				height: 50px;
				border-bottom: 1px solid #ddd;
				display: flex;
				align-items: center;
				justify-content: space-around;

				>.item {
					width: calc(100% / 5);
					text-align: center;
					height: 30px;
					line-height: 30px;

					>span {
						font-weight: bold;
					}

					>.you {
						color: #39b54a;
						border-bottom: 2px solid #39b54a;
						padding: 15px 10px;
					}
				}

				.date {
					border-right: 1px solid #ddd;
				}
			}

			.content {
				.DataWrapper {
					height: 50px;
					border-bottom: 1px solid #ddd;
					display: flex;
					align-items: center;
					justify-content: space-around;
					flex: 12;
					text-align: center;

					.datenumber {
						flex: 1;
						width: 20%;
					}

					.date {
						flex: 1;
						width: 20%;
					}

					.Content {
						flex: 3;
						width: 60%;
						display: flex;
						justify-content: space-around;

						.item {
							width: 25px;
							height: 25px;
							border-radius: 50%;
							color: #fff;
							line-height: 25px;
						}

						.number{
							background: #39B54A;
						}
						.dan{
							background: red;
						}
						.shuang{
							background: #aaa;
						}

						.wu {
							background: #eee;
						}
					}
				}
			}
		}
	}
</style>
