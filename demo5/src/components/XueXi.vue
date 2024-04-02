<template>
  <div style="background: azure ;height: 70px;display: flex;align-items: center;border-radius: 10px">
    <h3>学习计划表</h3>
  </div>
  <div style="background: azure ;height: 70px;display: flex;align-items: center;border-radius: 10px;margin-top: 10px">
    <div style="width: 400px;display: flex;height: 60px;align-items: center" >
      <div style="background: beige;height: 40px;display: flex;align-items: center">学习科目</div>
      <div style="height: 40px"><input type="text"  v-model="newLearn.kemu" style="height:36px;border-radius: 5px;border-style:none;box-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);"></div>
    </div>
    <div style="width: 400px;display: flex;height: 60px;align-items: center" >
      <div style="background: beige;height: 40px;display: flex;align-items: center">学习内容</div>
      <div style="height: 40px"><input type="text" v-model="newLearn.neirong" style="height:36px;border-radius: 5px;border-style:none;box-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);"></div>
    </div>
    <div style="width: 400px;display: flex;height: 60px;align-items: center" >
      <div style="background: beige;height: 40px;display: flex;align-items: center">学习地点</div>
      <select v-model="newLearn.didian"style="height: 36px; border-style: none;border-radius: 10px;box-shadow: 5px 5px 5px 0px rgba(0, 0, 0, 0.5);">
        <option value="明理楼">明理楼</option>
        <option value="科技楼">科技楼</option>
        <option value="图书馆">图书馆</option>
      </select>
    </div>
    <div>
      <button @click="add" style="background: cyan;border-radius: 10px;height: 30px;width: 90px;">添加</button>
    </div>
  </div>
  <div>
    <table style="width: 100%">
      <tr>
        <th>序号</th>
        <th>学习科目</th>
        <th>学习内容</th>
        <th>学习地点</th>
        <th>完成状态</th>
        <th>操作</th>
      </tr>
      <tr v-for="item in learn">
        <td>{{ item.id }}</td>
        <td>{{ item.kemu }}</td>
        <td>{{ item.neirong }}</td>
        <td>{{ item.didian }}</td>
        <td><input type="range" min="0" max="100" value="0">
        </td>
        <td><button @click="deleteLearn(item.id)">删除</button></td>
      </tr>
    </table>
  </div>
</template>

<script setup name="XueXi">
import {reactive, toRefs, watch} from "vue";
let learn = reactive([{id:'1',kemu:'数学',neirong:'aa',didian:'aa'}])
let newLearn={id:'',kemu:'',neirong:'',didian:''}
let cs=1
function add(){
  cs++
  let newObject = Object.assign({}, newLearn);
  newObject.id=cs
  learn.push(newObject); // 添加新对象到数组
  console.log(learn);
}
function deleteLearn(id){
  learn.splice(id-1,1)
}
watch(learn,(newValue,oldValue)=>{
  for (let i=0;i<learn.length;i++){
    learn[i].id=i+1
  }
})
</script>
<style scoped>
table {
  margin-top: 15px;
  width: 100%;
  border-collapse: collapse;
  border-radius: 10px;
}
th, td {
  border: 1px solid black;
  padding: 8px;
  text-align: center; /* 水平居中对齐 */
}
th {
  vertical-align: middle; /* 垂直居中对齐 */
}
</style>