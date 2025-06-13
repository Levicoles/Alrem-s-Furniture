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
</template>