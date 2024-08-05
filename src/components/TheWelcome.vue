<template>
  <div class="flex border boxizing">
    <h1>Bienvenue dans l'univers des taches</h1>
    <Form  @sendTaskName = "getTaskName"/>
    <TodoList  :getAllTodo=toDos />
  </div>
</template>

<script setup lang="ts">

import Form from "./FormComponent.vue";
import TodoList from "./TodoListComponent.vue";
import {nanoid} from 'nanoid'
import {ref} from 'vue'
import {Todo} from '../types'

// const toDos=ref<Array<Todo>>([])
const toDos = ref<Todo[]>([
  {id:nanoid(),text:"courir",isDone:true},
  {id:nanoid(),text:"danser",isDone:true},
  {id:nanoid(),text:"manger",isDone:false}
])


function getTaskName(taskName : string){
  console.log(taskName);
  const newTodo:Todo = {
    id:nanoid(),
    text:taskName,
    isDone:false
  }
  toDos.value.push(newTodo)
  console.log('recive'); 
}



</script>

<style>
.flex {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 20px;
}
.border {
  border: 2px solid rgb(73, 213, 231);
  border-radius: 20px;
}
.boxizing {
  padding-block: 20px;
  width: 50%;
  margin: 0 auto;
}
h1 {
  margin-top: -0rem;
  padding: 15px;
  max-width: 50%;
  left: 0;
  right: 0;
  text-align: center;
  background-color: rgb(73, 213, 231);
}
</style>