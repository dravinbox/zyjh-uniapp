<template>
	<view id="me" class="me_id">
		<view id="title" class="title_id">
			<view v-for="(item,index) in ['开奖提醒','计划设置','联系我们']" :class="pages==index?'you':''" @click="pageherf(index)">
				{{item}}
			</view>
		</view>
		<view id="main" class="main_id">
			<view id="switch" class="switch_ids">
				<view class="" style="white-space: nowrap;">
					请复制下方网址并保存，当app不可用时，便于下载最新版本。
				</view>
				<view>最新下载地址：www.shucy.top <button type="primary" style="float: right;height: 20px;color: #fff;font-size: 12px;line-height: 20px;background: green;">复制</button></view>
			</view>
			<view class="content">
				<view class="">
					在线反馈：
				</view>
				<textarea value="" placeholder="" class="textarea" />
				<input type="text" value="" placeholder="请留下您的联系方式" class="input"/>
				<view class="yanzhengma">
					<image src="../../static/logo-zy.png" mode=""></image>
					<input type="text" value="" placeholder="请输入验证码"/>
					<button type="primary">提交</button>
				</view>
				<view class="line" style="height: 10px;background: #efefef;"></view>
				<view class="lianxiwomen">
					联系我们：
					<view class="cart">
						<view class="view">微信：<span class="span">暂不公开</span> </view>
						<view class="view">公众号：<span class="span">暂不公开</span> </view>
						<view class="view">Q Q：<span class="span">暂不公开</span> </view>
						<view class="view">电话：<span class="span">暂不公开</span> </view>
						<view>邮箱：<span class="span">暂不公开</span> </view>
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
				PageCur: 'me',
				pages:'2',
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
			// padding: 10px;
			overflow: auto;
		padding-bottom: 50px;

			.switch_ids {
				// height: 40px;
				    height: 50px;
				    padding: 5px;
				background: #ddd;
				// display: flex;
				position: relative;
				font-size: 12px;
				    line-height: 20px;
				    color: green;
				    background: darkseagreen;
				// align-items: center;
			}
			.content{
				padding: 15px 10px;
				line-height: 35px;
				.textarea {
					background: #efefef;
				    width: 100%;
					padding: 10px;
					
				}
			
				.input{
					background: #efefef;
						margin-top: 10px;
						height: 40px;
						padding-left: 10px;
				}
				.yanzhengma{
					height: 60px;
					    display: flex;
					    align-items: center;
					    justify-content: space-between;
						image{
							height: 35px;
							    width: 80px;
						}
						input{
							    background: #efefef;
							    height: 35px;
							    width: 120px;
							    margin: 0 25px;
						}
						button{
							    height: 35px;
							    line-height: 35px;
							    width: 100px;
							    background: green;
						}
				}
				.lianxiwomen{
					padding-top: 20px;
					line-height: 25px;
					.cart{
						background: #efefef;
						display: flex;
						flex-wrap: wrap;
						padding: 20px;
						.view{
							width: 50%;
							.span{
								color: green;
								text-decoration: underline;
							}
						}
					}
				}
			}
		}
	}
</style>
