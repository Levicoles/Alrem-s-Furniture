<template>
    <v-form fast-fail @submit.prevent>
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
</template>