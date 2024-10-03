<template>
  <div class="likemodal">
    <div class="block" :style="newStyle()" v-if="showblk" @click="findMyReaction()">
      💀
    </div>
  </div>
  
</template>

<script>
export default {
    props:['wr', 'hr'],
    data(){
      return {
        showblk:false,
        time1:0,
        rctTime:0,
      }
    },

    methods:{
      
      newStyle(){
        return{
          marginTop:this.hr+'px' ,
          marginLeft:this.wr+'px',
        }
      },

      whatTime(){
        this.time1=performance.now();

      },

      findMyReaction(){

        this.rctTime = performance.now()-this.time1;
        this.$emit('end', Math.round(this.rctTime), !this.showblk)

      },

    },

    mounted(){
      // console.log('Block components mount now!');
      setTimeout(() => {

        this.showblk=true;
        this.whatTime();

      }, this.delay);
    },

    updated(){
      // console.log('Now its update . . .');
    },


    unmounted(){
      // console.log('Bye Bye!');
    },
}
</script>

<style>
.likemodal{
  position: fixed;
  top:0;
  left:0;
  width:100%;
  height: 100%;
  background-color: rgba(162, 255, 22, 0.5);
}

.block{
  
    width:50px;
    height: 50px;
    background: rgb(0, 0, 0);
    margin: 100px auto;
    display: flex;
    justify-content: center;
    align-items: center;
    border-radius: 50%;
}
</style>