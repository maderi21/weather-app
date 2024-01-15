<template>
  <main class="container text-white">
    <div class="pt-4 mb-4 relative">
      <input
        type="text"
        v-model="searchQuery"
        @input="getSearchResults"
        placeholder="Search for a city"
        class="py-2 px-1 bg-transparent border-b focus:border-weather-secondary focus:outline-none"
      />
    </div>
  </main>
</template>

<script setup>
import { ref } from "vue";
import axios from "axios";

const mapboxAPIKey =
  "pk.eyJ1IjoieGtvc3RvbGFuc2t5bSIsImEiOiJjbHJkdnlvM24xYW52Mm1ta3doMmQwZ2RxIn0.i4DbeJ5bm4s98O0seJkVbw";
const searchQuery = ref("");
const queryTimeout = ref(null);
const mapboxSearchResults = ref(null);

const getSearchResults = () => {
  setTimeout(queryTimeout.value);
  queryTimeout.value = setTimeout(async () => {
    if (queryTimeout.value !== "") {
      const result = await axios.get(
        `https://api.mapbox.com/geocoding/v5/mapbox.places/${searchQuery.value}.json?access_token=${mapboxAPIKey}`
      );
      mapboxSearchResults.value = result.data.features;
      return;
    }
    mapboxSearchResults.value = null;
  }, 300);
};
</script>
