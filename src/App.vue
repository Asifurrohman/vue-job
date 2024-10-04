<script setup>
import { RouterLink, RouterView } from 'vue-router'
import { ref, onMounted } from 'vue'
import axios from 'axios'

import Navbar from '@/components/Navbar.vue'
import Hero from '@/components/Hero.vue'
import HomeCards from '@/components/HomeCards.vue'


</script>

<template>
  <Navbar />
  <Hero title="test title" subtitle="test subtitle"/>
  <HomeCards />
  <h1>vue jobs</h1>

  <!-- <RouterView /> -->
</template>

<style scoped>

</style>
