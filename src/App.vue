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
        <li v-for="{ id, name, done } in todos" :key="id">
          {{ id }}{{ name }} {{ done }}<button @click="deleteTask(id)">Supprimer</button>
        </li>
      </ul>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, reactive, computed } from 'vue';
// création d'une propriété réactive pour stocker l'input
const tache = ref('');

const todosData = reactive([{ id: 1, name: 'test de task', done: false }]);
const todos = computed(() => todosData.values);

function addTask() {
  const newTask = tache.value;
  const getId = todos.value.length + 1;
  todos.value.push({
    id: getId,
    name: newTask,
    done: false
  });
  return todos;
}

function deleteTask(id) {
  confirm(`Confirmer suppression de la tâche ${id}`);
  todos.value = todos.value.filter((todo) => todo.id !== id);
  console.log('Task delete');
  return todos;
}
</script>

<style scoped></style>
