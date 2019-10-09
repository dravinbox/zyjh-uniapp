<template>
	<view class="me_id">
		<view class="title_id">
			<view v-for="(item,index) in ['开奖提醒','计划设置','联系我们']" :class="pages==index?'you':''" @click="pageherf(index)">
				{{item}}
			</view>
		</view>
		<view class="main_id">
			<view class="switch_id">
				<span style="padding:0px 10px">总开关</span>
				<switch @change="SetShadow" :class="shadow?'checked':''" color="#39B54A"></switch>
				<view class="" style="position: absolute;right: 10px;">
					
					<checkbox-group>
						<label>
							<checkbox :class="checkbox[0].checked?'checked':''" :checked="checkbox[0].checked" value="A" @click="checkbox[0].checked = !checkbox[0].checked" style="transform:scale(0.7);"></checkbox>震动</label>
						<label>
							<checkbox :class="checkbox[1].checked?'checked':''" :checked="checkbox[1].checked" value="A" @click="checkbox[1].checked = !checkbox[1].checked" style="transform:scale(0.7);"></checkbox>响铃</label>
					</checkbox-group>
				</view>
			</view>
			<view class="screen">
				<view v-for="(item,index) in ['时时彩','PK10','11选5','快三','快乐十分','更多']" @click="clickscreen=index" class="item" :class="clickscreen==index?'you':''"><span>{{item}}</span></view>
			</view>
			<view class="list">
				<li v-for="item in checkboxS">重庆时时彩 <label>
						<checkbox :class="item.checked?'checked':''" :checked="item.checked" :value="item.value" @click="item.checked = !item.checked" style="transform:scale(0.7);float:right;"></checkbox>
						</label>
						</li>
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
				PageCur: 'me',
				pages:'0',
				shadow: false,
				clickscreen: '0',
				cb:false,
				checkbox: [{
					value: 'A',
					checked: true
				}, {
					value: 'B',
					checked: false
				}, {
					value: 'C',
					checked: false
				}],
				checkboxS:[{
					value: '1',
					checked: false
				}, {
					value: '2',
					checked: true
				}, {
					value: '3',
					checked: false
				}, {
					value: '4',
					checked: true
				}, {
					value: '5',
					checked: false
				}, {
					value: '6',
					checked: true
				}]
			}
		},
		methods: {
			pageherf(index){
				if(index==0){
					this.$emit('pagechage',{pagecur:3,pagetab:3})
				}else if(index == 1){
					this.$emit('pagechage',{pagecur:6,pagetab:3})
				}else if(index == 2){
					this.$emit('pagechage',{pagecur:7,pagetab:3})
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
	.me_id {
		height: 100%;

		.title_id {
			text-align: center;
			border-bottom: 1px solid #bfbfbf;
			line-height: 50px;
			font-size: 17px;
			background: #f4f4f4;
			height: 50px;
			display: flex;
			justify-content: space-around;
			padding: 0 60px;
			font-size: 14px;

			.you {
				font-size: 17px;
				font-weight: bold;
			}
		}

		.main_id {
			height: calc(100% - 50px);
			background: #fff;
			padding: 10px;
			overflow: auto;

			.switch_id {
				height: 40px;
				background: #ddd;
				display: flex;
				align-items: center;
				position: relative;
			}

			.screen {
				height: 80px;
				display: flex;
				align-items: center;
				justify-content: space-between;

				.item {
					display: inline-block;
					padding: 2px 10px;
					border-right: 1px solid #ccc;
					// margin-top: 20px;
					// min-width: 16%;
					text-align: center;

					// flex: 1;
					span {
						padding-bottom: 10px;
					}
				}

				.you {
					span {
						color: #39B54A;
						border-bottom: 2px solid #39B54A;
					}
				}
			}

			.list {
				height: calc(100% - 110px);
				overflow: auto;

				>li {
					list-style: none;
					height: 40px;
					border-bottom: 1px solid #ccc;
					line-height: 40px;
				}
			}
		}
	}
</style>
