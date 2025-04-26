<script setup>
import IButton from '@/components/IButton/IButton.vue'
import IInput from '@/components/IInput/IInput.vue'
import { reactive, toRaw } from 'vue'
import FormContainer from '../FormContainer.vue'

const emit = defineEmits(['submit'])

const userData = reactive({
  email: '',
  password: '',
})
</script>

<template>
  <FormContainer
    @submit.prevent="emit('submit', toRaw(userData))"
    class="max-w-[500px] w-full p-10 bg-white"
  >
    <IInput
      class="mb-4"
      label="Електронна пошта"
      placeholder="example@gmail.com"
      v-model="userData.email"
    />
    <IInput label="Пароль" type="password" v-model="userData.password" />
    <IButton class="mt-10 w-full" variant="bg-[#FFA279]" type="submit">Увійти </IButton>
  </FormContainer>
</template>
