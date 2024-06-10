<template>
	<div class="hot-root">
		<div class="topic-box" :class="checkoutTopic == true ?'topic-box-active' : ''">
			
			<div class="up">
				<div class="topic-close" @click="checkoutTopic = false">
					<span>
						×
					</span>
				</div>

				<div class="logo"/>
				
				<div class="app-name">
					<span>今日热榜</span>
				</div>

				<div class="desc">
					<span>你感兴趣的都在这里</span>
				</div>
			</div>
			<scroll-view  class="down"  scroll-y="true" >
				<div v-for="(item,index) in topicsData" :key="index" class="topic-item" @click="checkToTopic(item)" :class="item.name ==  selectedTopic.name ? 'topic-item-active' : ''">
					{{ item.name }}
				</div>	
			</scroll-view>
		</div>

		<div class="hot-title">
			<div class="topic-open" @click="checkoutTopic = true">
				<span>
					☰
				</span>
			</div>
			<span>
				{{ selectedTopic.name }}
			</span>
		</div>
		
		<scroll-view class="body" scroll-y="true">
			<topic-item-vue v-for="(item,index) in hotNews" :key="index" :topic="item"/>
		</scroll-view>

		
	</div>
</template>

<script>
import topics from '../../resource/topics';
import topicItemVue from '../compoment/topic-item.vue';
	export default {
		data() {
			return {
				title: 'Hello',
				hotNews:[
				],
				topicsData:topics.data,
				checkoutTopic:false,
				selectedTopic:null
			}
		},
		components:{
			topicItemVue
		},
		created() {
			// 默认第一个
			this.checkToTopic(this.topicsData[0])
		},
		methods: {
			addCache(){
				let laterData =  uni.getStorageSync("later-data")
				console.log(laterData)
				laterData.push("1")
				uni.setStorageSync("later-data",laterData)
			},
			checkToTopic(item){
				this.selectedTopic = item
				this.checkoutTopic = false
				// 请求热榜数据 填充
				uni.request({
					url: item.url,
					success: (res) => {
						this.hotNews = res.data.data
					}
				});
			}
		}
	}
</script>

<style>
	.hot-root {
		position: relative;
		width: 100%;
		height: 100%;
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		align-items: center;
	}

	.topic-box {
		position: fixed;
		width: 70%;
		height: 100%;
		top: 0;
		left: -100vw;
		transition: all 0.5s ease;
		z-index: 100;
		background-color: #fff;
	}

	.hot-title {
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

	.body{
		width: 100%;
		height: 80vh;
	}

	.logo{
		width: 30vw;
		height: 30vw;
		background-image: url('@/static/logo.jpg');
		background-size: cover;
		border-radius: 3px;
	}

	.topic-box-active{
		left: 0;
	}


	.topic-close {
		color: #000;
		font-size: 8vh;
		font-weight: 200;
		align-self: flex-end;
		margin-right: 5px;
	}


	.topic-open{
		position: absolute;
		left: 3vw;
		display: flex;
		justify-content: center;
		align-content: center;
		font-size: 5vh;
		font-weight: 500;
	}

	.topic-item{
		width: 90%;
		height: 10vh;
		border-radius: 5px;
	}

	.up{
		position: relative;
		box-sizing: border-box;
		padding-left: 3vw;
		width: 100%;
		height: 35%;
		background-color: #f2eeff;
		color: #000;
		border-bottom: #fff 1px solid;
		display: flex;
		flex-direction: column;
		justify-content: top;
		align-items: left;
	}

	.app-name{
		margin-top: 2vh;
		font-size: 5vh;
		font-weight: bold;
		color: #805fe5;
	}

	.desc{
		margin-top: 2px;
		font-size: 3vh;
		font-weight: 500;
		color: #805fe5;
	}

	.down{
		width: 100%;
		height: 65%;
		display: flex;

		flex-direction: column;
		justify-content: top;
		align-items: center;
	}

	.topic-item{
		margin: 5px auto;
		width: 90%;
		display: flex;
		justify-content: center;
		align-items: center;
		transition: all 0.5s ease;
	}

	.topic-item-active{
		background-color: #805fe5;
		color: #fff;
	}
</style>