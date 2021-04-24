<template>
    <div class="page-two">
        <div class="part part1 content">
            <div class="content-title">
                <div>After rowing in the sea for a while, let us explore the deep sea. Are you ready?</div>
            </div>
        </div>
        <div class="part activeBg" ref="activeBg" :style="{'background-position-y':positionY1+'px'}"></div>
        <div class="part part2 content">
            <div class="content-title">
                <p>The exploration of the ocean depths will benefit humankind</p>
                <p>Our story is a voyage of discovery</p>
                <p>starting with feeling the gifts from the <span>sea creatures</span></p>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "PageTwo",
        props:{
          ST:{
              required:true,
              type:Number
          }
        },
        data(){
            return{
                positionY1: 0, //背景Y轴偏移量
                Y1: 0,
                ratio: 0.3 //视差偏移率
            }
        },
        mounted() {
            window.addEventListener("scroll", this.handleScroll);
            this.Y1 = this.$refs.activeBg.offsetTop * this.ratio
        },
        methods: {
            handleScroll: function() {
                this.positionY1 = this.Y1 - this.ST * this.ratio; //原始高度-滚动距离*视差系数

            }
        },
    }
</script>

<style>
    .page-two{
        width: 100%;
        height: 100vh;


    }
    .page-two .part{
        width: 100%;
    }
    .page-two .content{
        height: 30%;
    }
    .page-two .activeBg{
        height: 40%;
        background: url("../assets/img/pageT.png") no-repeat fixed;
        background-size: 100% 100%
    }
    .page-two .part{
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .page-two .part1 .content-title{
        display: grid;
        place-items: center;
        text-align: center;
        width: 80%;
        height: 80%;
        color: #5C99D2 ;
        font-family: 'FZYaoti', serif;
        font-size: 35px;
        font-weight: 800;
    }
    .page-two .part2{
        background-color: #2FABDF;
    }
    .page-two .part2 .content-title{
        text-align: center;
        width: 80%;
        height: 80%;
        color: #0A53AF;
        font-family: 'FZYaoti', serif;
        font-size: 35px;
        font-weight: 800;
    }
    .page-two .part2 .content-title p{
        line-height: 50px;
    }
    .page-two .part2 .content-title span{
        color: #D34C6C;
    }

</style>