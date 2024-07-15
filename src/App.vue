<script setup>
import { reactive, ref } from 'vue';

import AllTasks from './components/AllTasks.vue';


const title = ref('')
const taskBody = ref('')
const massivTasks = reactive([])
const flagSwitch = ref(true)


for (let key in localStorage) {
  if (!localStorage.hasOwnProperty(key)) {
    continue; // пропустит такие ключи, как "setItem", "getItem" и так далее
  }
  massivTasks.push(JSON.parse(localStorage.getItem(key)))
  
}

console.log(massivTasks)



function switcher() {
  flagSwitch.value = !flagSwitch.value
}

function addTasksInLocaleStorage() {
  localStorage.setItem(Date.now(), JSON.stringify({
    title: title.value,
    taskBody: taskBody.value,
    id: Date.now()
  }))

  title.value = ''
  taskBody.value = ''

  setTimeout(() => {
    window.location.reload()
  }, 100)

  
  console.log(massivTasks)
}
</script>

<template class="app">
    <div class="TODO">TODO</div>
    <div class="container" v-if="flagSwitch">
      <input
       class="title" 
       v-model="title" 
       type="text" 
       placeholder="Enter a name">
      <textarea 
      v-model="taskBody" 
      class="taskBody" 
      placeholder="Enter a text"
      ></textarea>
      <div class="btns">
        <button class="tasks" @click="switcher">ALL TASKS</button>
        <button class="add" @click="addTasksInLocaleStorage">ADD A TASK</button>
      </div>
  </div>

  <AllTasks 
  :switching="switcher"
  :flag="flagSwitch"
  :TASKS="massivTasks"/>
</template>

<style scoped>
  @import url('./assets/app.css');
</style>
