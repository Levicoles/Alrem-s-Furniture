<script setup>
import { ref } from 'vue'

const theme = ref('light')

function onClick () {
  theme.value = theme.value === 'light' ? 'dark' : 'light'
}
</script>

<template>
    <v-responsive>
    <v-app :theme="theme">
      <!-- <v-app-bar class="px-3">
        <v-spacer></v-spacer>

        <v-btn
          :prepend-icon="theme === 'light' ? 'mdi-weather-sunny' : 'mdi-weather-night'"
          text="Toggle Theme"
          slim
          @click="onClick"
        ></v-btn>
      </v-app-bar> -->

      <v-main>
        <v-container>
            <slot name="content"></slot>
        </v-container>
      </v-main>

      <v-footer border app color="brown-darken-1" class="justify-center font-weight-bold">2025 - Alrem's Furniture</v-footer>
    </v-app>
  </v-responsive>
</template>