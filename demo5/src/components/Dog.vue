
<template>
<div class="person">
 <h1>当前求和为：{{sum}},放大十倍后为{{sum*10}}</h1>
  <button @click="addOne">点我+1</button>
  <button @click="ddaOne">点我-1</button>
  <hr>
  <div style="display: flex">
    <div v-for="item in dogList" style="width:100px;margin-right: 10px">
      <img :src="item" alt="">
    </div>
  </div>
  <button @click="getDog">再来一只狗</button>
</div>
</template>

<script setup name="Dog">

import {reactive, ref} from "vue";
import axios from "axios";
let sum =ref(0)
let dogList = reactive([])
let dogSum= ref(0)
function addOne(){
  sum.value++
}
function ddaOne(){
  sum.value--
}
function getDog() {
  axios.get("https://dog.ceo/api/breed/retriever/images/random")
      .then(res=>{
        console.log(res)
        dogList.push(res.data.message)
        dogSum.value=dogList.length
        console.log(dogSum.value)
      })
}
wa
</script>


<style scoped>
.person{
  background: skyblue;
  box-shadow: 0 0 10px;
  border-radius: 10px;
  padding: 20px;
}
button{
  margin: 0 5px;
}
img{
  width: 100px;
  margin-right: 10px;
}
</style>