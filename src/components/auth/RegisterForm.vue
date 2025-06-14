<script setup>
import { ref } from 'vue'
import { requiredValidator, emailValidator, passwordValidator, confirmedValidator} from '@/utils/validitors';

const formDataDefault = {
  firstname: '',
  lastname: '',
  email: '',
  password: '',
  password_confirmation: '',
}

const formData = ref({
  ...formDataDefault
})

const isPasswordVisible = ref(false)
const isPasswordConfirmVisible = ref(false)
const refVForm = ref()

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
                    <v-row>
                        <v-col col="12" md="6">
                            <v-text-field v-model="formData.firstname" label="Firstname" variant="outlined"  prepend-inner-icon="mdi-account-outline" :rules="[requiredValidator]"></v-text-field>
                        </v-col>

                        <v-col cols="12" md="6">
                            <v-text-field v-model="formData.lastname" label="Lastname" variant="outlined" prepend-inner-icon="mdi-account-outline" :rules="[requiredValidator]"></v-text-field>
                        </v-col>
                    </v-row>
                    
                    <v-row>
                        <v-col cols="12" md="12">
                            <v-text-field
                            v-model="formData.email"
                            label="Email"
                            variant="outlined"
                            prepend-inner-icon="mdi-email-outline"
                            :rules="[requiredValidator, emailValidator]"
                            ></v-text-field>
                        </v-col>
                        </v-row>

                    <v-row>
                        <v-col cols="12" md="6">
                            <v-text-field 
                                v-model="formData.password"
                                prepend-inner-icon="mdi-lock-outline"
                                label="Password" 
                                variant="outlined" 
                                :type="isPasswordVisible ? 'text' : 'password'"
                                :append-inner-icon="isPasswordVisible ? 'mdi-eye-closed' : 'mdi-eye'" 
                                @click:append-inner="isPasswordVisible = !isPasswordVisible"
                                :rules="[requiredValidator, passwordValidator]"
                                ></v-text-field>
                        </v-col>    
                            
                        <v-col cols="12" md="6">
                            <v-text-field 
                                v-model="formData.password_confirmation"
                                prepend-inner-icon="mdi-lock-check-outline"
                                label="Confirm Password" 
                                variant="outlined"
                                :type="isPasswordConfirmVisible ? 'text' : 'password'"
                                :append-inner-icon="isPasswordConfirmVisible ? 'mdi-eye-closed' : 'mdi-eye'" 
                                @click:append-inner="isPasswordConfirmVisible = !isPasswordConfirmVisible"
                                :rules="[requiredValidator, confirmedValidator(formData.password_confirmation, formData.password)]"
                                ></v-text-field>
                        </v-col>
                    </v-row>
                    <v-btn 
                        class="mt-2" 
                        type="submit" 
                        block color="primary" 
                        prepend-icon="mdi-account-plus"
                        >Create account</v-btn>
                  </v-form>
</template>