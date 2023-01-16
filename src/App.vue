<script setup lang="ts">
import { ref, reactive } from "vue";
import Job from "./types/Job";
import JobList from "./components/JobsList.vue";
import OrderTerm from "./types/OrderTerms";

const name = ref("Juanjo");
const age = ref<string | number>(37);
const user = reactive({
  name: "Juanjo",
  age: 37 as string | number,
});
const jobs = ref<Job[]>([
  { title: "programmer", location: "Spain", salary: 20000, id: "1" },
  { title: "maths", location: "Portugal", salary: 40000, id: "2" },
  { title: "police", location: "France", salary: 30000, id: "3" },
]);
const order = ref<OrderTerm>("title");
function changeName(newName: string) {
  name.value = newName;
}
function changeAge(newAge: number | string) {
  age.value = newAge;
}
function handleClick(term: OrderTerm) {
  order.value = term;
}
</script>

<template>
  <div>Hello {{ name }} - {{ age }}</div>
  <button @click="changeName('Elena')">Change name</button>
  <button @click="changeAge(32)">Change age</button>
  <p>{{ jobs[0].location }}</p>
  <div class="app">
    <header>
      <div class="title">
        <h1>Jobs</h1>
      </div>
      <div class="order">
        <button @click="handleClick('title')">Order by title</button>
        <button @click="handleClick('salary')">Order by salary</button>
        <button @click="handleClick('location')">Order by location</button>
      </div>
    </header>
    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<style scoped>
header {
  text-align: center;
}
header .order {
  margin-top: 20px;
}
button {
  margin: 0 10px;
  color: #1195c9;
  border: 3px solid #1195c9;
  background: #d5f0ff;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
}
</style>
