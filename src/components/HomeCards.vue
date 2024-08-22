<script setup>
import Cards from "./Cards.vue";
</script>

<template>
  <section class="py-4">
    <div class="container-xl lg:container m-auto">
      <div class="grid grid-cols-1 md:grid-cols-2 gap-4 p-4 rounded-lg">
        <Cards
          title="For Developers"
          description="Browse our Vue jobs and start your career today"
          offer="Browse Jobs"
          color="white"
          links="/jobs"
        />
        <Cards
          title="For Employers"
          description="List your job to find the perfect developer for the role"
          offer="Add Job"
          color="green"
          links="/jobs/add"
        />
      </div>
    </div>
  </section>
</template>
