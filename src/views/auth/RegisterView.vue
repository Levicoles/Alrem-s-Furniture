<script setup>
import AppLayout from '@/components/layout/AppLayout.vue'
import { useDisplay } from 'vuetify';

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
                  <v-form fast-fail @submit.prevent>
                    <v-divider class="my-5"></v-divider>
                    <v-row>
                        <v-col md="6">
                            <v-text-field label="Firstname" variant="outlined"  prepend-inner-icon="mdi-account-outline">
                                
                            </v-text-field>
                        </v-col>
                        <v-col md="6">
                            <v-text-field label="Lastname" variant="outlined" prepend-inner-icon="mdi-account-outline"></v-text-field>
                        </v-col>
                    </v-row>

                    <v-text-field label="Email" variant="outlined" prepend-inner-icon="mdi-email-outline"></v-text-field>
                    
                    <v-text-field 
                        label="Password" 
                        type="password" 
                        variant="outlined" 
                        prepend-inner-icon="mdi-lock-outline"> 
                    </v-text-field>
                    
                    <v-text-field 
                        label="Confirm Password" 
                        type="password" 
                        variant="outlined"
                        prepend-inner-icon="mdi-lock-check-outline">
                    </v-text-field>

                    <v-btn class="mt-2" type="submit" block color="primary" prepend-icon="mdi-account-plus">Create account</v-btn>
                  </v-form>

                  <v-divider class="my-5"></v-divider>

                  <h5 class="text-center">Already have account? <RouterLink to="/" class="text-primary">Click here to Login</RouterLink></h5>
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>
        </template>
    </AppLayout>     
</template>