

<script setup>
import { ref } from 'vue';

import { useRemoteDataGET } from '@/composables/useRemoteDataGET.js';
import router from "@/router/index.js";

const userIdFromPath = router.currentRoute.value.params.farmerId;
const { data, error, loading } = useRemoteDataGET(`http://localhost:3030/api/Admin/farmers/${userIdFromPath}`, true);
</script>

<style>


.RouterLink:hover {
  transform: scale(1.1); /* ή άλλη κλίμακα που θέλετε */
}
</style>
<template>
  <div class="bg-body-tertiary">
    <div class="container">
      <div class="row py-4 px-3">
        <div class="col-12">
          <div class="mb-4">
            <h1 class="fs-3">Farmer's Details</h1>
          </div>
          <div v-if="loading">Loading...</div>
          <div v-if="error">Error loading data: {{ error.message }}</div>
          <div v-if="data">
            <table class="table">
              <thead>
              <tr>
                <th>Field</th>
                <th>Value</th>
              </tr>
              </thead>
              <tbody>
              <tr v-for="(value, field) in data" :key="field">
                <td>{{ field }}</td>
                <td>{{ value }}</td>
              </tr>
              </tbody>
            </table>
            <div>
              <RouterLink :to="{ name: 'farmer/update', params: { id: userIdFromPath }}">Update</RouterLink>
            </div>
            <div>   <RouterLink :to="{ name: 'farmer/delete', params: { id: userIdFromPath }}">Delete</RouterLink>
            </div>

          </div>
        </div>
      </div>
    </div>
  </div>
</template>
