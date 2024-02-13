<template>
  <div>
    <form @submit.prevent="registerUser">
      <label for="username">Username:</label>
      <input type="text" id="username" v-model="username" required />

      <label for="name">Name:</label>
      <input type="text" id="name" v-model="name" required />

      <label for="password">Password:</label>
      <input type="password" id="password" v-model="password" required />

      <label for="birthDate">Birth Date:</label>
      <input type="date" id="birthDate" v-model="birthDate" required />

      <label for="role">Role:</label>
      <select id="role" v-model="role">
        <option value="ROLE_ADMIN">Admin</option>
        <option value="ROLE_FARMER">Farmer</option>
        <option value="ROLE_EMPLOYEE">Employee</option>
        <option value="ROLE_USER">User</option>
        <!-- Add more roles as needed -->
      </select>

      <button type="submit" :disabled="loading">Register</button>
    </form>

    <div v-if="error" class="error-message">{{ error }}</div>
    <div v-if="data" class="success-message">{{ data.message }}</div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { useRemoteDataPOST } from '@/composables/useRemoteDataPOST.js';
import {useRouter} from "vue-router";

const router = useRouter();

const username = ref('');
const name = ref('');
const password = ref('');
const birthDate = ref('');
const role = ref(''); // Set the default role as needed
const loading = ref(false);
const error = ref(null);
const data = ref(null);

const registerUser = async () => {
  loading.value = true;
  error.value = null;

  const response = useRemoteDataPOST('http://localhost:3030/api/auth/signup', false, {
    username: username.value,
    name: name.value,
    password: password.value,
    birthDate: birthDate.value,
    role: role.value,
  });

  if (response.error) {
    error.value = response.error;

    router.push({name: 'home'});
  } else {
    data.value = response.data;
    // Optionally, you can redirect to a different page after successful registration
    // router.push('/dashboard');
  }

  loading.value = false;
};
</script>

