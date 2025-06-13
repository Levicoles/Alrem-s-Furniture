<script setup>
import { ref } from 'vue'

const theme = ref('light')

function onClick () {
  theme.value = theme.value === 'light' ? 'dark' : 'light'
}
</script>

<template>
    <v-responsive class="border rounded">
    <v-app :theme="theme">
      <v-app-bar class="px-3">
        <v-spacer></v-spacer>

        <v-btn
          :prepend-icon="theme === 'light' ? 'mdi-weather-sunny' : 'mdi-weather-night'"
          text="Toggle Theme"
          slim
          @click="onClick"
        ></v-btn>
      </v-app-bar>

      <v-main>
        <v-container>
          <v-row>
            <v-col cols="12" md="6" class="mx-auto">
              <v-card
                class="mx-auto"
                prepend-icon="mdi-account-plus"
                subtitle="Login"
                elevation="24"
              >
                <template v-slot:title>
                  <span class="font-weight-black">Alrem's Furniture</span>
                </template>

                <v-card-text class="bg-surface-light pt-4">
                  <v-form fast-fail @submit.prevent>
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

                    <v-btn class="mt-2" type="submit" block>Submit</v-btn>
                  </v-form>

                  <v-divider class="my-5"></v-divider>

                  <h5 class="text-center">Already have account? <RouterLink to="/" class="text-primary">Click here to Login</RouterLink></h5>
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>
        </v-container>
      </v-main>

      <v-footer border app color="brown-darken-1" class="justify-center">2025 - Alrem's Furniture</v-footer>
    </v-app>
  </v-responsive>
</template>