<template>
    <div id="app">
        <TopItem :ST="ST" @getPage="goTo"></TopItem>
        <PageOne></PageOne>
        <PageTwo :ST="ST" ref="pageTwo"></PageTwo>
        <PageThree ref="pageThree"></PageThree>
        <PageFour ref="pageFour"></PageFour>
    </div>
</template>
<script>
    import TopItem from "@/components/TopItem";
    import PageOne from "@/components/PageOne";
    import PageTwo from "@/components/PageTwo";
    import PageThree from "@/components/PageThree";
    import PageFour from "@/components/PageFour";
    export default {
        name: 'App',
        data() {
            return {
                ST: 0,
                TotalHeight:0
            }
        },
        components: {
            TopItem,
            PageOne,
            PageTwo,
            PageThree,
            PageFour
        },
        mounted() {
            window.addEventListener('scroll', this.handleScroll, true);
            this.TotalHeight = window.innerHeight;
            window.onmousewheel = document.onmousewheel = this.scrollFunc;
        },
        methods: {
            goTo(data){
                switch (data) {
                    case 2:
                        document.documentElement.scrollTop = this.TotalHeight;
                        break;
                    case 3:
                        document.documentElement.scrollTop = this.TotalHeight*2;
                        break;
                    case 4:
                        document.documentElement.scrollTop = this.TotalHeight*3;
                        break;
                    default:
                        document.documentElement.scrollTop = 0;
                }
                console.log(data);
            },
            handleScroll() {
                this.ST = document.documentElement.scrollTop || document.body.scrollTop || window.pageYOffset;
            },
            scrollFunc(e) {
                e = e || window.event;
                if (e.wheelDelta) {
                    //let t = Math.floor(document.documentElement.scrollTop / this.TotalHeight);
                    if (e.wheelDelta > 0) {
                            // if(t!==0){
                            //     document.documentElement.scrollTop = (t-1)*this.TotalHeight;
                            // }
                    } else if (e.wheelDelta < 0) {
                        // if(t!==4){
                        //     document.documentElement.scrollTop = (t+1)*this.TotalHeight;
                        // }
                    }
                }
            }
        }
    }
</script>

<style>
    @font-face{
        font-family:'AlegreyaSansSC';
        src:url('./assets/font/AlegreyaSansSC-ThinItalic.ttf');
    }
    @font-face{
        font-family:'BalooBhaina';
        src:url('./assets/font/BalooBhaina-Regular.ttf');
    }
    @font-face{
        font-family:'doudou';
        src:url('./assets/font/doudou.ttf');
    }
    @font-face{
        font-family:'FZYaoti';
        src:url('./assets/font/FZYTK.TTF');
    }
    @font-face{
        font-family:'STHupo';
        src:url('./assets/font/STHUPO.TTF');
    }
    @font-face{
        font-family:'STXinwei';
        src:url('./assets/font/STXINWEI.TTF');
    }
    #app {
        background: skyblue;
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        color: #2c3e50;
        position: relative;
    }
</style>
