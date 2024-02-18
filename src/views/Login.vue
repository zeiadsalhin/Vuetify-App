<script setup>
import { ref } from "vue";

const form = ref({
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
    }, 3000);
}
</script>
<template>
    <v-overlay :model-value="isloading" class="mx-auto flex items-center justify-center h-screen">
        <v-progress-circular indeterminate color="white"></v-progress-circular></v-overlay>
    <div style="margin: auto;" class="flex items-center justify-center h-screen">


        <v-card class="pa-4 mx-auto" width="350">


            <v-card-title class="text-center">Login</v-card-title>
            <v-card-item>

                <v-form @submit.prevent="submit">
                    <v-text-field type="email" variant="solo" prepend-inner-icon="mdi-email" v-model="form.email"
                        label="email"></v-text-field>
                    <v-text-field type="password" variant="solo" prepend-inner-icon="mdi-key" v-model="form.pass"
                        label="password"></v-text-field>
                    <v-checkbox v-model="form.remember" label="Remember me"></v-checkbox>
                    <v-btn color="red-darken-1" type="submit" block class="mt-2">
                        <!-- <v-progress-circular v-if="isloading" indeterminate color="white" class="m-2"></v-progress-circular> -->
                        <span>Submit</span></v-btn>
                </v-form>

            </v-card-item>

            <v-card-action>
                <div class="mx-4">
                    <V-btn block to="/Register">Register</V-btn>
                </div>
            </v-card-action>

        </v-card>

    </div>
</template>