<template>
    <div class="page-three">
        <div class="items" :style="{marginLeft:`${this.ML}px`}">
            <Card v-for="card in cards" :key="card.index" :card="card"/>
        </div>
        <div class="buttons">
            <div class="button-group" @click="prePic"><button class="arrow arrow-left"><i class="fa fa-caret-left"></i></button><button class="btn left-btn">Previous</button></div>
            <div class="button-group" @click="nexPic"><button class="btn right-btn">Next</button><button class="arrow arrow-right"><i class="fa fa-caret-right"></i></button></div>
        </div>
    </div>
</template>

<script>
    import Card from "@/components/Card";

    export default {
        name: "PageThree",
        data(){
          return {
              ML:0,
              onTransition:'0.4s',
              timer:undefined,
              cards:[
                  {
                      url:require('@/assets/img/pic1.png'),
                      number:1,
                      title:'Hermit',
                      middle:2,
                      content: 'Hermit mainly live on the edge of the Yellow Sea and the southern seas,\n'+
                          'generally in the crevices between beaches and rocks on the seashore.\n'+
                          ' Hermit crabs use snail shells as their parasites,Normally crawling under the shell, \n'+
                          'when frightened, it will immediately retract the body into the mayfly\'s shell.',
                      ML:0,
                      index:0
                  },
                  {
                      url:require('@/assets/img/pic2.png'),
                      number:2,
                      title:'Starfish',
                      content: 'A type of echinoderms with a star-shaped body,\n'+
                          ' also called "star fish". It is mainly distributed on shallow seabed sands or reefs all over the world.\n'+
                          ' Starfish is a greedy carnivore. Its main predator is some slow-moving marine animals,\n'+
                          ' such as shellfish, sea urchins, crabs and sea anemones.',
                      middle:2,
                      ML:0,
                      index:1
                  },
                  {
                      url:require('@/assets/img/pic3.png'),
                      number:3,
                      title: 'Sharks',
                      content: 'Little Sharks live in the vast and boundless ocean. They were born with golden colors.\n' +
                          'They have a pair of piercing eyes and a pointed mouth with white jade teeth.\n'+
                          ' They have a pale yellow triangular fin on their back and sides,\n'+
                          ' which look like sails on a small sailboat. Its tail is also triangular',
                      middle:2,
                      ML:0,
                      index:2
                  },
                  {
                      url:require('@/assets/img/pic4.png'),
                      number:4,
                      title:'Octopuses',
                      middle:2,
                      content:'Octopuses are easily mistaken for fish animals, \n'+
                          'but they belong to mollusks, and octopuses and squids are soft.\n'+
                          'The legs are connected to the head, and the mouth is in the middle of the legs.\n'+
                          'Squids like bright lights, and they often gather in places with light.\n',
                      ML:0,
                      index:3
                  },
                  {
                      url:require('@/assets/img/pic5.png'),
                      number:5,
                      title:'Dolphin',
                      middle:2,
                      content:'It is said that the dolphin is smarter than the gorilla.\n'+
                          'Although it looks very cumbersome, it is very agile.\n'+
                          'The dolphin is known as a "lifeguard at sea." \n'+
                          'Whenever it sees something floating on the water, it will rescue it, and the plank is no exception.',
                      ML:0,
                      index:4
                  },
                  {
                      url:require('@/assets/img/pic6.png'),
                      number:6,
                      title:'Mermaid',
                      middle:2,
                      content:'The mermaid is a kind of magical creature with a human fish tail in a fairy tale. \n'+
                          'The mermaid looks very beautiful. Some studies suggest that the mermaid may be a branch of early humans living in watern\n'+
                          'but we have not really seen them yet.',
                      ML:0,
                      index:5
                  },
                  {
                      url:require('@/assets/img/pic7.png'),
                      number:7,
                      title:'Whales',
                      content:'Whales live in the ocean. \n'+
                          'Many people call them whales because they are like fish.\n'+
                          ' In fact, it is not a fish, but a mammal.\n'+
                          ' Whales are viviparous, and fin whales are more than ten meters long and weigh 7,000 kilograms when they are born.',
                      middle:2,
                      ML:0,
                      index:6
                  },
                  {
                      url:require('@/assets/img/pic1.png'),
                      number:1,
                      title:'Hermit',
                      content:'Hermit mainly live on the edge of the Yellow Sea and the southern seas,\n'+
                          'generally in the crevices between beaches and rocks on the seashore.\n'+
                          ' Hermit crabs use snail shells as their parasites,Normally crawling under the shell, \n'+
                          'when frightened, it will immediately retract the body into the mayfly\'s shell.',
                      middle:2,
                      ML:0,
                      index:7
                  },
                  {
                      url:require('@/assets/img/pic2.png'),
                      number:2,
                      title:'Starfish',
                      content: 'A type of echinoderms with a star-shaped body,\n'+
                          ' also called "star fish". It is mainly distributed on shallow seabed sands or reefs all over the world.\n'+
                          ' Starfish is a greedy carnivore. Its main predator is some slow-moving marine animals,\n'+
                          ' such as shellfish, sea urchins, crabs and sea anemones.',
                      middle:2,
                      ML:0,
                      index:8
                  },
                  {
                      url:require('@/assets/img/pic3.png'),
                      number:3,
                      title: 'Sharks',
                      content: 'Little Sharks live in the vast and boundless ocean. They were born with golden colors.\n' +
                            'They have a pair of piercing eyes and a pointed mouth with white jade teeth.\n'+
                          ' They have a pale yellow triangular fin on their back and sides,\n'+
                          ' which look like sails on a small sailboat. Its tail is also triangular',
                      middle:2,
                      ML:0,
                      index:9
                  },
              ],
          }
        },
        components:{
            Card,
        },
        mounted() {
            this.timer = setInterval(this.Swpier, 4000);
        },
        methods:{
            Swpier(){
                this.ML -= 455;
                for (let c of this.cards){
                    c.middle = c.middle%7 + 1;
                }
                if(this.ML/455 === -8){
                    this.ML = 0;
                    for (let c of this.cards){
                        c.middle = 2;
                    }
                }
            },
            prePic(){
                clearInterval(this.timer);
                if(this.ML/455 === 0){
                    this.ML = 0;
                }else{
                    this.ML += 455;
                    for (let c of this.cards){
                        c.middle = c.middle%7 - 1;
                    }
                }
                setTimeout(() =>{},2000);
                this.timer = setInterval(this.Swpier, 4000);
            },
            nexPic(){
                clearInterval(this.timer);
                if(this.ML/455 === -7){
                    this.ML = 0;
                }
                this.ML -= 455;
                for (let c of this.cards){
                    c.middle = c.middle%7 + 1;
                }
                setTimeout(()=> {},2000);
                this.timer = setInterval(this.Swpier, 4000);
            }
        }
    }
