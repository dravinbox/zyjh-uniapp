<template>
	<view style="height: 100%">
		<view style="height: calc(100% - 50px); width: 100%;overflow: auto;">
			<me v-if="pagecur==pagevar.me" @pagechage="pagechage"></me>
			<index v-if="pagecur==pagevar.index" @pagechage="pagechage"></index>
			<movement v-if="pagecur==pagevar.movement" @pagechage="pagechage"></movement>
			<shop v-if="pagecur==pagevar.shop" @pagechage="pagechage"></shop>
			<movementDetail v-if="pagecur==pagevar.movementDetail" @pagechage="pagechage"></movementDetail>
			<shopDetail v-if="pagecur==pagevar.shopDetail" @pagechage="pagechage"></shopDetail>
			<me1 v-if="pagecur==pagevar.me1" @pagechage="pagechage"></me1>
			<me2 v-if="pagecur==pagevar.me2" @pagechage="pagechage"></me2>
		</view>
		<view class="cu-bar tabbar bg-white shadow foot">
			<view class="action" :class="pagetab==pagevar.index?'new-text-blue':'new-text-black'" @click="NavChange(pagevar.index)" data-cur="home">
				<view :class="pagetab==pagevar.index?'cuIcon-homefill':'cuIcon-home'"></view>
				<view>首页</view>
			</view>
			<view class="action " :class="pagetab==pagevar.movement?'new-text-blue':'new-text-black'" @click="NavChange(pagevar.movement)" data-cur="movements">
				<view :class="pagetab==pagevar.movement?'cuIcon-rank':'cuIcon-rankfill'"></view>
				<view>走势</view>
			</view>
			<view class="action " :class="pagetab==pagevar.shop?'new-text-blue':'new-text-black'" @click="NavChange(pagevar.shop)" data-cur="shop">
				<view :class="pagetab==pagevar.shop?'cuIcon-cart':'cuIcon-cartfill'"></view>
				<view>购买</view>
			</view>
			<view class="action" :class="pagetab==pagevar.me?'new-text-blue':'new-text-black'" @click="NavChange(pagevar.me)" data-cur="me">
				<view :class="pagetab=='me'?'cuIcon-myfill':'cuIcon-my'">
				</view>
				<view>我的</view>
			</view>
		</view>
	</view>
</template>

<script>
	import me from '@/pages/me/me.vue'
	import index from '@/pages/index/index.vue'
	import movement from '@/pages/movement/movement.vue'
	import shop from '@/pages/shop/shop.vue'
	import movementDetail from '@/pages/movement/detail.vue'
	import shopDetail from '@/pages/shop/detail.vue'
	import me1 from '@/pages/me/me1.vue'
	import me2 from '@/pages/me/me2.vue'
	export default {
		data() {
			return {
				pagecur:0,//展示的内容
				pagetab:0,//被选中的tab
				pagevar:{
					index:0,
					movement:1,
					shop:2,
					me:3,
					movementDetail:4,
					shopDetail:5,
					me1:6,
					me2:7
				}
			}
		},
		components: {
			me,
			index,
			movement,
			shop,
			movementDetail,
			shopDetail,
			me2,
			me1
		},
		created() {
			if(this.$route.query.pageNum){
				this.pagecur = this.$route.query.pageNum
			}
		},
		methods: {
			NavChange(e){
				this.pagecur = e
				this.pagetab = e
			},
			pagechage(e){
				this.pagecur = e.pagecur
				this.pagetab = e.pagetab
			}
		}
	}
</script>

<style>

</style>
