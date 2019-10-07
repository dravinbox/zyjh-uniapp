<template>
	<view style="height: calc(100% + 50px);">
		<cu-custom bgColor="bg-white" :isBack="true">
			<block slot="content">教程</block>
		</cu-custom>
		
		<scroll-view scroll-x scroll-y="false" class="bg-white nav  " scroll-with-animation :scroll-left="scrollLeft">
			<view class="cu-item" :class="index==TabCur?'text-green cur':''" v-for="(item,index) in list" :key="index"
			 @tap="tabSelect" :data-id="index">
				{{item}}
			</view>
		</scroll-view>
	</view>
</template>

<script>
		
	export default {
		data(){
			return {
				list: [
					'重庆时时彩',
					'腾讯分分彩',
					'北京时时彩',
					'黑龙江时时彩',
				],
				TabCur: 0,
				scrollLeft: 0,
			}
		},
		methods:{
			tabSelect(e) {
				console.log(this.CustomBar)
				this.TabCur = e.currentTarget.dataset.id;
				this.scrollLeft = (e.currentTarget.dataset.id - 1) * 60
			},
		}
	}
</script>

<style>
</style>
