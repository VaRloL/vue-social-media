<template>
    <v-navigation-drawer persistent dark class="d-flex flex-column px-5" width="100px" app>
        <div class="d-flex flex-column">
            <v-btn to="/" icon class="align-self-center my-2">
                <v-img src="../assets/vueweblogo.png" width="60px"></v-img>
            </v-btn>
            <v-divider dark></v-divider>
            <v-btn to="/profile" icon class="align-self-center my-2">
                <v-icon x-large>mdi-account-outline</v-icon>
            </v-btn>
            <v-divider dark></v-divider>
            <v-btn to="/notifications" icon class="align-self-center my-2">
                <v-icon x-large>mdi-bell-outline</v-icon>
            </v-btn>
            <v-divider dark></v-divider>
            <v-btn to="/users" icon class="align-self-center my-2">
                <v-icon x-large>mdi-book-account-outline</v-icon>
            </v-btn>
        </div>
    </v-navigation-drawer>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
    name:"navDrawer"
})
</script>