<script setup>
import { ref, onMounted } from "vue";

const users = ref([]);

onMounted(async () => {
  try {
    const response = await fetch("http://localhost:3000/users");
    users.value = await response.json();
  } catch (error) {
    console.error("Error fetching users:", error);
  }
});
</script>

<template>
  <div>
    <h1>List of Users</h1>
    <ul>
      <li v-for="user in users" :key="user.id">
        {{ user.name }} - {{ user.email }}
      </li>
    </ul>
  </div>
</template>
