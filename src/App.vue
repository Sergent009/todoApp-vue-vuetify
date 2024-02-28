<template>
  <v-app id="inspire">
    <v-navigation-drawer v-model="drawer" app>
  <v-list-item title="My Application" subtitle="Vuetify">Vuetify Todo</v-list-item>
  <v-divider></v-divider>
  <v-list-item link title="List Item 1" :to="homePage.to">Todo</v-list-item>
  <v-list-item link title="List Item 2" :to="aboutPage.to">About</v-list-item>
    </v-navigation-drawer>

    <!-- <v-app-bar app> -->
      <!-- <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

      <v-app-bar-title>Application</v-app-bar-title> -->
    <!-- </v-app-bar> -->

     <v-app-bar
        app
        color="primary"
        dark
        src="mountains.jpg"
        prominent
      >
        <template v-slot:img="{props}">
          <v-img
          v-bind="props"
            gradient="to top right, rgba(19,84,122,.8), rgba(128,208,199,.8)"
          ></v-img>
        </template>

        <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
        <v-app-bar-title>Vuetify Todo</v-app-bar-title>

        <v-spacer></v-spacer>

        <v-btn icon>
          <v-icon>mdi-magnify</v-icon>
        </v-btn>

        <v-btn icon>
          <v-icon>mdi-heart</v-icon>
        </v-btn>

        <v-btn icon>
          <v-icon>mdi-dots-vertical</v-icon>
        </v-btn>
      </v-app-bar>

    <v-main>
      <router-view></router-view>
    </v-main>
  </v-app>
</template>

<script setup>
  import { ref } from 'vue'

  const drawer = ref(null)
</script>

<script>
  export default {
    data: () => ({
      drawer: null,
      // items: [
      //   {title: 'Todo', to: '/'},
      //   {title: 'About', to: 'about'}
      //   ]
      homePage: {to: '/'},
      aboutPage: {to: '/about'}
     }),
  }
</script>