</script>

<style>
    .page-three{
        width: 100%;
        height: 100vh;
        position: relative;
        background-image: url("../assets/img/bg3.png");
        background-repeat: no-repeat;
        background-size: cover;
    }
    .items{
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%,-50%);
        display: flex;
        height: 600px;
        width: 1365px;
        align-items: center;
        transition: 0.4s;
    }
    .buttons{
        position: absolute;
        width: 100%;
        height: 64px;
        bottom: 5%;
        left: 0;
        display: flex;
        justify-content: space-around;
    }
    .buttons .button-group{
        display: flex;
        width: 200px;
        height: 50px;
        justify-content: center;
        align-items: center;
        box-shadow: 0 0 10px #000000;
    }
    .buttons .button-group button{
        cursor: pointer;
        height: 50px;
        outline: none;
        border: none;
        background-color: #BD507D;
        color: white;
        font-family: 'BalooBhaina', serif;
    }
    .buttons .button-group .arrow{
        box-sizing: border-box;
        width: 50px;
    }
    .buttons .button-group .arrow-right{
        box-shadow: 0 1px 3px rgb(18 18 18);
    }
    .buttons .button-group .arrow-left{
        border-right: 1px solid #EBEBEB;
    }
    .buttons .button-group .btn{
        width: 150px;
        font-weight: 600;
        font-size: 18px;
    }
    .buttons .button-group .right-btn{
        border-right: 1px solid #EBEBEB;
    }
    .buttons .button-group .left-btn{

        box-shadow: 0 1px 3px rgb(18 18 18);
    }
</style>