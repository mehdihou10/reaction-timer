<template>
<div class="game">
  <div class="start-game">
  <h1>Mehdi Reaction Timer</h1>

  <button ref="play" class="btn btn-success" @click="playGame">Play</button>
  </div>

  <Block  v-show="showBox" @click="stopGame"/>

  <Result v-show="showResult" :class="addClass()" :time="timer" :notice="timerNotice"/>

</div>
</template>

<script>
import './assets/master.css';
import Block from './components/Block.vue';
import Result from './components/Result.vue';

export default {
 
 components:{Block,Result},

 data(){
 
  return{
    showBox : false,
    showResult: false,
    timer: 0,
    c: null,

  }
 },

  methods: {

    playGame(e){

     e.target.classList.add("stop-btn");

     this.showBoxFun();

     this.showBox = false;
     this.showResult = false;


    },

    showBoxFun(){
this.timer = 0;

setTimeout(() =>{
      this.showBox = true;
      this.c = setInterval(() => {
        this.timer++;
      },1);

},2000 + Math.random() * 5000);
},

    stopGame(){
      this.showBox = false;
      this.showResult = true;

      this.$refs.play.classList.remove("stop-btn");
      clearInterval(this.c)

    },

    addClass(){
      if(this.timer < 50){
        return 'success';
      }

      else{
        return 'fail'
      }
    }

  },
  
  computed:{
    timerNotice(){

      if(this.timer < 40){

      return 'Fast pace'
     }
     else{

      return 'slow pace'
     }


  
    }
  }

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
</style>
