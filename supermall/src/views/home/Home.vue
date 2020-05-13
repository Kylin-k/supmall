<template>
  <div id="home">
		<nav-bar class="home-nav">
			<div slot="center">购物街</div>
			<home-swiper :banners="banners"></home-swiper>
			<recommend-view :recommends="recommends"></recommend-view>
		</nav-bar>
	</div>
</template>

<script>
	import NavBar from 'components/navbar/NavBar.vue'
  import HomeSwiper from './childComps/HomeSwiper.vue'
	import RecommendView from './childComps/RecommendView.vue'
	
	import {getHomeMultidata} from 'network/home.js'
	
	export default {
   components:{
		 NavBar
	 },
	 data(){
		 return{
			 // result:null
			 banners:[],
			 recommends:[]
		 }
	 },
		created() {
			// 1.请求多个数据
			getHomeMultidata().then(res => {
				// this.result = res
				this.banners = res.data.banner.list,
				this.recommends = res.data.recommend.list
			})
		}
  }
</script>

<style scoped>
	.home-nav{
		background-color:hotpink;
		color: white;
	}
</style>
