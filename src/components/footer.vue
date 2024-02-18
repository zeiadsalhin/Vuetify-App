<template>
    <!-- <v-footer class="bg-grey-lighten-1"> -->
    <div class="p-4 text-current">
        <v-row justify="center" no-gutters>
            <v-btn v-for="link in links" :key="link" variant="text" class="mx-2" rounded="xl">
                {{ link }}
            </v-btn>
            <v-col class="text-center mt-4" cols="12">
                {{ new Date().getFullYear() }} — <strong>Vuetify, Ziad</strong>
            </v-col>
        </v-row>
    </div>
    <!-- </v-footer> -->
</template>
<script>
export default {
    data: () => ({
        links: [
            'Home',
            'About Us',
            'Team',
            'Services',
            'Blog',
            'Contact Us',
        ],
    }),
}
</script>