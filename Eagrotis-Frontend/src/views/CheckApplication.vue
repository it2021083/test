<template>
  <div>
    <h1>Examine Application</h1>
    <form @submit.prevent="checkApplicationForm">
      <div>
        <label>Status:</label>
        <select v-model="tempStatus">
          <option value="UNSEEN">Unseen</option>
          <option value="DISPROVED">Disproved</option>
          <option value="APPROVED">Approved</option>
        </select>
      </div>
      <div>
        <label>Comments:</label>
        <textarea v-model="tempComment"></textarea>
      </div>
      <button type="submit" :disabled="loading">Submit</button>
    </form>

    <div v-if="data">Application checked successfully: {{ data }}</div>
    <div v-if="error">Error checking application: {{ error.message }}</div>
    <div v-if="loading">Checking...</div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { useRouter } from 'vue-router';
import { useRemoteDataPUT } from '@/composables/useRemoteDataUPDATE.js';
import {useApplicationStore} from "@/stores/application.js";

const store = useApplicationStore();

const router = useRouter();
const applicationId = router.currentRoute.value.params.id;

const loading = ref(false);

const checkApplication = ref({
  status: '',
  employee: '',
  comments: '',
});

const tempStatus = ref();
const tempComment = ref();

const checkApplicationForm = async () => {
// Log form data before API call
  console.log('Form data before submission:', checkApplication.value);


  const requestData = {
    status: tempStatus.value,
    comments: tempComment.value, // Use tempMembers instead of applicationForm.value.members
    employee: store.userData.username,
  };




  const { data, error, loading } =  useRemoteDataPUT(`http://localhost:3030/api/Employee/application/approval/${applicationId}`, true, requestData);

  // Assuming data is not null, check if data contains the expected response
  if (data) {
    // Log form data after API call
    console.log('Form data after submission:', data.status);
    console.log('Form submitted successfully:', data);

    router.push({name: 'application', params: {appId: applicationId}});

  } else {
    console.error('Error submitting form:', error.value);
  }
};
</script>
