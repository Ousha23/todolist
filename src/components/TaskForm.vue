<!-- TaskForm -->
 
<template>
  <div class="hello">
    <h3>Saisir une tâche</h3>
    <form @submit.prevent="submitTask">
      <input type="text" v-model="newTask" required>
      <button type="submit">Ajouter</button>
    </form>
  </div>
</template>

<script setup>
  import { ref } from 'vue';

  const newTask = ref("");

  const emit = defineEmits(["add-task"]);
  const submitTask = () => {
console.log("submit");
    if (newTask.value.trim() !== "") { 
      emit("add-task", newTask.value.trim());
      newTask.value = "";
    }
  };
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h3 {
    margin: 40px 0 0;
  }
  input {
    margin: 5px;
  }
  button {
    background-color: burlywood;
    border-radius: 5px;
    border: none;
    padding: 5px 10px;
  }
</style>
