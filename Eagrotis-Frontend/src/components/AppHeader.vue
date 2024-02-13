<!--<script setup>
import { RouterLink } from 'vue-router';
import { useApplicationStore } from '@/stores/application.js';
const applicationStore = useApplicationStore();
</script>

<template>
    <header class="text-bg-dark">
        <div class="container">
            <div class="d-flex flex-wrap justify-content-center py-2 px-3">
                <a
                    href="/"
                    class="d-flex align-items-center mb-3 mb-md-0 me-md-auto link-body-emphasis text-decoration-none"
                >
                    <span class="fs-5 fw-bolder text-white">API Client</span>
                </a>
                <ul class="nav nav-pills">-->
                    <!-- @EXERCISE: Add different color to active link (improve UX/UX). -->
                    <!-- @EXERCISE: Add different color to active link with nested routes (improve UX/UX). -->
                    <!-- @EXERCISE: Hide links that users has no access to. -->
                    <!--<li class="nav-item" v-if="applicationStore.isAuthenticated === true">
                        <router-link :to="{ name: 'home' }" class="nav-link text-white"
                            >Home</router-link
                        >
                    </li>
                    <li class="nav-item" v-if="applicationStore.isAuthenticated === true">
                        <router-link :to="{ name: 'users' }" class="nav-link text-white"
                            >Users</router-link
                        >
                    </li>-->
                    <!--
                    <li class="nav-item" v-if="applicationStore.isAuthenticated === true">
                        <router-link :to="{ name: 'courses' }" class="nav-link text-white"
                            >Courses</router-link
                        >
                    </li>-->
                    <!--<li class="nav-item" v-if="applicationStore.isAuthenticated === true">
                        <router-link :to="{ name: 'profile' }" class="nav-link text-white"
                            >Profile
                            <span style="font-size: 10px"
                                >({{ applicationStore.userData?.username }})</span
                            ></router-link
                        >
                    </li>
                    <li class="nav-item" v-if="applicationStore.isAuthenticated === false">
                        <router-link :to="{ name: 'login' }" class="nav-link text-white"
                            >Login</router-link
                        >
                    </li>
                    <li class="nav-item" v-if="applicationStore.isAuthenticated === true">
                        <router-link :to="{ name: 'logout' }" class="nav-link text-white"
                            >Logout</router-link
                        >
                    </li>
                </ul>
            </div>
        </div>
    </header>
</template>
-->



<!--
<script setup>

import { RouterLink } from 'vue-router';
import { useApplicationStore } from '@/stores/application.js';

const applicationStore = useApplicationStore();
</script>

<style scoped>
/* Στυλ για το header */
.head1 {
  background-color: #2c3e50;
  color: white;
  padding: 10px 0;
}

/* Στυλ για το container */
.container1 {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 15px;
}

/* Στυλ για τα κουμπιά σύνδεσης/αποσύνδεσης */
.auth-buttons {
  display: flex;
  align-items: center;
}
</style>

<template>
  <header class="text-bg-dark">
    <div class="container">

      <div class="d-flex flex-wrap justify-content-center py-2 px-3">

        <a
            href="/"
            class="d-flex align-items-center mb-3 mb-md-0 me-md-auto link-body-emphasis text-decoration-none"
        >
          <span class="fs-5 fw-bolder text-white">API Client</span>
        </a>


          <ul class="auth-buttons-l">
            <li class="auth-button-item" v-if="applicationStore.isAuthenticated">
              <router-link  to="/profile" class="nav-link text-white"> Profile </router-link>
            </li>
            <li class="auth-button-item" v-if="!applicationStore.isAuthenticated">
              <router-link  to="/login" class="nav-link text-white"> Login </router-link>
            </li>
            <li class="auth-button-item" v-if="applicationStore.isAuthenticated">
              <router-link  to="/logout" class="nav-link text-white"> Logout </router-link>
            </li>
          </ul>


      </div>

    </div>
  </header>
</template>
-->


<script setup>
import { RouterLink } from 'vue-router';
import { useApplicationStore } from '@/stores/application.js';
const applicationStore = useApplicationStore();
</script>


<style scoped>
/* Στυλ για το header */
.mainHeader {
  background-color: greenyellow;
  padding: 10px 0;
}

/* Στυλ για το container */
.headerContainer {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 15px;
}

/* Στυλ για τα κουμπιά σύνδεσης/αποσύνδεσης */
.nav-item {
  display: flex;
  align-items: center;
}
</style>

<template>
  <header class="mainHeader">
    <div class="headerContainer
">
      <div class="d-flex flex-wrap justify-content-center py-2 px-3">
        <a
            href="/"
            class="d-flex align-items-center mb-3 mb-md-0 me-md-auto link-body-emphasis text-decoration-none"
        >
          <span class="fs-5 fw-bolder text-green-700">E-AGROTIS</span>
        </a>
        <ul class="nav nav-pills">
          <!-- @EXERCISE: Add different color to active link (improve UX/UX). -->
          <!-- @EXERCISE: Add different color to active link with nested routes (improve UX/UX). -->
          <!-- @EXERCISE: Hide links that users has no access to. -->




          <li class="nav-item" v-if="applicationStore.isAuthenticated === true">
            <router-link :to="{ name: 'profile' }" class="nav-link text-black"
            >Profile
              <span style="font-size: 10px"
              >({{ applicationStore.userData?.username }})</span
              ></router-link
            >
          </li>
          <li class="nav-item" v-if="applicationStore.isAuthenticated === false">
            <router-link :to="{ name: 'login' }" class="nav-link text-black"
            >Login</router-link
            >
          </li>
          <li class="nav-item" v-if="applicationStore.isAuthenticated === true">
            <router-link :to="{ name: 'logout' }" class="nav-link text-black"
            >Logout</router-link
            >
          </li>
        </ul>
      </div>
    </div>
  </header>
</template>