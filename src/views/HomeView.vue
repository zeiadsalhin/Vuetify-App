<script setup>
// import sidepanel from '../components/sidepanel.vue'
</script>

<template>
  <v-carousel cycle class="">
    <v-carousel-item src="https://cdn.vuetifyjs.com/images/backgrounds/vbanner.jpg" cover>
      <div class="text justify-center md:p-20 p-12 space-y-3 text-white drop-shadow-2xl">
        <h1 class="text-5xl font-bold">Created with,</h1>
        <p
          class="inline-block text-4xl font-semibold text-green-700 drop-shadow-2xl bg-gray-100 p-1.5 rounded-md md:ml-36 ">
          Vue
        </p>
        <p class="text-4xl inline-block p-1">+</p>
        <p class="inline-block text-4xl font-semibold text-blue-300 drop-shadow-2xl p-1">Vuetify</p>
      </div>
    </v-carousel-item>
    <v-carousel-item src="https://cdn.vuetifyjs.com/images/cards/docks.jpg" cover></v-carousel-item>
    <v-carousel-item src="https://cdn.vuetifyjs.com/images/cards/hotel.jpg" cover></v-carousel-item>
  </v-carousel>

  <v-parallax class="mt-2" src="https://cdn.vuetifyjs.com/images/backgrounds/vbanner.jpg">
    <div class="d-flex flex-column fill-height justify-center align-center text-white">
      <h1 class="text-h4 font-weight-thin mb-4">
        Soon
      </h1>
      <h4 class="subheading">
        The new Progressive experience
      </h4>
    </div>
  </v-parallax>

  <v-divider></v-divider>
  <div class="rate flex-col space-y-5 mx-auto text-center p-2 mt-5">
    <p>Rate my work ;)</p>
    <v-rating hover :length="5" :size="32" :model-value="4" active-color="teal" />
  </div>
  <v-divider inset class="mx-auto"></v-divider>
</template>
