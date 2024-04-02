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

<script>
export default {
  name: "P67",
  data(){
    return{
      demo:1
    }
  },
  methods:{
    changeDemo(){
      if (this.demo==1){
        this.demo=0
      }else{
        this.demo=1
      }
    }
  },
  beforeCreate() {
    console.log("这是实例对象创建前")
    console.log("-------------")
  },
  created() {
    console.log("这是实例对象创建后")
    console.log("-------------")
  },
  beforeMount() {
    console.log("这是页面挂载前")
    console.log("-------------")
  },
  mounted() {
    console.log("这是页面挂载成功后")
    console.log("-------------")
  },
  beforeUpdate() {
    console.log("这是组件更新前")
    console.log("-------------")
  },
  updated() {
    console.log("这是组件中的任意DOM元素更新后")
    console.log("-------------")
  },
  beforeDestroy() {
    console.log("组件实例销毁前")
    console.log("-------------")
  },
  destroyed() {
    console.log("组件实例销毁后")
    console.log("-------------")
  }
}
</script>

<style scoped>
 .zhong{
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);}

</style>