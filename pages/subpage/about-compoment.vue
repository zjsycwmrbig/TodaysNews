<template>
    <div class="about-root">
        <div class="about-title">
            <span>关于我们</span>
        </div>
        <div class="about-body">
            <div class="about-item">
                <span class="item-title">项目作者</span>
                <span class="item-content">
                    <uni-link href="https://github.com/zjsycwmrbig" showUnderLine="false" color="#000" :fontSize="linkFontSize">BUPT 2021 2021211202 张靳生</uni-link>
                </span>
            </div>
            <div class="about-item">
                <span class="item-title">项目地址</span>
                <span class="item-content">
                    <uni-link href="https://github.com/zjsycwmrbig/TodaysNews" showUnderLine="false" color="#000" :fontSize="linkFontSize">TodaysNews</uni-link>
                </span>
            </div>
            <div class="about-item">
                <span class="item-title">特别鸣谢</span>
                <span class="item-content">
                    <uni-link href="https://www.itab.link/" showUnderLine="false" color="#000" :fontSize="linkFontSize">ITAB 新标签页</uni-link>
                </span>
            </div>
        </div>

        <div class="tips">
            <span class="tips-title">
                <span>
                    严重敬告
                </span>
            </span>
            <span>本项目仅供学习交流使用，不得用于商业用途,本项目中使用的api均来源于网络，请勿恶意攻击与传播</span>
        </div>
        <div class="logo"></div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                linkFontSize: '20'
            }
        },
        onLoad() {

        },
        methods: {

        }
    }
</script>

<style>
.about-root{
    display: flex;
    flex-direction: column;
}

.about-title{
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

.about-body{
    width: 100%;
}

.about-item{
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
    
    padding: 2px;
    
    width: 100%;
    height: 10vh;

    background-color: #f2eeff;
    color: #000;
    border-bottom: #fff 4px solid;
    margin: 5px auto;
}

.item-title{
    font-size: 4vh;
    font-weight: 1000;
    align-self: flex-start;
    border-left: #805fe5 4px solid;
}

.item-content{
    font-size: 3vh;
    font-weight: 500;
    display: flex;
    justify-content: center;
    align-items: center;
}



.tips{
    padding: 2px;
    width: 100%;
    height: 10%;
    background-color: #f2eeff;
    color: #000;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 3vh;
    font-weight: 1000;
}

.tips-title{
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 4vh;
    font-weight: 1000;
    color: red;
}

.logo{
    margin: 5px auto;
    width: 40vw;
    height: 40vw;
    background-image: url("~@/static/logo.jpg") ;
    background-size: 100%;
    background-repeat: no-repeat;
}


</style>