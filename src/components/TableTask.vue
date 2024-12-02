<!-- TableTask -->
<template>
  <table>
    <thead>
      <tr>
        <th>#</th>
        <th>Tâche</th>
        <th>Actions</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(task, index) in tasks" :key="index">
        <td>{{ index + 1 }}</td>
        <td>{{ task }}</td>
        <td>
          <button @click="deleteTask(index)">Supprimer</button>
          <button @click="doneTask(index)">{{ status}}</button>
        </td>
      </tr>
    </tbody>
  </table>
</template>
<script setup>
  import {ref} from "vue";
  const status = ref("Commencer");
  const props = defineProps({
    tasks: {
      type: Array,
      required: true,
    },
  });

  const emit = defineEmits(["delete-task"]);
  const deleteTask = (index) => {
    emit("delete-task", index);
  };
  const doneTask = (index) => {
    console.log(`Tâche ${index + 1} terminée!!`);
    switch(status.value){
      case "Commencer" :
        status.value = "En cours";
        break;
      case "En cours" :
        status.value = "Terminé";
        break;
    }
    
  };
</script>
<style scoped>
  table {
    width: 75%;
    margin: auto;
  }
  th, td {
    border: 1px solid black;
    padding: 5px;
  }
  button { 
    background-color: lightblue;
    border: none;
    padding: 5px;
    margin: 5px;
    border-radius: 4px;
    cursor: pointer;
  }
  button:hover {
    background-color: rgba(151, 224, 248, 0.868);
  }
</style>