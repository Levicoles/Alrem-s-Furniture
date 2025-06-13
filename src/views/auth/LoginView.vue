<script setup>
import AppLayout from '@/components/layout/AppLayout.vue'
import { useDisplay } from 'vuetify';

const { mobile } = useDisplay()
</script>

<template>
  <AppLayout>
    <template #content>
      <v-row>
        <v-col cols="12" md="6" class="mx-auto pt-16">
          <v-card
            class="mx-auto"
            elevation="24"
          >

          <v-card-title class="text-center">
            <v-img class="mx-auto" src="images/logo-favicon.png" :width="mobile ? '50%' : '15%'"></v-img>
            <h3 class="font-weight-black">Alrem's Furniture</h3>
            <p>Login to continue</p>

          </v-card-title>

          <v-card-text class="bg-surface-light pt-4">
            <v-form fast-fail @submit.prevent>
              <v-divider class="my-5"></v-divider>
              <v-text-field 
                label="Email" 
                variant="outlined" 
                prepend-inner-icon="mdi-email-outline">
              </v-text-field>

              <v-text-field 
                label="Password" 
                type="password" 
                variant="outlined" 
                prepend-inner-icon="mdi-lock-outline"> 
              </v-text-field>

              <v-btn class="mt-2" type="submit" block color="primary" prepend-icon="mdi-login">Log in</v-btn>
            </v-form>

            <v-divider class="my-5"></v-divider>

              <h5 class="text-center">Don't have account? <RouterLink to="register" class="text-primary">Click here to Register</RouterLink> </h5>

          </v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </template>
    
  </AppLayout>       
</template>