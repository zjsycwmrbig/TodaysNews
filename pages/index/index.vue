<template>
	<div class="content">
		
		<div class="subpage">
			<hot-compoment-vue v-if="routerIndex == 'hot'"></hot-compoment-vue>
			<later-compoment-vue v-if="routerIndex == 'later'"></later-compoment-vue>
			<about-compoment-vue v-show="routerIndex == 'about'"></about-compoment-vue>
		</div>
		
		<div class="nav">
			<div class="hot nav-item" :class="routerIndex=='hot' ? 'nav-index' : ''" @click="routerIndex = 'hot'">
				<uni-icons type="paperplane-filled" size="30" :color="routerIndex=='hot'?'yellow':'white'"></uni-icons>
				<span>
					今日热榜
				</span>
			</div>
			<div class="later nav-item" :class="routerIndex=='later' ? 'nav-index' : ''" @click="routerIndex = 'later'">
				<uni-icons type="star-filled" size="30" :color="routerIndex=='later'?'yellow':'white'"></uni-icons>
				<span>
					稍后再读
				</span>
			</div>
			<div class="about nav-item" :class="routerIndex=='about' ? 'nav-index' : ''" @click="routerIndex = 'about'">
				<uni-icons type="person-filled" size="30" :color="routerIndex=='about'?'yellow':'white'"></uni-icons>
				<span>
					关于我们
				</span>
			</div>
		</div>
	</div>
</template>

<script>
	import hotCompomentVue from '../subpage/hot-compoment.vue'
	import laterCompomentVue from '../subpage/later-compoment.vue'
	import aboutCompomentVue from '../subpage/about-compoment.vue'
	export default {
		data() {
			return {
				title: 'Hello',
				routerIndex: 'hot',
			}
		},
		components:{
			hotCompomentVue,
			laterCompomentVue,
			aboutCompomentVue
		},
		onLoad() {
			
		},
		methods: {

		}
	}
</script>

<style>
	.content {
		height: 100vh;
		width: 100vw;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: space-between;
	}	
	.nav{
		display: flex;
		justify-content: space-evenly;
		height: 10%;
		width: 100%;
		background-color: #805fe5;
		color: aliceblue;

	}
	
	.nav-item{
		display: flex;
		justify-content: center;
		align-items: center;
	}
	
	.nav-index{
		color: yellow;
		font-weight: 1000;
	}

	.subpage{
		width: 100%;
	}
</style>
