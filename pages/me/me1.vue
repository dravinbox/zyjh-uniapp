<template>
	<view id="me" class="me_id">
		<view id="title" class="title_id">
			<view v-for="(item,index) in ['开奖提醒','计划设置','联系我们']" :class="pages==index?'you':''" @click="pageherf(index)">
				{{item}}
			</view>
		</view>
		<view id="main" class="main_id">
			<view class="screen">
				<view v-for="(item,index) in ['时时彩','PK10','11选5','快三','快乐十分','更多']" @click="changetab(index)" class="item" :class="clickscreen==index?'you':''"><span>{{item}}</span></view>
			</view>
			<view class="list">
				<!-- <li v-for="(item,index) in 20">重庆时时彩 {{index}} -->
				<uni-collapse @change="change">
				    <uni-collapse-item title="标题文字" v-for="(item,index) in 20">
				        <uni-list style="background: #f4f4f4;">
							<view style="text-align: center;line-height: 30px;border-bottom: 1px solid #c8c7cc;" @tap="showModal" data-target="Modal" :data-index="index" :data-indexs="indexs" v-for="(items,indexs) in 3">标题文字{{items}}</view>
				        </uni-list>
				    </uni-collapse-item>
				</uni-collapse>
				
				<view class="cu-modal" :class="modalName=='Modal'?'show':''">
					<view class="cu-dialog">
						<view class="cu-bar bg-white justify-end">
							<view class="content">{{modalInit.title}}</view>
							<view class="action" @tap="hideModal">
								<text class="cuIcon-close text-red"></text>
							</view>
						</view>
						<view class="padding-xl">
							<view style="display: flex;height: 30px;line-height: 30px;margin: 8px 0;"><view style="padding: 0 5px;">码数:</view><input type="text" value="1" style="flex: 1;height: 30px;border:1px solid #ccc;text-align: left;padding-left: 10px;"></view>
							<view style="display: flex;height: 30px;line-height: 30px;margin: 8px 0;"><view style="padding: 0 5px;">期数:</view><input type="text" value="3" style="flex: 1;height: 30px;border:1px solid #ccc;text-align: left;padding-left: 10px;"></view>
							<view class="button" style="display: flex;justify-content: space-between;margin-top: 20px;">
								<button type="primary" @tap="hideModal" style="height: 30px;line-height: 30px;font-size: 13px;">取消</button>
								<button type="primary" style="height: 30px;line-height: 30px;font-size: 13px;">确定</button>
							</view>
						</view>
					</view>
				</view>
<!-- 					<label>
						<checkbox value="cb" checked="true" style="transform:scale(0.7);float:right" />
					</label> -->
				<!-- </li> -->
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
	import uniCollapse from "@/components/uni-collapse/uni-collapse.vue"
	import uniCollapseItem from "@/components/uni-collapse-item/uni-collapse-item.vue"
	import uniList from "@/components/uni-list/uni-list.vue"
	import uniListItem from "@/components/uni-list-item/uni-list-item.vue"
	export default {
		components: {uniCollapse,uniCollapseItem,uniListItem,uniList},
		data() {
			return {
				PageCur: 'me',
				modalName: null,
				modalInit:{
					title:'model 标题',
				},
				pages:'1',
				shadow: false,
				clickscreen: '0',
				checkbox: [{
					value: 'A',
					checked: true
				}, {
					value: 'B',
					checked: true
				}, {
					value: 'C',
					checked: false
				}]
			}
		},
		methods: {
			changetab(index){
				this.clickscreen=index
			},
			showModal(e) {
				console.log(e)
				this.modalName = e.currentTarget.dataset.target
				this.modalInit.title = `第${parseInt(e.currentTarget.dataset.index)+1}条里面的第${parseInt(e.currentTarget.dataset.indexs)+1}条`
				console.log(this.modalName)
			},
			hideModal(e) {
				this.modalName = null
			},
			change(e){
				console.log('change',e)
			},
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

		padding-bottom: 50px;
			.screen {
				height: 60px;
				display: flex;
				align-items: center;
				justify-content: space-between;
				border-bottom: 1px solid #ccc;

				.item {
					white-space: nowrap;
					display: inline-block;
					padding: 2px 10px;
					border-right: 1px solid #ccc;
					text-align: center;
					span{
						padding-bottom: 20px;
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
				height: calc(100% - 60px);
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
