<template>
    <div class="box">
      <div class="input-box">
        <input type="text" placeholder="输入事件" v-model="inputthing">
        <button @click="add">添加</button>
      </div>
      <div class="liebiao">
      <ul v-if="inputlist.length!==0">
        <li v-for="item of inputlist" :key="item.id">{{ item.thing }}<button @click="del(item.id)">删除</button></li>
      </ul>
    </div>
    </div>
</template>
<script setup>
import {ref} from 'vue';
let inputlist=ref([{
  id:1,
  thing:"原神"
},{
  id:2,
  thing:"王者荣耀"
},{
  id:3,
  thing:"星穹"
}]);
let inputthing=ref("");
const del=(index)=>{
  inputlist.value=inputlist.value.filter(item=>item.id!==index);
}
const add=()=>{
  if(inputthing.value.length>0){
    inputlist.value.push({
    id:inputlist.value.length+1,
    thing:inputthing.value
  });
  }else{
    alert("请输入事件");
  }
  inputthing.value="";
}
</script>

<style scoped>
.input-box{
  width: 100%;
  display: flex;
  justify-content: center;
}
.input-box input{
  width: 50%;
  height: 30px;
  margin: 30px 5px;
  border-radius: 10px;
  border: 1px solid gray;
  box-shadow: 4px 4px 10px rgb(197, 193, 193);
}
.input-box input:focus{
  outline: none;
}
.box{
  width: 500px;
  height: 300px;
  border: 1px solid #000;
  top: 50%;
  left: 50%;
  position: absolute;
  transform: translate(-50%,-50%);
}
.input-box button{
  margin: 30px 10px;
  width: 50px;
  height: 35px;
  color: pink;
  background-color: aqua;
  border: none;
  border-radius: 12px;
  box-shadow: 4px 4px 2px gray;
}
button:hover{
  background-color: rgb(94, 93, 93);
}
button:active{
  box-shadow: 0 0 0 rgba(0, 0, 0, 0.4);
}
ul{
  list-style: none;
}
</style>