<script setup>
import AppLayout from '@/components/layout/AppLayout.vue'
import { useDisplay } from 'vuetify';
import RegisterForm from '@/components/auth/RegisterForm.vue';

const { mobile } = useDisplay()
</script>

<template>
    <AppLayout>
        <template #content>
            <v-row>
            <v-col cols="12" md="6" class="mx-auto pt-3">
              <v-card
                class="mx-auto"
                elevation="24"
              >
                <v-card-title class="text-center">
                    <v-img class="mx-auto" src="images/logo-favicon.png" :width="mobile ? '50%' : '15%'"></v-img>
                    <h3 class="font-weight-black">Alrem's Furniture</h3>
                    <p>Create your account</p>
                </v-card-title>

                <v-card-text class="bg-surface-light pt-4">
                  <v-divider class="my-5"></v-divider>
                  
                  <RegisterForm></RegisterForm>

                  <v-divider class="my-5"></v-divider>

                  <h4 class="text-center">Already have account? <RouterLink to="/" class="text-primary">Click here to Login</RouterLink></h4>
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>
        </template>
    </AppLayout>     
</template>