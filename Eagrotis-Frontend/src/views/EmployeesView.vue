<script setup>
import { useRemoteDataGET } from '@/composables/useRemoteDataGET.js';

const { data, error, loading } = useRemoteDataGET('http://localhost:3030/api/Admin/employees', true);

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
</style>

<template>
  <div>
    <div><h1>Employees</h1></div>
    <table class="table" v-if="data && data.length > 0">
      <thead>
      <tr>
        <th>Id</th>
        <th>Name</th>
        <th></th>
        <th></th>
        <th></th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="(entry, index) in data" :key="index">
        <td>{{ BigInt(entry.id) }}</td>
        <td>{{ entry.username }}</td>
        <td><RouterLink :to="{ name: 'getEmployee', params: { id: entry.id }}">More Details</RouterLink></td>
        <td></td>
        <td></td>
      </tr>
      </tbody>
    </table>

  </div>
</template>