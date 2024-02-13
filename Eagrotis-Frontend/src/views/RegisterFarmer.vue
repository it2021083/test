<template>
  <div>
    <form @submit.prevent="signUpFarmer">
      <label for="username">Username:</label>
      <input type="text" id="username" v-model="username" required />

      <label for="name">Name:</label>
      <input type="text" id="name" v-model="name" required />

      <label for="password">Password:</label>
      <input type="password" id="password" v-model="password" required />

      <label for="birthDate">Birth Date:</label>
      <input type="date" id="birthDate" v-model="birthDate" required />

      <button type="submit" :disabled="loading">Sign Up</button>
    </form>

    <div v-if="error" class="error-message">{{ error }}</div>
    <div v-if="data" class="success-message">{{ data.message }}</div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { useRemoteDataPOST } from '@/composables/useRemoteDataPOST.js';
import { useRouter } from 'vue-router';

const router = useRouter();
const username = ref('');
const name = ref('');
const password = ref('');
const birthDate = ref('');
const loading = ref(false);
const error = ref(null);
const data = ref(null);

const signUpFarmer = async () => {
  loading.value = true;
  error.value = null;

  const response = useRemoteDataPOST('http://localhost:3030/api/auth/farmerSignUp', false, {
    username: username.value,
    name: name.value,
    password: password.value,
    birthDate: birthDate.value,
  });

  if (response.error) {
    error.value = response.error;

    router.push({name: 'home'});
  } else {
    data.value = response.data;
    // Optionally, you can redirect to a different page after successful signup
    router.push({name: 'login'});
  }

  loading.value = false;
};
</script>
