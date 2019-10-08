<template>
	<view style="height: calc(100% + 50px);">
		<cu-custom bgColor="bg-white" :isBack="true">
			<block slot="content">定位胆</block>
		</cu-custom>

		<view class="head-menu">
			<view class=" bg-white solid-bottom" style="border-bottom: 1px solid #ccc;">
				<view class="flex justify-between align-center" style="padding: 0 20px;">
					<view class="flex justify-start align-center">
						<view>
							玩法：
						</view>
						<view class="bg-gray padding-xs margin-xs radius text-sm Drop-down-Wrapper" @click="select1 = !select1" data-target="RadioModal">
							定胆个位
							<text class="cuIcon-unfold"></text>
							<view class="mask" v-show="select1" @click.stop="select1 = !select1"></view>
							<view class="Drop-down" v-show="select1">
								<li class="li">定位个胆</li>
								<li class="li">定位个胆</li>
								<li class="li">定位个胆</li>
								<li class="li">定位个胆</li>
								<li class="li">定位个胆</li>
							</view>
						</view>
					</view>
					<view class="flex justify-start align-center">
						<view>
							码数：
						</view>
						<view class="bg-gray padding-xs margin-xs radius text-sm Drop-down-Wrapper" @click="select2 = !select2" data-target="RadioModal">5<text
							 class="cuIcon-unfold"></text>
							<view class="mask" v-show="select2" @click.stop="select2 = !select2"></view>
							 <view class="Drop-down" v-show="select2">
							 	<li class="li">码数</li>
							 	<li class="li">码数</li>
							 	<li class="li">码数</li>
							 	<li class="li">码数</li>
							 	<li class="li">码数</li>
							 </view>
							</view>
					</view>
					<view class="flex justify-start align-center">
						<view>
							期数：
						</view>
						<view class="bg-gray padding-xs margin-xs radius text-sm Drop-down-Wrapper" @click="select3 = !select3" data-target="RadioModal">3<text
							 class="cuIcon-unfold"></text>
							 
							 <view class="mask" v-show="select3" @click.stop="select3 = !select3"></view>
							 <view class="Drop-down" v-show="select3">
							 	<li class="li">5</li>
							 	<li class="li">5</li>
							 	<li class="li">5</li>
							 	<li class="li">5</li>
							 	<li class="li">5</li>
							 </view>
							 </view>
					</view>
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

			<view style="height: 60px;">
				<image src="../../static/logo-zy.png" mode="" style="width: 100%;height: 100%;"></image>
			</view>
		</view>


		<!-- 首页列表 -->
		<scroll-view scroll-y scroll-with-animation :scroll-top="scrollTop" class="item-list" style="height: calc(100% - 168px - 144px);">


			<view class="flex justify-between bg-white" style="margin-bottom: 10px;">
				<view class="bg-white padding-sm margin-xs radius">计划期间</view>
				<view class="bg-white padding-sm margin-xs radius">最终截至</view>
				<view class="bg-white padding-sm margin-xs radius">计划结果</view>
				<view class="bg-white padding-sm margin-xs radius">当前预期值</view>
			</view>

			<view class="flex solid-bottom padding-xs justify-between bg-white" v-for="(item,index) in tableList" :key="index">
				<view class="padding-sm margin-xs radius">{{item.planName}}{{tableList.length}}</view>
				<view class="padding-sm margin-xs radius">第{{item.codeNum}}期{{index}}</view>
				<view class="padding-sm margin-xs radius" :style="item.nper.length>1?'color:blue;':''">{{item.nper.join()}}</view>
				<view class="padding-sm margin-xs radius" :style="item.nper.length<=1?'color:#ff8000;':'color:blue;'">{{item.rate.join()}}</view>
			</view>

		</scroll-view>

		<view class="footer" style="position: fixed;bottom: 0;background: #fff;width: 100%;">
			<view class="card" style="background: #a0a0a0;color: #fff;padding-left: 10px;line-height: 22px;font-size: 12px;">
				<view>已完成16个周期，正确率100.0%，错误0个。</view>
				<view>已完成16个周期，正确率100.0%，错误0个。</view>
			</view>
			<view class="input flex" style="">
				<view class="" style="height: 100px; padding: 10px;flex:1;">
					<textarea value="1,2,5,6,7" placeholder="" style="border-radius: 3px;padding: 5px;border:1px solid #ccc;width: 100%;height: 100%;" />
					</view>
				<view class="flex buttons" style="width:80px;flex-wrap: wrap;align-items: center;padding: 10px;">
					<button style="width: 100%;height: 30px;line-height: 30px;font-size: 12px;">5组</button>
					<button type="primary" style="width: 100%;height: 30px;font-size: 12px;line-height: 30px;">复制</button>
				</view>
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
				ItemList: [],
				select1:false,
				select2:false,
				select3:false,
				scrollTop: 0,
				tableList: [{
					'planName': '001-003',
					'codeNum': 5,
					'nper': ['进行中'],
					'rate': [1, 4, 8, 3, 2],
				}, {
					'planName': '001-003',
					'codeNum': 5,
					'nper': ['9', '4', 8, 3, 2],
					'rate': [1, 4, 8, 3, 2],
				}, {
					'planName': '001-003',
					'codeNum': 5,
					'nper': ['9', '4', 8, 3, 2],
					'rate': [1, 4, 8, 3, 2],
				}, {
					'planName': '001-003',
					'codeNum': 5,
					'nper': ['9', '4', 8, 3, 2],
					'rate': [1, 4, 8, 3, 2],
				},{
					'planName': '001-003',
					'codeNum': 5,
					'nper': ['9', '4', 8, 3, 2],
					'rate': [1, 4, 8, 3, 2],
				},{
					'planName': '001-003',
					'codeNum': 5,
					'nper': ['9', '4', 8, 3, 2],
					'rate': [1, 4, 8, 3, 2],
				},{
					'planName': '001-003',
					'codeNum': 5,
					'nper': ['9', '4', 8, 3, 2],
					'rate': [1, 4, 8, 3, 2],
				},{
					'planName': '001-003',
					'codeNum': 5,
					'nper': ['9', '4', 8, 3, 2],
					'rate': [1, 4, 8, 3, 2],
				},{
					'planName': '001-003',
					'codeNum': 5,
					'nper': ['9', '4', 8, 3, 2],
					'rate': [1, 4, 8, 3, 2],
				},{
					'planName': '001-003',
					'codeNum': 5,
					'nper': ['9', '4', 8, 3, 2],
					'rate': [1, 4, 8, 3, 2],
				},{
					'planName': '001-003',
					'codeNum': 5,
					'nper': ['9', '4', 8, 3, 2],
					'rate': [1, 4, 8, 3, 2],
				},{
					'planName': '001-003',
					'codeNum': 5,
					'nper': ['9', '4', 8, 3, 2],
					'rate': [1, 4, 8, 3, 2],
				},{
					'planName': '001-003',
					'codeNum': 5,
					'nper': ['9', '4', 8, 3, 2],
					'rate': [21, 4, 8, 3, 2],
				}, ],
			}
		},
		methods: {
			toggleEl(e){
				this.select1 = !this.select1;
				console.log(e)
			}
		}
	}
</script>

<style lang="scss">
	.head-menu {
		/* position: fixed; */
		width: 100%;
		/* z-index: 1024; */
	}

	.item-list {
		/* position: absolute; */
		/* top: 330rpx; */

	}
	.Drop-down-Wrapper{
		position: relative;
		.mask {
			position: fixed;
			background: red;
			width: 100%;
			height: 100%;
			top: 0;
			left: 0;
			z-index: 9999;
			opacity: 0;
		}
	}
	.Drop-down{
		// display: none;
		position: absolute;
		z-index: 102;
		background: #fff;
		white-space: nowrap;
		left: -5px;
		margin-top: 14px;
		box-shadow: 0px 3px 9px 0px #555;
		.li {
			    height: 20px;
			    padding: 10px 20px;
			    border-bottom: 1px solid #ccc;
			    list-style: none;
			    line-height: 20px;
		}
	}
</style>
