<template>
  <div class="divar">
    زمان واکنشت : 
    <br>
    {{ time }} میلی ثانیه
    <br>
    {{ sts }}
  </div>
  <button class="startbtn" @click="restartGame()">
    شروع مجدد
  </button>
</template>

<script>
export default {
    props:['time'],
    data(){
        return{
            sts : null,
        }
    },

    methods:{
        restartGame(){
            this.$emit('res',false);    
        },
    },

    mounted(){
      if(this.time<700){
        this.sts = "بابا دستخوش، چه سرعت عملی!";
      }
      else if(this.time<1200){
        this.sts ="بد نیست ولی نیاز به تمرین بیشتر داری!";
      }
      else{
        this.sts ="خیلی کندی، هیچی نمیشی بی مصرف";
      }
    },
}
</script>

<style>
.divar{

    font-family: 'kamran';
    font-size: 25px;
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 50px auto;
    width:300px;
    height: 100px;
    border: 4px dashed yellowgreen;
    border-radius: 50px;
}
</style>