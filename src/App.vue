<script setup lang="ts">
import { ref } from 'vue';

  const addTodo = ref<string>("");
  // const editTodo = ref<string>("");
  const todolist = ref([]);

  const add = () => {
    if (addTodo.value.trim() !== ""){
      todolist.value.push(addTodo.value);
      addTodo.value = '';
    }
  };

  const remove = (index: number) => {
    todolist.value.splice(index, 1);
  }

  // const edit = (index: number) => {
  //   todolist.value[index] = editTodo.value;
    
  // }
</script>

<template>

  <main>
    <header>
      <h1 class="font-bold text-center text-2xl">Todo List App</h1>
    </header>
    <div class="flex items-center justify-center">
      <div class="flex flex-col">
        <label for="todo">Todo</label>
        <input v-model="addTodo" class="border mt-2.5" type="text" name="todo" placeholder="Add Todo"/>
        <button @click="add" class="border mt-2.5 bg-green-500">Add</button>
        <div id="todo" class="mt-5">
          <li v-for="(todo,index) in todolist" :key="index" class="list-none">
            <div class="border p-2">
              {{ todo }}
              <div class="flex space-x-4">
                <button @click="remove(index)" class="border mt-2.5 bg-red-500">Delete</button>
                <button class="border mt-2.5 bg-blue-500">Edit</button>
              </div>
            </div>
            <br>
          </li>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>

</style>
