<template>
    <div class="top" :style="{top:ST+'px'}">
        <div class="left-col col">
            <ul>
                <li :style="changeColor" @click="sentPage(2)">Missions</li>
                <li :style="changeColor" @click="sentPage(3)">Creatures</li>
            </ul></div>
        <div class="mid"><img src="../assets/img/logo.png" alt="logo"></div>
        <div class="right-col col">
            <ul>
                <li :style="changeColor" @click="sentPage(4)">JoinUs</li>
                <li :style="changeColor">Early Access</li>
            </ul></div>
    </div>
</template>

<script>
    export default {
        name: "Top",
        props:{
            ST:{
                type:Number
            }
        },
        data(){
            return {
                changeColor:{
                    color:"white"
                },

            }
        },
        watch:{
            ST(newVal){
                let i = Math.floor(newVal/window.innerHeight);
                if (i%2===0){
                    this.changeColor.color = "white";
                }else if (i%2===1){
                    this.changeColor.color = "black";
                }
            }
        },
        methods:{
            sentPage(page){
                this.$emit('getPage', page);
            }
        }
    }
</script>

<style>
    .top{
        z-index: 99999;
        background: transparent;
        position: absolute;
        left: 0;
        width: 100%;
        height: 64px;
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: space-around;
    }
    .top div{
        height: 100%;
    }
    .top .left-col{
        margin-left: 50px;
    }
    .top .right-col{
        margin-right: 50px;
    }
    .top .col{
        width: 300px;
    }
    .top .mid{
        width: 400px;
        display: flex;
        flex-direction: row;
        justify-content: center;
        align-items: center;
        overflow: hidden;
    }
    .top div ul{
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: space-between;
        width: 100%;
        height: 100%;
    }
    .top div ul li{
        font-family: 'STXinwei',serif;
        color: white;
        font-size: 18px;
        cursor: pointer;
    }
    .top .right-col ul li:last-child{
        padding: 10px 25px ;
        border: 2px #B85F8C solid;
        cursor: default;
    }
    .top .mid img{
        height: 100%;
        width: auto;
        transition: 0.4s;
    }
    .top .mid img:hover{
        height: 150%;
        transform: rotate(30deg);
    }
</style>