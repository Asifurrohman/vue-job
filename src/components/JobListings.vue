<template>
    <section class="bg-blue-50 px-4 py-10">
        <div class="container-xl lg:container m-auto">
            <div class="h2 text-3xl font-bold text-green-500 mb-6 text-center">
                Browse Jobs
            </div>
            <!-- Tampilkan loading spinner saat loading-->
            <div v-if="!jobs.length" class="text-center text-gray-500 py-6">
                <PulseLoader />
            </div>
            <!-- Tampilkan data ketika selesai loading -->
            <div v-else class="grid grid-cols-1 md:grid-cols-3 gap-6">
                <JobListing v-for="job in jobs.slice(0, limit || jobs.length)" v-bind:key="job.id" :job="job"/>
            </div>
        </div>
    </section>
    <section v-if="showButton" class="m-auto max-w-lg my-10 px-6">
        <RouterLink to="/jobs" class="block bg-black text-white text-center py-4 px-6 rounded-xl hover:bg-gray-700">
            View All Jobs
        </RouterLink>
    </section>
</template>

<script setup>
import { ref, defineProps, onMounted } from 'vue'
import { RouterLink } from 'vue-router'
import PulseLoader from 'vue-spinner/src/PulseLoader.vue'
import axios from 'axios'

import JobListing from '@/components/JobListing.vue'

defineProps({
    limit: Number,
    showButton: {
        type: Boolean,
        default: false
    }
})

const jobs = ref([])
// console.log(jobs.value)

onMounted(async () => {
    try{
        const response = await axios.get('http://localhost:8000/jobs')
        jobs.value = response.data
    } catch(error){
        console.error('Error fetching jobs', error)
    }
})
</script>

<style scoped>

</style>