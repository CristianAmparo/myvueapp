<script setup>
import Hero from "@/components/Hero.vue";
import HomeCards from "@/components/HomeCards.vue";
import JobListings from "@/components/JobListings.vue";
</script>

<template>
  <Hero name="Cristian" subtitle="Welcome to my Vue Website" />
  <HomeCards />
  <JobListings :limit="3" :show="true" />
</template>
