<template>
 <div class="three">
   <p>姓名：{{student.name}}</p>
   <p>年龄：{{student.age}}</p>
   <button @click="changeName">修改姓名</button>
   <button @click="changeAge">修改年龄</button>
   <button @click="changeStudnet">修改所有信息</button>
 </div>
</template>

<script setup name="Three">
import {reactive, watch} from "vue";

    let student = reactive({
      name:'陈燕武',age:'19'
    })
    function changeName(){
      student.name += '~'
    }
    function changeAge(){
      student.age += 1
    }
    function changeStudnet(){
      student.name = 'chenyanwu'
      student.age = 15
    }
    const zhen = watch(student,(newValue,oldValue) =>{
      console.log(`学生对象发生了变化，新值newValue是  ${JSON.stringify(newValue)},旧值oldValue是  ${JSON.stringify(oldValue)}`)
    })
</script>

<style scoped>
  .three{
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }
</style>