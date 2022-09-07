<template>
  <nav>
    <v-toolbar app color="yellow accent-3">
      <v-app-bar-nav-icon @click='toggleDrawer'></v-app-bar-nav-icon>
      <v-toolbar-title>

      </v-toolbar-title>
      <v-spacer></v-spacer>

      <!-- dropdown menu -->
      <v-menu open-on-hover >
        <template v-slot:activator="{ props }">
          <v-btn color="brown lighten-1" v-bind="props">
            Dropdown
          </v-btn>
        </template>

        <v-list>
          <v-list-item v-for="(item, index) in items" :key="index" router :to="item.path" :prepend-icon="item.icon">
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>

      <v-btn href="https://www.youtube.com/watch?v=dQw4w9WgXcQ&ab_channel=RickAstley" target="_blank" flat
        color="primary">
        <span>Click for Fun</span>
      </v-btn>


    </v-toolbar>

    <v-navigation-drawer app v-model="drawer" color="yellow accent-3">
      <center>
        <br>
        <v-list-item-title>
          <h3>Ian Guilan B.Gaudier</h3>
        </v-list-item-title>
      </center>
      <img src="../assets/c.png" alt="Avatar" style="border-radius: 50%; width:200px; height: auto;">
        <br>
      <v-divider></v-divider>
      <v-list-item v-for="item in items" :key="item.title" router :to="item.path" :prepend-icon="item.icon">
        <v-list-item-title>{{ item.title }}</v-list-item-title>

      </v-list-item>

    </v-navigation-drawer>
  </nav>
</template>

<script setup>
import { ref } from 'vue'

const drawer = ref(false)

const items = ref([
  { title: 'Dashboard', icon: 'mdi-view-dashboard', path: '/' },
  { title: 'Math', icon: 'mdi-plus-one', path: '/basicMath' },
  { title: 'String App', icon: 'mdi-help-box', path: '/stringApp' },
  { title: 'Vuetify', icon: 'mdi-vuejs', path: '/vuetifyApp' },
  { title: 'About Me', icon: 'mdi-account', path: '/aboutmeApp' },
  { title: 'Axios', icon: 'mdi-alien', path: '/axiosdemo' },
])

function toggleDrawer() {
  return drawer.value = !drawer.value
}
</script>

<style>
</style>