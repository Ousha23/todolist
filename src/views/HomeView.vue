<!-- HomeView -->
<template>
  <div class="home">
    <TaskForm @add-task="addTask"/>
    <TableTask v-if="tasks.length > 0" :tasks="tasks" @delete-task="deleteTask"/>
    <p v-else>Aucune tâche saisie</p>
  </div>
</template>

<script setup>
  // @ is an alias to /src
  import {ref} from 'vue';
  import TaskForm from '@/components/TaskForm.vue';
  import TableTask from '@/components/TableTask.vue';

  const tasks = ref([]);

  const addTask = (task) => {
console.log("addTask")
    tasks.value.push(task);
  };

  const deleteTask = (index) => {
console.log("delete");
    tasks.value.splice(index, 1)
  };

</script>
