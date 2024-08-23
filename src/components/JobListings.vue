<script setup>
import { ref, defineProps, onMounted } from "vue";
import JobListing from "./JobListing.vue";
import { RouterLink } from "vue-router";
import axios from "axios";

defineProps({
  limit: Number,
  show: Boolean,
});
const jobs = ref([]);

onMounted(async () => {
  try {
    const response = await axios.get("http://localhost:5000/jobs");
    jobs.value = response.data;
  } catch (error) {
    console(error);
  }
});
</script>

<template>
  <section class="mt-20">
    <div class="container mx-auto p-5">
      <h2 class="text-3xl font-bold text-orange-500 mb-5 text-center">
        Browse Jobs
      </h2>
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 mx-auto gap-5">
        <JobListing
          v-for="(job, index) in jobs.slice(0, limit || jobs.length)"
          :key="index"
          :job="job"
        />
      </div>
    </div>
  </section>
  <section v-if="show" class="">
    <div class="container mx-auto p-5 text-center w-full h-20">
      <RouterLink to="/jobs">
        <button class="bg-gray-700 text-white py-3 px-12 rounded-lg">
          View More Jobs
        </button>
      </RouterLink>
    </div>
  </section>
</template>
