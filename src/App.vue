<script setup>
import { RouterLink, RouterView } from 'vue-router'
// import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <v-toolbar density="compact">
    <v-app-bar-nav-icon></v-app-bar-nav-icon>

    <v-toolbar-title><router-link to="/">Home</router-link></v-toolbar-title>

    <!-- <v-spacer></v-spacer> -->

    <v-btn to="/login">
      Login
    </v-btn>


  </v-toolbar>
  <v-fade-transition>
    <RouterView />
  </v-fade-transition>
</template>

<style scoped></style>
