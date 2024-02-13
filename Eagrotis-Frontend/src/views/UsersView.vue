

<template>
  <div>
    <div><h1>Users</h1></div>
    <table class="table" v-if="data && data.length > 0">
      <thead>
      <tr>
        <th>Id</th>
        <th>Username</th>
        <th></th>
        <th></th>
        <th></th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="entry in data" :key="entry[0].id">
        <td>{{ BigInt(entry[0].id) }}</td>
        <td>{{ entry[0].username }}</td>
        <!-- Χρήση του RouterLink -->
        <td><RouterLink :to="{ name: 'user', params: { userId: BigInt(entry[0].id) }}" class="RouterLink">More Details</RouterLink></td>
        <td></td>
        <td></td>
      </tr>
      </tbody>
    </table>

    <!-- Εμφάνιση μηνύματος φόρτωσης -->
    <div v-if="loading">Loading...</div>

    <!-- Εμφάνιση μηνύματος λάθους -->
    <div v-if="error">{{ error.message }}</div>
  </div>
</template>

<script setup>
import { useRemoteDataGET } from '@/composables/useRemoteDataGET.js';

// Φόρτωση δεδομένων από το API
const { data, error, loading } = useRemoteDataGET('http://localhost:3030/api/Admin/users', true);
</script>

<style>
.RouterLink {
  color: #007bff;
  text-decoration: none;
  cursor: pointer;
}

.RouterLink:hover {
  text-decoration: underline;
}

.table {
  width: 100%;
  border-collapse: collapse;
}

.table th,
.table td {
  border: 1px solid #cec1c1;
  padding: 8px;
  text-align: left;
}

.table th {
  background-color: #439af1;
}
</style>
