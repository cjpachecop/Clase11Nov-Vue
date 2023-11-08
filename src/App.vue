<script setup>
import { ref } from "vue";
let newTask = ref('')
let taskList= ref([
{text: 'Estudiar', done:false},
{text: 'Jugar Play', done:true}])
function addTask(){
  if(newTask.value.trim() == '')return
  taskList.value.push({
    text: newTask.value,
    done: false
  })
  newTask.value = ''

}

function setDone(index){
  taskList.value[index].done = !taskList.value[index].done
  taskList.value.splice(index,1)
}
</script>

<template>
  <div class= "card">
    <h1>Lista de Cosas</h1>
    <p class="subtitule">{{newTask}}</p>
    <div>
  
  <div v-for="(task,index) in taskList" :key="index" class= "task " :class="{done: task.done}">{{task.text}}<span @click="setDone(index)" class= "button">x</span></div>

  </div>
 
  <div>
     <input v-model="newTask" @keypress.enter="addTask" type="text" placeholder="Escribe tu tarea" />
     <p class="help" v-show="newTask != ''">Presiona enter para confirmar</p>
  </div>
  </div>
  
</template>

<style scoped>
.done{
  text-decoration: line-through;
}

.help{
margin: 0;
font-size: 10px;
opacity: 0.4;

}




.button{
display: inline-flex;
align-items: center;
background-color: red;
padding: 0 5px;
border-radius: 2px;
color: white;

}

.button:hover{
cursor: pointer;
background-color: #9d007a;

}

.task{
background-color: green;
border-radius: 4px;
padding: 2px 8px;
padding-right: 2px;
margin-bottom: 2px;
display: flex;
justify-content: space-between;



}

.task:hover{
  background-color: blue;
}


.subtitule{
margin-bottom:16px;
padding: 0;
margin:0;
text-align:center;
opacity:0.6;
}


h1{
text-transform: uppercase;
text-align:center;
padding: 0;
margin:0;


}

.card{

  background-color: #f8EDE8;
  max-width: 520px;
  border-radius:8px;
  padding: 18px 16px;
  margin: 0 auto;
  font-family: 'Roboto', sans-serif;
}

input {
  width: 100%;
  box-sizing: border-box;
  border: none;
  outline: none;
   padding: 3px 6px;
   border-radius: 4px;
}


</style>
