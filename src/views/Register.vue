<script setup>
import router from "@/router";
import { ref } from "vue";
import { useRouter } from "vue-router";
import Login from "./Login.vue";
const form = ref({
    name: '',
    email: '',
    pass: '',
    remember: false,
})

const isloading = ref(false)

function submit() {
    isloading.value = true
    setTimeout(() => {
        isloading.value = false
        alert(JSON.stringify(form.value))
        router.push({ path: '/login', replace: true })
    }, 3000);
}
</script>
<template>
    <v-overlay :model-value="isloading" class="mx-auto flex items-center justify-center h-screen">
        <v-progress-circular indeterminate color="white"></v-progress-circular></v-overlay>
    <div style="margin: auto;" class="flex items-center justify-center h-[85vh]">


        <v-card class="pa-4 mx-auto" width="350">


            <v-card-title class="text-center">Create new Account</v-card-title>
            <v-card-item>

                <v-form v-model="form" @submit.prevent="submit">
                    <v-text-field type="text" :rules="[required]" variant="solo" prepend-inner-icon="mdi-account"
                        v-model="name" label="Name"></v-text-field>
                    <v-text-field type="email" :rules="[required]" variant="solo" prepend-inner-icon="mdi-email"
                        v-model="email" label="Email"></v-text-field>
                    <v-text-field type="password" :rules="[required]" variant="solo" prepend-inner-icon="mdi-key"
                        v-model="password" label="Password"></v-text-field>
                    <!-- <v-checkbox v-model="remember" label="Remember me"></v-checkbox> -->
                    <v-btn color="red-darken-1" :disabled="!form" type="submit" block class="mt-2">
                        <!-- <v-progress-circular v-if="isloading" indeterminate color="white" class="m-2"></v-progress-circular> -->
                        <span>Create</span></v-btn>
                </v-form>

            </v-card-item>

            <v-card-action>
                <div class="mx-4">
                    <V-btn block to="/login">Have account? Login</V-btn>
                </div>
            </v-card-action>

        </v-card>

    </div>
</template>
<script>
export default {
    data: () => ({
        form: false,
        name: '',
        email: null,
        password: null,
        remember: false,
        // loading: false,
    }),

    methods: {
        submit() {
            if (!this.form) return

        },
        required(v) {
            return !!v || 'Field is required'
        },
    },
}
</script>