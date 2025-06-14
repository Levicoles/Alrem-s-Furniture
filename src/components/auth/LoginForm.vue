<script setup>
import { ref } from 'vue'
import { requiredValidator, emailValidator } from '@/utils/validitors';

const isPasswordVisible = ref(false)
const refVForm = ref()

const formDataDefault = {
  email: '',
  password: '',
}

const formData = ref({
  ...formDataDefault
})

const onSubmit = () => {
  // alert(formData.value.email)
}

const onFormSubmit = () => {
  refVForm.value?.validate().then(({valid}) =>{
    if(valid)
    onSubmit()
  })
}
</script>

<template>
    <v-form ref="refVForm" @submit.prevent="onFormSubmit">
            <v-col cols="12">
              <v-text-field
                v-model="formData.email"
                label="Email" 
                variant="outlined" 
                prepend-inner-icon="mdi-email-outline"
                :rules="[requiredValidator, emailValidator]"
                ></v-text-field>
            </v-col>

            <v-col cols="12">
              <v-text-field 
                v-model="formData.password"
                prepend-inner-icon="mdi-lock-outline"
                label="Password" 
                :type="isPasswordVisible ? 'text' : 'password'"
                :append-inner-icon="isPasswordVisible ? 'mdi-eye-closed' : 'mdi-eye'" 
                @click:append-inner="isPasswordVisible = !isPasswordVisible"
                variant="outlined" 
                :rules="[requiredValidator]"
                > 
              </v-text-field>
            </v-col>
            
              <v-btn class="mt-2" type="submit" block color="primary" prepend-icon="mdi-login">Log in</v-btn>
            </v-form>
</template>