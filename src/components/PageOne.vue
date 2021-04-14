<template>
    <div class="page-one" :style="{'background-position-x':BPX,'background-position-y':BPY}">
        <div class="pd-l"></div>
        <div class="big-title">Origin</div>
        <div class="sub-title">
            <div style="text-align: center">let's <span>explore</span> the <span>ocean</span></div>
            <p><span>&</span></p>
            <div style="text-align: center">find the <span>origin</span> of <span>life</span></div>
        </div>
        <div class="parallax1"><img src="../assets/img/main.png" alt="parallax1"></div>
        <div class="center-button"><button class="btn">Get started</button></div>
    </div>
</template>

<script>
    export default {
        name: "PageOne",
        data(){
          return {
                  BPX:`0px`,
                  BPY:`0px`
          }
        },
        mounted(){
            window.addEventListener('mousemove',this.Parallax,true);
        },
        methods:{
            Parallax(e){
                let horizontal = e.clientX / parseInt(getComputedStyle(document.querySelector('.page-one')).width, 10);
                let vertical = e.clientY / parseInt(getComputedStyle(document.querySelector('.page-one')).height, 10);
                document.querySelector('.big-title').style.transform = this.calculateTransform(horizontal, vertical, -10);
                document.querySelector('.parallax1').style.transform = this.calculateTransform(horizontal, vertical, 10);
                document.querySelector('.center-button').style.transform = this.calculateTransform(horizontal, vertical, 20);
                this.calculateBg(horizontal, vertical, 5);
            },
            calculateTransform(horizontal, vertical, offset){
                return `translate(${horizontal * offset / 0.5}px, ${vertical * offset / 0.5}px)`
            },
            calculateBg(horizontal, vertical, offset){
                this.BPX= `${(horizontal * offset / 0.5)-15}px`;
                this.BPY = `${(vertical * offset / 0.9)-2}px`;
            }
        }
    }
</script>

<style>
    .page-one{
        user-select: none;
        background-image: url("../assets/img/bg.png");
        width: 100%;
        height: 100vh;
        background-color: skyblue;
        position: relative;
    }
    .pd-l{
        width: 64px;
        background: transparent;
        height: 100%;
    }
    .big-title{
        position: absolute;
        left: 45%;
        top: 25%;
        font-family: 'STHupo',serif;
        font-weight: 800;
        font-size: 150px;
        color: white;
        z-index: 888888;
    }
    .sub-title{
        position: absolute;
        left: 60%;
        top: 45%;
        font-family: 'FZYaoti',serif;
        font-weight: 800;
        font-size: 35px;
        color: white;
        z-index: 888888;
    }
    .sub-title p{
        text-align: center;
    }
    .sub-title span{
        color: #D34C6C;
    }
    .parallax1{
        z-index: 9999;
        position: absolute;
        left: 1%;
        top: -1%;
        width: 1000px;
        height: 750px;
    }
    .center-button{
        z-index: 999999;
        position: absolute;
        left: 55%;
        top: 65%;
        width: 200px;
        height: 50px;

    }
    .center-button button{

        cursor: pointer;
        width: 100%;
        height: 100%;
        outline: none;
        border: none;
        color: white;
        background-color: #D34C6C;
        border-radius: 0 30px 0 0 ;
        font-family: 'STXinwei',serif;
        font-size: 18px;
    }
</style>