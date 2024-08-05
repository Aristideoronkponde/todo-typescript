<template>
  <div>
    <ul>
      <li v-for="todo,index in getAllTodo" :key="index">
        <input type="checkbox">
        <span>{{todo.text}}</span>
        <!-- <span>{{todo.isDone?"Traitée":"Non tritée"}}</span> -->
        <span class="sup" @click="remove(index)"> X </span>
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import { log } from "console";
import { Todo } from "../types";
import { ref} from "vue";

const props = defineProps<{
  getAllTodo: Todo[];
}>();
console.log(props.getAllTodo);
const todoList = ref<Array<Todo>>(props.getAllTodo)
// function remove(el:Todo):void{
// todoList.value = props.getAllTodo.filter((ownTodo:Todo)=>{
//   return ownTodo.id!==el.id
// })
// }
function remove(index:number):void{
props.getAllTodo.splice(index)
}
</script>

<style scoped>
.sup{
 padding: 5px;
 border: 2px solid;
 cursor: pointer;
 color: white;
 background-color: red;
 border-radius: 100%;
 margin-left: 10px;
 
}
li{
list-style-type: none;
}
</style>

