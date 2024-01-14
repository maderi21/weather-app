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
import axios from "axios";

const searchQuery = ref("");
const queryTimeout = ref(null);

const getSearchResults = () => {
  queryTimeout.value = setTimeout(() => {
		if (queryTimeout.value !== '') {
			const result = await axios.get(`https://api.mapbox.com/search/geocode/v6/forward?q={search_text}`);
	}
},300);
};
</script>
