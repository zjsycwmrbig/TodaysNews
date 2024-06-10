<template>
	<div class="later-root">
		<div class="later-title">
			<span>稍后再看</span>
		</div>

		<scroll-view class="later-body" scroll-y="true" v-if="laterData.length != 0">
			<topic-item-vue v-for="(item,index) in laterData" :key="index" :topic="item" type="later" />
		</scroll-view>
		<div class="empty" v-else />
	</div>
</template>

<script>
import topicItemVue from '../compoment/topic-item.vue'
	export default{
		data(){
			return{
				laterData:[],
			}
		},
		components:{
			topicItemVue
		},
		created() {
			this.laterData = uni.getStorageSync('later-data')
		},
		methods:{
			refreshLaterData(){
				this.laterData = uni.getStorageSync('later-data')
			}
		}
		
	}
</script>

<style>
.later-root{
	display: flex;
	flex-direction: column;

}
.later-title{
	padding: 2px;
		width: 100%;
		height: 10%;
		background-color: #f2eeff;
		color: #805fe5;
		display: flex;
		justify-content: center;
		align-items: center;
		font-size: 5vh;
		font-weight: 1000;
}
.later-body{
	width: 100%;
	height: 80vh;
}

.empty{
	margin-top: 20vh;
	height: 40vh;
	background-image: url("~@/static/empty.png") ;
	background-size: 100%;
	background-repeat: no-repeat;
}
</style>