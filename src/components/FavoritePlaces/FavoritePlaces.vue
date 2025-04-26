<script setup>
import { ref } from 'vue'
import FavoritePlace from '../FavoritePlace/FavoritePlace.vue'
import IButton from '../IButton/IButton.vue'

const buttonVariant = ref('bg-[#FFA279]')

const changeButtonVariant = () => {
  buttonVariant.value = buttonVariant.value === 'bg-[#FFA279]' ? 'outlined' : 'bg-[#FFA279]'
}
</script>

<template>
  <div class="px-6">
    <div class="text-[#939393] mb-4">Додані маркери</div>
    <slot name="list"><FavoritePlace :key="n" v-for="n in 4" /></slot>
    <IButton class="w-full mt-10" :variant="buttonVariant" @Click="changeButtonVariant"
      >Додати маркер</IButton
    >
  </div>
</template>
