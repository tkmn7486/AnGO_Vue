<template>
<div class="app">
  <div class="title">
    <h2 class="mainTitle">AnGO</h2>
    <p class="subTitle">※現在、アルファベットの小文字と一部記号にのみ対応しています。</p>
  </div>
  <p class="modeName">-- {{menu[count].name}}モード --</p>
  <button class="changeModeButton" @click="changeMode">モード切替</button>
  <textarea v-model="inputS"></textarea>
  <button class="EXButton" @click="pushButton">{{menu[count].name}}</button>
</div>

</template>

<script>
import { ref } from 'vue'

export default {
  name: 'App',
  setup(){
    let inputS = ref("")
    let mode = ref()
    let count=ref(0)

    let menu = ref([
      {type:"1", name:"暗号化"},
      {type:"2", name:"解読"}
    ])

    const EXCode =[
      {crp:'a', lan:'あ'},
      {crp:'b', lan:'い'},
      {crp:'c', lan:'う'},
      {crp:'d', lan:'え'},
      {crp:'e', lan:'お'},
      {crp:'f', lan:'か'},
      {crp:'g', lan:'き'},
      {crp:'h', lan:'く'},
      {crp:'i', lan:'け'},
      {crp:'j', lan:'こ'},
      {crp:'k', lan:'さ'},
      {crp:'l', lan:'し'},
      {crp:'m', lan:'す'},
      {crp:'n', lan:'せ'},
      {crp:'o', lan:'そ'},
      {crp:'p', lan:'た'},
      {crp:'q', lan:'ち'},
      {crp:'r', lan:'つ'},
      {crp:'s', lan:'て'},
      {crp:'t', lan:'と'},
      {crp:'u', lan:'な'},
      {crp:'v', lan:'に'},
      {crp:'w', lan:'ぬ'},
      {crp:'x', lan:'ね'},
      {crp:'y', lan:'の'},
      {crp:'z', lan:'は'},
      {crp:',', lan:'ひ'},
      {crp:'-', lan:'ふ'},
      {crp:'@', lan:'へ'},
      {crp:'!', lan:'ま'},
      {crp:'/', lan:'み'},
      {crp:'_', lan:'む'},
      {crp:' ', lan:'め'},
    ]

    const pushButton=()=>{
      if(count.value == 1){
        forLang();
      }else{
        forCript();
      }
    }

    const forCript=()=>{
      for(let cc = 0; cc < EXCode.length; cc++){
        let before = EXCode[cc].crp
        let after = EXCode[cc].lan

        inputS.value = inputS.value.replace(new RegExp(before,"g"),after);
        console.log(inputS.value);
      }
    }

    const forLang=()=>{
      for(let cc = 0; cc < EXCode.length; cc++){
        let before = EXCode[cc].lan
        let after = EXCode[cc].crp

        inputS.value = inputS.value.replace(new RegExp(before,"g"),after);
        console.log(inputS.value);
      }
    }

    const changeMode=()=>{
      if(count.value>=1){
        count.value=0;
      }else{
        count.value++;
      }
    }

    return{
      inputS,
      mode,
      menu,
      count,
      EXCode,
      changeMode,
      forCript,
      forLang,
      pushButton,
    }
  }
}
</script>

<style>
html{
  background-color:black;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #00c02a9f;
  margin-top: 60px;
}

.mainTitle{
  font-size:50px;
  font-family:Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif
}

.subTitle{
  font-size:5px;
}

.changeModeButton{
  display:inline;
  margin-bottom:30px;
  color:#00c02a9f;
  background-color:black;
}

.EXButton{
  margin-top:15px;
  color:#00c02a9f;
  background-color:black;
}

textarea{
  display:block;
  margin:0 auto;
  color:#00c02a9f;
  background-color:black;
  width:300px;
  height:200px;
}
</style>