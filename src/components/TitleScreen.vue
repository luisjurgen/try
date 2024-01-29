<template>
   <div class="titleScreen">
      <h1>SoundPillards</h1>
      <p>A simple Creative Coding example</p>
      <button v-if="!playFlag" @click="onPlay()">REPRODUCIR</button>
      <button v-else @click="onPause()">Pausar</button>
   </div>
</template>

<script>

import SoundReactor from "../classes/SoundReactor";

export default {
   name: "TitleScreen",
   data(){
      return {
         initFlag: false,
         playFlag: false,
      }
   },
   methods:{
      onPlay(){
         if(!this.initFlag){
            this.initFlag = true;
            SoundReactor.init();
         }

         SoundReactor.play();
         this.playFlag=true;
      }, 
      onPause(){
         SoundReactor.pause();
         this.playFlag=false;
      }

   }
   }

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="stylus">
.titleScreen{
   position: absolute;
   width:100vw;
   height: 100vh;
   top:0;
   left:0;
   color:white;
   padding: 3rem;
   pointer-events:none;
   
   
   button {
      color:white;
      background:none;
      border-radius: 20rem
      display:flex;
      justify-content:center;
      align-items:center;
      padding: 1rem;
      border: none;
      position:absolute
      bottom: 3rem;
      right:3rem;
      border:solid white;
      pointer-events:initial;
      cursor: pointer; 
      transition: all 0.3s;



      &:hover{
         background: purple;
      }
   }
}

</style>
