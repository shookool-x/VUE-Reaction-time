<template>
  <h1>سرعت عملت را نشان بده</h1>
  <button class="startbtn" @click="showBlock();mkwh();" :disabled="isShow" >بزن بریم</button>
  <Block v-if="blkshow" :wr="rndwidth" :hr="rndheight" @end="endthisGame" />
  <Result v-if="resShow" :time="myTime" @res="restartGame"/>
</template>

<script>
import Block from './components/Block.vue'
import Result from './components/Result.vue'

export default {
  name:'App',
  components: {Block, Result},
  data(){
    return{

      blkshow:false,
      resShow:false,
      isShow : false,
      delay:null,
      myTime:0,
      wwidth :window.innerWidth-50,
      wheight:window.innerHeight-50,
      rndwidth : 0,
      rndheight : 0,

    }
  },

  methods:{
    showBlock(){
      this.delay = 2000 + Math.random()*5000;
      this.isShow = true;
      this.blkshow = true;
    },

    endthisGame(tt,showblk){
      this.myTime = tt;
      this.blkshow = showblk;
      this.resShow = true;
    },

    restartGame(a){
      this.isShow = a;
      this.resShow = a;
    },

    mkwh(){
      this.rndwidth = Math.random()*this.wwidth;
      this.rndheight = Math.random()*this.wheight;
    }

  },

}
</script>

<style>
#app{
  /* font-family: Avenir, Helvetica, Arial, sans-serif; */
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #39e7e7;
  margin-top: 60px;
}
.startbtn{
  margin: 10px auto;
  font-family: 'IRnastealiq';
  font-size: 24px;
  width: 100px;
  height: 60px;
  border-radius: 50%;
  background-color: #39e7e7;
  cursor: pointer;
}
.startbtn[disabled]:hover{
  cursor: not-allowed;
}
</style>