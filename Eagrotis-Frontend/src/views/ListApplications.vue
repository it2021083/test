
<template>
  <div>
    <div v-if="loading">Loading...</div>
    <div v-if="error">Error loading applications: {{ error.message }}</div>
    <div><h1>Applications</h1></div>
      <table class="table" v-if="data && data.length > 0">
        <thead>
        <tr>
          <th>Id</th>
          <th>Name</th>
          <th>Status</th>
          <th></th>
          <th></th>
        </tr>
        </thead>
        <tbody>
        <tr v-for="entry in data" :key="entry.id">
          <td>{{ BigInt(entry.id) }}</td>
          <td>{{ entry.agriculturalCooperativeName }}</td>
          <td>{{entry.status}}</td>
          <td><RouterLink :to="{ name: 'application', params: { appId: entry.id }}">More Details</RouterLink></td>
          <td></td>
          <td></td>
        </tr>
        </tbody>
      </table>
    </div>
    <div v-if="data && data.length === 0">No applications available.</div>
</template>

<script setup>
import { ref } from 'vue';
import { useRemoteDataGET } from '@/composables/useRemoteDataGET';

const { data, error, loading } = useRemoteDataGET('http://localhost:3030/api/Employee/applications', true);
</script>


