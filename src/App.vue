<script setup>
import { RouterLink, RouterView } from 'vue-router'
import { ref, onMounted } from 'vue'
import axios from 'axios'

import Navbar from '@/components/Navbar.vue'


</script>

<template>
  <Navbar />

  <RouterView />
</template>

<style scoped>

</style>
