<script setup>

import router from "@/router/index.js";
import {useRemoteDataGET} from "@/composables/useRemoteDataGET.js";

const appId = router.currentRoute.value.params.appId;


const { data, error, loading } = useRemoteDataGET(`http://localhost:3030/api/Employee/application/${appId}`, true);

</script>

<style>
.table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 20px;
}

th, td {
  padding: 15px;
  text-align: left;
  border-bottom: 1px solid #ddd;
}

thead {
  background-color: #f2f2f2;
}

tr:nth-child(even) {
  background-color: #f9f9f9;
}

tr:hover {
  background-color: #e5e5e5;
}

.RouterLink {
  color: #007bff;
  text-decoration: none;
  cursor: pointer;
}

.RouterLink:hover {
  text-decoration: underline;
}
</style>
<!--
<template>
  <div class="bg-body-tertiary">
    <div class="container">
      <div class="row py-4 px-3">
        <div class="col-12">
          <div class="mb-4">
            <h1 class="fs-3">Application's Details</h1>
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
              <RouterLink :to="{ name: 'check/application', params: { id: appId }}">Update</RouterLink>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
-->
<template>
  <div class="bg-body-tertiary">
    <div class="container">
      <div class="row py-4 px-3">
        <div class="col-12">
          <div class="mb-4">
            <h1 class="fs-3">Application's Details</h1>
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
                <td>
                  <!-- Check if the field is 'employee' or 'farmer' and display the relevant information -->
                  <template v-if="field === 'employee' || field === 'farmer'">
                    {{ value?.name }} ({{ value?.username }})
                  </template>
                  <template v-else>
                    {{ value }}
                  </template>
                </td>
              </tr>
              </tbody>
            </table>
            <div>
              <RouterLink :to="{ name: 'check/application', params: { id: appId }}">Update</RouterLink>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
