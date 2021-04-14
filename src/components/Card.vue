<template>
    <div class="card" :style="card.middle === card.number?activeClass:disableClass">
        <div id="pic"><img :src="card.url" alt="pic"></div>
        <div class="number">{{`0${card.number}`}}</div>

        <div class="bottom-item">
            <p class="bottom-title">{{card.title}}</p>
            <div class="border"></div>
            <div class="detail">
                {{card.middle === card.number?card.content:''}}
            </div>
            <button class="learn-more"> Learn More <span><i class="fa fa-caret-right"></i></span></button>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Card",
        data(){
            return {
                activeClass:{
                    height: "500px",
                },
                disableClass:{
                    height: "400px",
                },
            }
        },
        props:{
            card:{
                required:true
            }
        },
    }
</script>

<style>
    .card{
        position: relative;
        width: 275px;
        min-width: 275px;
        background-color: #4249B9;
        margin: 0 80px;
        border: 10px solid #33328F;
        border-radius: 35px;
        transition: 0.4s;
    }
    .card .number{
        text-align: left;
        padding-right: 5px;
        color: white;
        z-index: 99999;
        width: 100%;
        font-family: 'STXinwei',serif;
        font-weight: 800;
        font-size: 25px;
    }
    .card #pic{
        z-index: 999;
        position: absolute;
        top: -5%;
        left: 50%;
        transform: translate(-50%);
        width: 400px;
        height: 400px;
    }
    .card #pic img{
        height: auto;
        width: 100%;
    }
    .card .bottom-item{
        margin-left: 15px;
        position: absolute;
        top: 270px;
        left: 0;
        width: 100%;
        height: 125px;
        min-height: 125px;
    }
    .card .bottom-item .bottom-title{
        font-size: 25px;
        color: white;
        font-family: 'STXinwei',serif;
    }
    .card .bottom-item .border{
        margin: 15px 0;
        width: 80px;
        padding-left: 15px;
        height: 1px;
        background-color: white;
    }
    .card .bottom-item .detail{
        width: 90%;
        margin: 15px 0;
        color: white;
        font-size: 10px;
        transition: 0.4s;
    }
    .card .bottom-item .learn-more{
        width: 125px;
        height: 30px;
        background-color: #4249B9;
        color: white;
        border:3px solid #BA72CB;
        border-radius: 2px;
    }
    .card .bottom-item .learn-more span{
        float: right;
        margin-right: 15px;
    }
</style>