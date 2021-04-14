<template>
    <div class="page-four">
        <div class="foo"><img src="../assets/foo.png" alt=""></div>
        <div class="join">

            <div class="textField">
                <p class="p1">Our website has not been completed yet</p>
                <p>we hope you can join us & contribute to the ocean of science</p>
                <p>We are looking for partners who will be able to <span>design</span> and <span>maintain</span> the website to join us</p>
                <p>We look forward to cooperating with you</p>
            </div>
            <div class="form">
                <form action="">
                    <div class="button-group">
                        <label>
                            <input type="text" v-model="emailAddress" placeholder="Your Email Address">
                        </label>
                        <input type="submit" value="Join us" @click.prevent="check">
                    </div>
                </form>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "PageFour",
        data(){
            return {
                emailAddress:''
            }
        },
        methods:{
            check(){
                let reg = new RegExp("^[a-z0-9]+([._\\-]*[a-z0-9])*@([a-z0-9]+[-a-z0-9]*[a-z0-9]+.){1,63}[a-z0-9]+$");
                if(this.emailAddress === ''){
                    alert("Oops!The input cannot be empty!");
                    return false;
                }else if(!reg.test(this.emailAddress)){
                    alert("Emmm it look like the format you input was wrong!");
                    return false;
                }else{
                    alert("successfully");
                    return true;
                }
            }
        }
    }
</script>

<style>
    @font-face{
        font-family:'AlegreyaSansSC';
        src:url('../assets/font/AlegreyaSansSC-ThinItalic.ttf');
    }
    .page-four{
        width: 100%;
        height: 100vh;
        position: relative;
    }
    .page-four .foo{
        position: absolute;
        width: 1000px;
        height: 750px;
        bottom: 0;
        left: 0;
    }
    .page-four .foo img{
        width: 100%;
        height: 100%;
    }
    .page-four .join{
        position: absolute;
        width: 800px;
        height: 450px;
        bottom: 0;
        right: 0;
    }
    .page-four .textField{
        color: white;
        font-size: 25px;
        font-family: 'AlegreyaSansSC','FZShuTi',serif;
        font-weight: 800;
        text-align: center;
    }
    .page-four .textField span{
        color: #D14D6D;
    }
    .page-four .textField p:first-child{
        font-size: 40px;
        line-height: 80px;
    }
    .page-four .textField p{
        line-height: 45px;
    }
    .page-four .join .form{
        margin-top: 30px;
    }
    .page-four .join .button-group{
        margin: 0 auto;
         width: 600px;
         height: 64px;
     }
    .page-four .join .button-group input{
        width: 50%;
        height: 100%;
        border: none;
        outline: none;
        font-family: 'AlegreyaSansSC','FZShuTi',serif;
        font-weight: 600;
        font-size: 20px;
    }
    .page-four .join .button-group input[type="submit"]{
        border-radius: 0 35px 0 0;
        background-color: #D14D6D;
        color: white;
    }
    .page-four .join .button-group input[type="text"]{
        text-align: center;
     }
    .page-four .join .button-group input[type="text"]::-webkit-input-placeholder{
        color: #C4C4C4;
        text-align: center;
    }
</style>