<script setup>
import LoginForm from './components/Auth/LoginForm/LoginForm.vue'
import RegistrationForm from './components/Auth/RegistrationForm/RegistrationForm.vue'

// import HomePage from './views/HomePage.vue'
// import FavoritePlaces from './components/FavoritePlaces/FavoritePlaces.vue'
</script>

<template>
  <!-- <HomePage /> -->
  <!-- <div class="h-screen w-[379px]"><FavoritePlaces></FavoritePlaces></div> -->
  <RegistrationForm @submit="console.log" />
  <LoginForm @submit="console.log" />
</template>
