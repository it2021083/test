<template>
  <div>
    <h1>Notifications</h1>
    <div v-if="loading">Loading...</div>
    <div v-if="error">Error loading notifications: {{ error.message }}</div>
    <div v-if="data && data.length > 0">
      <ul>
        <li v-for="notification in data" :key="notification.id">
          {{ notification.agriculturalCooperativeName }} - {{ notification.status }}
        </li>
      </ul>
    </div>
    <div v-if="data && data.length === 0">No notifications available.</div>
  </div>
</template>

<script setup>
import { useRemoteDataGET } from '@/composables/useRemoteDataGET.js';

const { data, error, loading } = useRemoteDataGET('http://localhost:3030/api/Farmer/get/not', true);
</script>