<template>
  <div class="zhong">
    <span v-if="demo==1">
      <h1>Hello,Vue</h1>
    </span>
    <span v-if="demo==0">
      <h1>Hello,World</h1>
    </span>
    <button @click="changeDemo">点我切换页面</button>
  </div>
</template>

<script setup name="P66">
import {onBeforeMount, onBeforeUnmount, onBeforeUpdate, onMounted, onUnmounted, onUpdated,ref} from "vue";
let demo=ref(1)
function changeDemo(){
  console.log("aaa")
  if (demo.value == 1){
    demo.value = 0
  }else{
    demo.value = 1
  }
}

onBeforeMount(()=>{
  console.log("这是在组件挂载之前")
  console.log("----------------")
})
onMounted(()=>{
  console.log("这是在组件挂载之后")
  console.log("----------------")
})
onBeforeUpdate(()=>{
  console.log("这是组件更新之前")
  console.log("----------------")
})
onUpdated(()=>{
  console.log("这是组件任意的DOM元素更新之后")
  console.log("----------------")
})
onBeforeUnmount(()=>{
  console.log("这是组件实例销毁之前")
  console.log("----------------")
})
onUnmounted(()=>{
  console.log("这是组件实例销毁之后")
})
</script>

<style scoped>
.zhong{
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);}
</style>