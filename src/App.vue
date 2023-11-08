<script setup>
import { ref } from 'vue';

let newTask = ref ('')
let taskList = ref([
  {
    name:'Estudiar',
    done: true
    
  },
{
    name:'Comer',
    done: false
  },

{  name:'Dormir',
   done: false}])
  


function addTask(){
  if(newTask.value.trim()==='')return
  taskList.value.push(newTask.value)
  newTask.value =''
}

function setDone(index){
  taskList.value[index].done = true
  newTask.value = ''

}

</script>

<template>

  <div class="container">
    <h1>LISTA DE TAREAS</h1>
    <p class="subtitle">{{ newTask }}</p>

    <div>
      <div class="task" :class="{done:task.done}" v-for="(task,index) in taskList" :key="index">{{task.name}}<span @click="setDone(index)" class="button">x</span></div>    
    </div>
  <input v-model="newTask" @keypress.enter="addTask" type="text" placeholder="Escriba su tarea">
  <p v-show="newTask!=''" class="help">Presiona Enter para agregar la tarea</p>
  </div>
</template>

<style scoped>
.done{
  text-decoration: line-through;
}
.help{
  font-size: 10px;
  opacity: 0.6;
  margin: 0;
}
.container{
  color: beige;
  padding: 6px 12px;
  background-color: #1A6566 ;
  border-radius: 6px;
  max-width: 420px;
  margin: 0 auto;

}
.button{
  background-color: #45214A;
  display: inline-block;
  padding: 0 6px;
  border-radius: 3px;
}
.button:hover{
  cursor: pointer;
}
.task{
 display: flex;
justify-content: space-between;
 background-color: #5D8A66;
 border-radius: 3px;
 margin-bottom: 1px;
 padding: 2px 2px 1px 6px;
}
input{
  border: none;
  border-radius: 3px;
  padding: 2px 6px;
  outline: none;
  width: calc(100% - 12px);
  margin-top: 12px;
}
input::placeholder{
  opacity: 0.4;
}
.task:hover{
  background-color: rgba(242, 178, 99, 0.8);
 

}
.subtitle{
  font-size: 10px;
  margin: 0;
  margin-bottom: 16px;
  text-align: center;
  opacity: 0.6;
}

h1{
  text-transform: uppercase;
  font-size: 18px;
  text-align: center;
  margin: 0;
  margin-top: 12px;
}

</style>
