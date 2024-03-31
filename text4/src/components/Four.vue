<template>
  <div class="four">
    <p>姓名：{{ student.name }}</p>
    <p>年龄：{{ student.age }}</p>
    <button @click="changeName">修改姓名</button>
    <button @click="changeAge">修改年龄</button>
    <button @click="changeOneDog">修改第一只宠物</button>
    <button @click="changeTowDog">修改第二只宠物</button>
    <button @click="changeAllDog">修改所有宠物</button>
  </div>
</template>

<script setup name="Four">

import {reactive, watch} from "vue";

let student=reactive({name:'陈燕武',age:19,pet:{pet1:'小榴莲',pet2:'小粉'}})
function changeName(){
  student.name += '~'
}
function changeAge(){
  student.age += 1
}
function changeOneDog(){
  student.pet.pet1='绿色小榴莲'
}
function changeTowDog(){
  student.pet.pet2='粉色小恐龙'
}
function changeAllDog(){
  student.pet.pet1 = '我是一只小榴莲'
  student.pet.pet2 = '我是一只小恐龙'
}
const sname = watch(()=>student.name,(newValue,oldValue)=>{
  console.log(`学生的姓名发生了变化，新值newValue是${newValue},旧值oldValue是${oldValue}`)
})
const sage = watch(()=>student.age,(newValue,oldValue)=>{
  console.log(`学生的年龄发生了变化，新值newValue是${newValue},旧值oldValue是${oldValue}`)
})
const spet = watch(student.pet,(newValue,oldValue)=>{
  console.log(`学生的宠物发生了变化，新值newValue是${JSON.stringify(newValue)},旧值oldValue是${JSON.stringify(oldValue)}`)
})
</script>

<style scoped>
.four {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
</style>