<template>
    <div class="topic-item-root" v-show="!deleted">
        <div class="index topic-unit" v-show="type == 'hot' ">
            <span>
                {{ topic.index }}
            </span>
        </div>

        <uni-link class="content topic-unit" :href="topic.link" showUnderLine="false" color="#000">
            {{ topic.title }}
        </uni-link>

        <div class="hot-nums topic-unit"  :v-show="topic.hotValue != ''">
            <uni-icons type="fire-filled" size="20" color="red"></uni-icons>
            <span>
                {{ topic.hotValue }}
            </span>
        </div>

        <div class="option topic-unit">

            <div class="hot" v-if="type == 'hot'">
                <uni-icons type="heart-filled" size="30" color="red" v-if="collected" @click="cancelTopicForLater"></uni-icons>
                <uni-icons type="heart" size="30" color="red" v-else @click="collectTopicForLater"></uni-icons>
            </div>

            <div class="later" v-else>
                <uni-icons type="trash-filled" size="30" color="red" @click="removeTopicForLater"></uni-icons>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        props: {
            topic: {
                type: Object,
                default: () => {
                    return {}
                }
            },
            type:{
                type: String,
                default: 'hot'
            }
        },
        data() {
            return {
                title: 'Hello',
                collected: false,
                deleted: false
            }
        },
        onLoad() {

        },
        methods: {
            collectTopicForLater(){
                this.collected = true;
                let laterData = uni.getStorageSync("later-data")
                if(!laterData){
                    laterData = []
                }
                laterData.push(this.topic)
                uni.setStorageSync("later-data",laterData)
				uni.vibrateShort({
					success: function () {
						console.log('success');
					}
				});
            },
            cancelTopicForLater(){
                this.collected = false;
                let laterData = uni.getStorageSync("later-data")
                if(!laterData){
                    return
                }
                let index = laterData.findIndex(item => item.title == this.topic.title)
                if(index != -1){
                    laterData.splice(index,1)
                }
                uni.setStorageSync("later-data",laterData)
				uni.vibrateShort({
					success: function () {
						console.log('success');
					}
				});
            },
            removeTopicForLater(){
                let laterData = uni.getStorageSync("later-data")
                if(!laterData){
                    return
                }
                let index = laterData.findIndex(item => item.title == this.topic.title)
                if(index != -1){
                    laterData.splice(index,1)
                }
                uni.setStorageSync("later-data",laterData)
                this.deleted = true
				uni.vibrateShort({
					success: function () {
						console.log('success');
					}
				});
            },
            openWebView(){
                // 在浏览器中打开

            }
        }
    }
</script>

<style>
.topic-unit{
    margin: 3px 3px;
}
.topic-item-root{
    display: flex;
    justify-content: space-evenly;
    align-items: center;
    background-color: #f2eeff;
    color: #000;
    margin: 4px auto;
    width: 90%;
    max-height: 20vh;
    border-radius: 10px;
}

.index{
    display: flex;
    justify-content: center;
    align-items: center;

    font-size: 4vh;
    font-weight: bold;
    color: #805fe5;
}

.content{
    display: flex;
    justify-content: center;
    align-items: center;
    font-weight: bold;
    color: #000;
}

.hot{
    display: flex;
    justify-content: center;
    align-items: center;
}

.later{
    display: flex;
    justify-content: center;
    align-items: center;
}

.hot-nums{
    display: flex;
    justify-content: center;
    align-items: center;
    font-weight: bold;
    font-size: small;
    color: red;
}

.option{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

</style>