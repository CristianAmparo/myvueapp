<script setup>
import { defineProps } from "vue";
import { RouterLink } from "vue-router";

defineProps({
  title: String,
  description: String,
  color: String,
  offer: String,
  links: String,
});
</script>

<template>
  <div
    :class="[
      color !== 'green' ? 'bg-gray-100' : 'bg-green-100',
      'p-6 rounded-lg shadow-md',
    ]"
  >
    <h2 class="text-2xl font-bold">{{ title }}</h2>
    <p class="mt-2 mb-4">{{ description }}</p>
    <RouterLink
      :to="links"
      :class="[
        'inline-block  text-white rounded-lg px-4 py-2 ',
        color !== 'green'
          ? 'bg-black hover:bg-gray-700'
          : 'bg-green-400 hover:bg-green-600',
      ]"
    >
      {{ offer }}
    </RouterLink>
  </div>
</template>
