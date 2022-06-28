<template>
	<div id="home">
		<nav-bar class="home-nav"><div slot="center">购物车</div></nav-bar>
		<home-swiper :banners="banners"/>
		<recommend-view :recommends="recommends"/>
		<feature-view></feature-view>
		<tab-control class="tab-control" 
		:titles="['流行','精选','新款']"
		@tabClick="tabClick"/>
		<goods-list :goods="showGods"/>
		<p>888</p>
		<p>888</p>
		
	</div>
  
</template>

<script>
	//导航顶部购物车
	import NavBar from '@/components/common/navbar/NavBar.vue'
	//商品
	import TabControl from '@/components/content/tabControl/TabControl.vue'
	
	//轮播
	import HomeSwiper from './childComps/HomeSwiper.vue'
	import RecommendView from './childComps/RecommendView.vue'
	import FeatureView from './childComps/FeatureView.vue'
	//goods
	import GoodsList from '@/components/content/goods/GoodsList'
	import GoodsListItem from '@/components/content/goods/GoodsListItem'
	//网络请求
	//export function getHomeMultidata(){}导出用  用 {} 包裹
	import {getHomeMultidata, getHomeGoods} from "@/network/home.js"
	
	export default{
		components:{
			NavBar,
			HomeSwiper,
			RecommendView,
			FeatureView,
			TabControl,
			getHomeGoods,
			GoodsList,
			GoodsListItem
		},
		data(){
			return {
				result: null,
				banners: [],
				recommends: [],
				goods:{
					'pop': {page: 0, list: []},
					'new': {page: 0, list: []},
					'sell': {page: 0, list: []}
				},
				currentType: 'pop'
			}
		},
		computed:{
			showGods(){
				return  this.goods[this.currentType].list
			}
		},
		created(){
			//1、请求多个数据
			this.getHomeMultidata()
			//2、请求商品数据
			this.getHomeGoods('pop')
			this.getHomeGoods('new')
			this.getHomeGoods('sell')
		},
		methods:{
			//数据请求方法
			tabClick(index){
				console.log(index);
				switch (index){
					case 0:
						this.currentType = 'pop'
						break;
					case 1:
						this.currentType = 'new'
						break;
					case 2:
						this.currentType = 'sell'
						break;
				}
			},
			//网络请求方法
			getHomeMultidata(){
				getHomeMultidata().then(res => {
					//this.result = res;
					this.banners = res.data.banner.list;
					this.recommends = res.data.recommend.list;
					//console.log(res);
				})
			},
			getHomeGoods(type){
				//请求数据加1
				const page = this.goods[type].page + 1
				getHomeGoods(type, page).then(res => {
					console.log(res);
					this.goods[type].list.push(...res.data.list)
					this.goods[type].page += 1
				})
			}
		}
	}
</script>

<style>
	.home-nav{
		background-color: var(--color-tint);
		color: aliceblue;
		
		position: fixed;
		left: 0;
		right: 0;
		top: 0;
		z-index: 9;
	}
	#home{
		padding-top: 44px;
	}
	.tab-control{
		position: sticky;
		top: 44px;
		z-index: 9;
	}
</style>