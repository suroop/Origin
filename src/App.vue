<template>
    <div id="app">
        <TopItem :ST="ST"></TopItem>
        <PageOne></PageOne>
        <PageTwo :ST="ST"></PageTwo>
        <PageThree></PageThree>
        <PageFour></PageFour>
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

    #app {
        background: skyblue;
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        color: #2c3e50;
        position: relative;
    }
</style>
