<script setup lang="ts">
import { ref } from "vue";
import { RouterView } from "vue-router";

const items = [
  { title: "Click Me" },
  { title: "Click Me" },
  { title: "Click Me" },
  { title: "Click Me 2" },
];

const darkTheme = ref(false);

function changeTheme() {
  darkTheme.value = !darkTheme.value;
}
</script>

<template>
  <v-app>
    <v-toolbar density="compact">
      <v-app-bar-nav-icon></v-app-bar-nav-icon>

      <v-toolbar-title>
        <RouterLink to="/">My Image App</RouterLink>
      </v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon @click="changeTheme">
        <v-icon
          :icon="darkTheme ? 'mdi-weather-sunny' : 'mdi-weather-night'"
        ></v-icon>
      </v-btn>

      <v-menu transition="scale-transition">
        <template v-slot:activator="{ props }">
          <v-btn icon v-bind="props">
            <v-badge content="5" color="red-darken-2" size="x-small">
              <v-icon icon="mdi-bell" color="white"></v-icon>
            </v-badge>
          </v-btn>
        </template>
        <v-list>
          <v-list-item
            v-for="(item, index) in items"
            :key="index"
            :value="index"
          >
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>

      <v-btn to="/login" variant="outlined" size="small" text="Login"></v-btn>
    </v-toolbar>

    <v-main>
      <v-fade-transition>
        <RouterView />
      </v-fade-transition>
    </v-main>
  </v-app>
</template>
