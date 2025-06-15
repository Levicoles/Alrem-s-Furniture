<script setup>
import { ref } from 'vue'
import { requiredValidator, emailValidator } from '@/utils/validitors';
import { supabase, formActionDefault } from '@/utils/supabase';
import AlertNotification from '@/components/common/AlertNotification.vue'

const isPasswordVisible = ref(false)
const refVForm = ref()

const formDataDefault = {
  email: '',
  password: '',
}

const formData = ref({
  ...formDataDefault
})

const formAction = ref({
  ...formActionDefault
})

const onSubmit = async () => {
    formAction.value = { ...formActionDefault }
    formAction.value.formProcess = true

    const { data, error } = await supabase.auth.signInWithPassword({
      email: formData.value.email,
      password: formData.value.password,
})

  if(error){
    console.log(error)
    formAction.value.formErrorMessage = error.message
    formAction.value.formStatus = error.status
  }
  else if(data){
    console.log(data)
    formAction.value.formSuccessMessage = "Successfully Login Account."
    refVForm.value?.reset()
  }

  formAction.value.formProcess = false
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
    <AlertNotification
      :form-success-message="formAction.formSuccessMessage"
      :form-error-message="formAction.formErrorMessage"
    ></AlertNotification>

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
    
      <v-btn 
        class="mt-2" 
        type="submit" 
        block 
        color="primary" 
        prepend-icon="mdi-login"
        :disabled="formAction.formProcess"
        :loading="formAction.formProcess"
      >Log in
      </v-btn>
    </v-form>
</template>