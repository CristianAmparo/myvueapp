//This is Composition API
<script setup>
import { onMounted, ref } from "vue";

const name = "Cristian";
const age = "23";
const status = ref(true);
const tasks = ref(["Task 1", "Task 2", "Task 3", "Task 4"]);
const newTask = ref("");

const toggleMe = () => {
  status.value = !status.value;
};

const addTask = () => {
  if (newTask.value !== "") {
    tasks.value.push(newTask.value);
    newTask.value = "";
  } else {
    alert("You need to input task!");
  }
};

const deleteTask = (index) => {
  tasks.value.splice(index, 1);
};

const updateTask = (index) => {
  tasks.value.splice(index, 1, "new value");
};

onMounted(async () => {
  try {
    const response = await fetch("https://jsonplaceholder.typicode.com/todos");
    const data = await response.json();
    tasks.value = data.map((task) => task.title);
  } catch (error) {
    console.log(error);
  }
});
</script>

<template>
  <h1>Hello World {{ name + " " + age }} years old</h1>
  <button @click="toggleMe">click</button>
  <p v-if="status">Active</p>
  <p v-else="status">Inactive</p>

  <form @submit.prevent="addTask">
    <label for="newTask">Add Task</label>
    <input type="text" id="newTask" name="newTask" v-model="newTask" />
    <button type="submit">Submit</button>
  </form>
  <h3>Tasks</h3>
  <ul>
    <li v-for="(task, index) in tasks" :key="index">
      <span>{{ task }}</span>
      <button @click="updateTask(index)">update</button>
      <button @click="deleteTask(index)">delete</button>
    </li>
  </ul>
</template>

<style scoped></style>
