<template>
  <div class="one">
    <h2>sum的值为：{{sum}}</h2>
    <button @click="SunAdd">sum+1</button>
  </div>
</template>

<script setup name="One">
  import {ref,watch} from "vue";
  let sum = ref(0);
  function SunAdd(){
    sum.value = sum.value + 1
  }
  const stop = watch(sum, (newValue, oldValue) => {
    console.log(`sum的值发生了变化，旧的值为 ${oldValue}, 新的值为 ${newValue}`);
    if (newValue >= 10) {
      stop(); // 停止侦听
    }
  });

</script>

<style scoped>
  .one {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
</style>