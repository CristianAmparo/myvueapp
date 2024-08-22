<script setup>
import { defineProps } from "vue";

defineProps({
  name: String,
  subtitle: String,
});
</script>

<template>
  <section class="bg-orange-50 py-20 mt-20 mb-4">
    <div
      class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 flex flex-col items-center"
    >
      <div class="text-center">
        <h1
          class="text-4xl font-extrabold text-orange-600 sm:text-5xl md:text-6xl"
        >
          {{ name }} Vue Dev
        </h1>
        <p class="my-4 text-xl text-orange-600">
          {{ subtitle }}
        </p>
      </div>
    </div>
  </section>
</template>
