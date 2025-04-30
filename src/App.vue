<script setup>
import { ref } from 'vue'
import LoginForm from './components/Auth/LoginForm/LoginForm.vue'
import RegistrationForm from './components/Auth/RegistrationForm/RegistrationForm.vue'
import CreateNewPlaceModal from './components/CreateNewPlaceModal/CreateNewPlaceModal.vue'
// import HomePage from './views/HomePage.vue'
// import FavoritePlaces from './components/FavoritePlaces/FavoritePlaces.vue'

const isOpen = ref(true)

const openModal = () => {
  isOpen.value = true
}

const closeModal = () => {
  isOpen.value = false
}
</script>

<template>
  <button @click="openModal" class="text-white">Click me</button>
  <!-- <HomePage /> -->
  <!-- <div class="h-screen w-[379px]"><FavoritePlaces></FavoritePlaces></div> -->
  <RegistrationForm @submit="console.log" />
  <LoginForm @submit="console.log" />
  <CreateNewPlaceModal :is-open="isOpen" @close="closeModal" @submit="console.log" />
</template>
