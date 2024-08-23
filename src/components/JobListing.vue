<script setup>
import { ref, defineProps, computed } from "vue";
import { RouterLink } from "vue-router";

const props = defineProps({
  job: Object,
});

const showFullDescription = ref(false);

const toggleShowmore = (index) => {
  showFullDescription.value = !showFullDescription.value;
};

const truncatedDescription = computed(() => {
  let description = props.job.description;
  if (!showFullDescription.value) {
    description = description.substring(0, 90) + "...";
  }
  return description;
});
</script>

<template>
  <div class="w-full bg-slate-50 shadow-lg space-y-3 rounded-lg p-5">
    <p>{{ job.type }}</p>
    <h3 class="font-bold text-xl mb-10">{{ job.title }}</h3>
    <p class="text-sm">
      {{ truncatedDescription }}
      <span @click="toggleShowmore" class="text-orange-600 cursor-pointer">{{
        showFullDescription ? "Less" : "More"
      }}</span>
    </p>
    <p class="text-orange-500">{{ job.salary }}</p>
    <div class="w-full bg-gray-400 h-0.5"></div>
    <p class="text-red-700 pb-5">{{ job.location }}</p>
    <RouterLink :to="'/jobs/' + job.id">
      <button
        class="py-2 w-full text-white rounded-lg bg-orange-500 hover:bg-orange-600"
      >
        Read More
      </button></RouterLink
    >
  </div>
</template>
