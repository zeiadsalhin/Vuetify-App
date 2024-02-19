<script setup>
import { RouterLink, RouterView } from 'vue-router'
import { ref } from "vue"
import { useTheme } from 'vuetify/lib/framework.mjs';
import { onMounted } from 'vue';
import footer1 from "./components/footer.vue"
// import sidepanel from './components/sidepanel.vue'

//set automatic theme
onMounted(() => {
  if (!localStorage.getItem("data-theme")) {
    if (window.matchMedia("(prefers-color-scheme: dark)").matches) {
      localStorage.setItem('data-theme', "dark");
      document.documentElement.setAttribute('data-theme', "dark");
    } else {
      localStorage.setItem('data-theme', "light");
      document.documentElement.setAttribute('data-theme', "light");
    }
  }
})

const theme = ref(false)
const themelook = useTheme()

function changetheme() {

  theme.value = !theme.value
  themelook.global.name.value = theme.value ? "dark" : "light"
  document.documentElement.setAttribute('data-theme', themelook.global.name.value);
  localStorage.setItem('data-theme', themelook.global.name.value);
}
</script>

<template>
  <v-toolbar density="default">

    <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
    <v-toolbar-title><router-link to="/">Home</router-link></v-toolbar-title>

    <!-- <v-spacer></v-spacer> -->

    <v-btn icon @Click="changetheme">
      <v-icon :icon="theme ? 'mdi-weather-night' : 'mdi-weather-sunny'"></v-icon>
    </v-btn>

    <div class="d-flex justify-space-around m-2">
      <v-menu transition="slide-y-transition">
        <template v-slot:activator="{ props }">
          <v-btn icon v-bind="props">
            <v-badge content="6"><v-icon icon="mdi-bell"></v-icon></v-badge>
          </v-btn>
        </template>
        <v-list>
          <v-list-item v-for="(item, i) in items" :key="i">
            <v-list-item-title><v-icon :icon="item.icon"></v-icon>{{ item.title }}</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>
    </div>




    <v-btn to="/login" class="m-2">
      Login
    </v-btn>


  </v-toolbar>
  <v-fade-transition>
    <RouterView />

  </v-fade-transition>
  <footer1 />

  <v-layout>
    <v-navigation-drawer v-model="drawer" :rail="rail" temporary>
      <v-list-item prepend-avatar="https://randomuser.me/api/portraits/men/85.jpg" title="John Leider" nav>
        <template v-slot:append>
          <v-btn variant="text" icon="mdi-chevron-left" @click.stop="rail = !rail"></v-btn>
        </template>
      </v-list-item>

      <v-divider></v-divider>

      <v-list density="compact" nav>
        <v-list-item prepend-icon="mdi-home-city" title="Home" value="home" to="/"></v-list-item>
        <v-list-item prepend-icon="mdi-account" title="My Account" value="account" to="/register"></v-list-item>
        <v-list-item prepend-icon="mdi-account-group-outline" title="Users" value="users"></v-list-item>
        <v-list-item v-if="rail" prepend-icon="mdi-chevron-right" title="" value="expand"
          @click.stop="rail = !rail"></v-list-item>
      </v-list>
    </v-navigation-drawer>
  </v-layout>
</template>
<script>
export default {
  data() {
    return {
      drawer: false,
      rail: false,
    }
  },
}

const items = [
  { title: 'Message', icon: 'mdi-email' },
  { title: 'Click Me', icon: 'mdi-email' },
  { title: 'Click Me', icon: 'mdi-email' },
  { title: 'Click Me 2', icon: 'mdi-email' },
]
</script>
<style scoped></style>
