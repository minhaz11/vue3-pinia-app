<template>
  <main>
    <header>
      <img src="./assets/logo.svg" alt="">
      <h1>Pinia task</h1>
    </header>

    <div class="new-task-form">
      <TaskForm />
    </div>


    <nav class="filter">
      <button @click="filter = 'all'">All task</button>
      <button @click="filter = 'favs'"> Fav tasks</button>
    </nav>

    <div class="task-list" v-if="filter === 'all'">
      <h5>All Task</h5>
      <div v-for="task in taskStore.tasks" :key="task.id">
        <TaskDetails :task="task" />
      </div>
    </div>
    <div class="task-list" v-if="filter === 'favs'">
      <h5>Favorite Task</h5>
      <div v-for="task in taskStore.favs" :key="task.id">
        <TaskDetails :task="task" />
      </div>
    </div>
  </main>
</template>


<script setup>

import { useTaskStore } from "./stores/TaskStore";
import TaskDetails from "./components/TaskDetails.vue";
import TaskForm from "./components/TaskForm.vue";
import { ref } from "vue";

const taskStore = useTaskStore();

const filter = ref("all");

  
</script>

