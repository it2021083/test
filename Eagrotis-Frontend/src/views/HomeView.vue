<script setup>
import { useApplicationStore } from '@/stores/application.js';
 const applicationStore = useApplicationStore();
</script>

<style>
  .bg-body {
    background-color: black;
  }

.container1 {
  background-color: black;
  margin-top: 20px;
}

.row {
  background-color: darkgreen;
  color: white;
  padding: 20px;
}

.fs-3 {
  font-size: 1.5rem;
  color: white; /* Χρώμα κειμένου */
}

.link{
  color: black;
  margin-top: 20px;
}

.auth-buttons a {
  color: black;
  //margin-right: 15px;
  //text-decoration: none;
  //font-weight: bold;
  //font-size: 16px;
}

.auth-buttons a:hover {
  color: white; /* Αλλαγή χρώματος κατά το hover */
}
</style>
<template>
    <div class="bg-body">
        <div class="container1">
            <div class="row py-4 px-3">
                <div class="col-12">
                    <div class="mb-4">
                        <h1 class="fs-3">Home</h1>
                    </div>
                    <div>
                        <p>
                            Logged in as: <strong>{{ applicationStore.userData.username }}</strong>
                        </p>
                        <ul>
                            <li>Welcome to Eagrotis App</li>
                            <li> Logged in as: <strong>{{ applicationStore.userData.name }}</strong></li>
                            <li v-if="applicationStore.isAdmin()"><router-link  to="/users" class="link">Users</router-link></li>
                            <li v-if="applicationStore.isAdmin()"><router-link  to="/getFarmers" class="link">Farmers</router-link>
                            </li>
                          <li v-if="applicationStore.isAdmin()"><router-link  to="/getEmployees" class="link">Employees</router-link></li>
                          <li v-if="applicationStore.isEmployee()"><router-link  to="/applications" class="link">Applications</router-link></li>
                          <li v-if="applicationStore.isFarmer()"><router-link  to="/sumbitApplication" class="link">New Application</router-link></li>
                          <li v-if="applicationStore.isFarmer()"><router-link  to="/get/not" class="link">My Applications</router-link></li>
                          <li v-if="applicationStore.isAdmin()"><router-link  to="/signup" class="link">Register new user</router-link></li>
                        </ul>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
