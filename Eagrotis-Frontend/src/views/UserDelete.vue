<script setup>
import { ref } from 'vue';
import { useRouter } from 'vue-router';
import { useRemoteDataDELETE } from '@/composables/useRemoteDataDELETE.js';

const loading = ref(false);
const router = useRouter();
const userIdFromPath = ref(null);

const onFormSubmit = async () => {
  loading.value = true;

  // Retrieve the id from the route params and set it to userIdFromPath
  userIdFromPath.value = router.currentRoute.value.params.id;

  // Log the userIdFromPath
  console.log('userIdFromPath:', userIdFromPath.value);

  // Construct the delete endpoint using the userIdFromPath
  const deleteEndpoint = `http://localhost:3030/api/Admin/users/delete-user/${userIdFromPath.value}`;

  // Use the delete function with the constructed endpoint
  useRemoteDataDELETE(deleteEndpoint, true);
  router.push({name: '/users'})
};
</script>

<template>
  <div class="bg-body-tertiary">
    <div class="container">
      <div class="row py-4 px-3">
        <div class="col-4">
          <div class="mb-4">
            <h1 class="fs-3">Delete User</h1>
          </div>
          <div>
            <h1>{{ userIdFromPath }}</h1>
          </div>
          <div class="spinner-border" role="status" v-if="loading">
            <span class="visually-hidden">Loading...</span>
          </div>
          <form v-else>
            <button @click="onFormSubmit" type="button" class="btn btn-danger">
              Delete
            </button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>
