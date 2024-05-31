<template>
  <div class="container flex min-h-screen flex-col items-center justify-center border">
    <div class="border p-5">
      <h1 class="text-2xl font-bold uppercase">Ma Todo list</h1>
      <input
        type="text"
        class="rounded-lg border p-2"
        placeholder="Ajouter une nouvelle tâche"
        v-model="tache"
      />
      <button class="rounded-md bg-blue-400 px-2 py-1 text-white" @click="addTask">Ajouter</button>
    </div>
    <div class="border">
      <ul>
        <li v-for="{ id, name } in todo" :key="id">
          {{ name }} <button @click="deleteTask">Supprimer</button>
        </li>
      </ul>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, reactive } from 'vue';
const tache = ref('');

function addTask() {
  const newTask = tache;
  let id = 0;
  todo.push({
    id: id++,
    name: newTask,
    done: false
  });
  console.log(newTask);
  // console.log('Nouvelle tâche');
}

function deleteTask() {
  confirm('Confirmer la suppression de la tâche');
}

const todo = reactive([
  {
    id: 1,
    name: 'Ma premiere tache',
    done: false
  }
]);
</script>

<style scoped></style>
