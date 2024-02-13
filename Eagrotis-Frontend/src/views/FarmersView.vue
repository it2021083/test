<script setup>
import { useRemoteDataGET } from '@/composables/useRemoteDataGET.js';

// Φόρτωση δεδομένων από το API
const { data, error, loading } = useRemoteDataGET('http://localhost:3030/api/Admin/farmers', true);
</script>


<style scoped>
.RouterLink {
  color: #007bff;
  text-decoration: none;
  cursor: pointer;
}

.RouterLink:hover {
  text-decoration: underline;
}
</style>

<template>
  <div>
    <div><h1>Farmers</h1></div>
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
      <tr v-for="entry in data" :key="entry.id">
        <td>{{ entry.id }}</td>
        <td>{{ entry.username }}</td>
        <td><RouterLink :to="{name: 'farmer', params: { farmerId: entry.id }}" class="RouterLink">More Details</RouterLink></td>
        <td></td>
        <td></td>
      </tr>
      </tbody>
    </table>

    <template v-if="loading">
      Loading...
    </template>

    <template v-else-if="error">

      Error fetching data.
    </template>

    <template v-else-if="data && data.length === 0">

      No farmers found.
    </template>
  </div>
</template>


<!-------------------------------------------------------------------------------------------------->


<!--
<template>
  <div>
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
      <tr v-for="entry in data" :key="entry.id">
        <td>{{ entry.id }}</td>
        <td>{{ entry.username }}</td>
        <td><RouterLink :to="{ name: 'getFarmer', params: { farmerId: entry.id }}" class="RouterLink">More Details</RouterLink></td>
        <td></td>
        <td></td>
      </tr>
      </tbody>
    </table>

    <div v-if="loading">Loading...</div>

    <div v-if="error">{{ error.message }}</div>
  </div>
</template>

<script setup>
import { useRemoteDataGET } from '@/composables/useRemoteDataGET.js';

// Φόρτωση δεδομένων από το API
const { data, error, loading } = useRemoteDataGET('http://localhost:3030/api/Admin/farmers', true);
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
-->