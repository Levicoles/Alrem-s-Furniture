<script setup>
import { ref } from 'vue'

const isPasswordVisible = ref(false)
const isPasswordConfirmVisible = ref(false)
</script>

<template>
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
                    
                    <v-row>
                        <v-col md="6">
                            <v-text-field 
                                prepend-inner-icon="mdi-lock-outline"
                                label="Password" 
                                variant="outlined" 
                                :type="isPasswordVisible ? 'text' : 'password'"
                                :append-inner-icon="isPasswordVisible ? 'mdi-eye-closed' : 'mdi-eye'" 
                                @click:append-inner="isPasswordVisible = !isPasswordVisible"
                                ></v-text-field>
                        </v-col>    
                            
                        <v-col md="6">
                            <v-text-field 
                                prepend-inner-icon="mdi-lock-check-outline"
                                label="Confirm Password" 
                                variant="outlined"
                                :type="isPasswordConfirmVisible ? 'text' : 'password'"
                                :append-inner-icon="isPasswordConfirmVisible ? 'mdi-eye-closed' : 'mdi-eye'" 
                                @click:append-inner="isPasswordConfirmVisible = !isPasswordConfirmVisible"
                                ></v-text-field>
                        </v-col>
                    </v-row>
                    <v-btn class="mt-2" type="submit" block color="primary" prepend-icon="mdi-account-plus">Create account</v-btn>
                  </v-form>
</template>