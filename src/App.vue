<script setup>
import { ref } from "vue";
const newTodo = ref('')
const todos = ref([]);
const addTodo = () => {
  todos.value.push({
    title: newTodo.value,
    completed: false,
    date: Date.now
  })
  newTodo.value = ''
}
</script>
<template>
  <form action="" @submit.prevent="addTodo">
    <fieldset role="group"
      class="bg gradient-to-br from-gray-100 to-gray-200 p-50 flex justify-center item-center column">
      <div
        class="bg-white bg-opacity-50 backgrop-filter backdrop-blur-lg rounded-lg shadow-lg p-8 max-w-md w-full text-gray-800 ">
        <h1 class="text-4xl font-bold text-center mb-8 bg-blue-100">To-do List</h1>
        <div id="app" class="max-w-md mx-auto  font-sans">
          <div class="flex items-center mb-4">
            <input v-model="newTodo" type="text" class="flex-1  rounded-1 py-2 px-3 focus-outline-none text-gray-800"
              placeholder="Add a new task">
            <button :class="{ 'bg-gray-300 cursor-not-allowed': newTodo.length === 0, }"
              class="bg-blue-500 font-bold text-white px-4 py-2 rounded-r focus:outline-none">
              <i class="fas fa-plus"></i>
            </button>
          </div>
        </div>
        <div class="text-sm font-bold text-center mb-8 bg-blue-2<<00" v-if="todos.length === 0">
          You don't have tasks
        </div>
        <div v-else>
          <ul>
            <li v-for="todo in todos" :key="todo.date" class="flex items-center mb-4 font-mono">
              <label>
                <input type="checkbox">
                {{ todo.title }}
              </label>

            </li>
          </ul>
        </div>
      </div>
    </fieldset>

  </form>

</template>
<style scoped></style>
