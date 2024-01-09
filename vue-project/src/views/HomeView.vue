<template>
  <main class="container text-white">
    <div class="pt-4 mb-4 relative">
      <input
        type="text"
        v-model="searchQuery"
        placeholder="Search for a city"
        class="py-2 px-1 bg-transparent border-b focus:border-weather-secondary focus:outline-none"
      />
    </div>
  </main>
</template>

<script setup>
import { ref } from "vue";

const searchQuery = ref("");
</script>
