<template>
  <input
    type="text"
    v-model="newTask"
    placeholder="Ajouter une nouvelle tache"
    @keydown.enter="submitTask"
  />
</template>

<script setup lang="ts">
import { ref } from "vue";

const newTask = ref<string>("");
// const emit = defineEmits(['sendTask']); sans le typescripts
const emit = defineEmits<{
    (e:"sendTaskName" , value:string):void
}>();

 function submitTask(e:Event):void{
    if(newTask.value.trim()!==""){
    }
    emit('sendTaskName', newTask.value)
    newTask.value="";
console.log("donner envoyer");

 }
</script>

<style scoped>
input {
  padding: 5px;
  background-color: rgb(252, 248, 241);
  border: 1px solid rgb(73, 73, 231);
}
</style>

