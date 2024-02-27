<template>
    <div>
      <h2>Anime Quote</h2>
      <div v-if="isLoading">Loading...</div>
      <div v-else>
        <p><strong>Quote:</strong> {{ quote }}</p>
        <p><strong>Anime:</strong> {{ anime }}</p>
        <p><strong>Character:</strong> {{ character }}</p>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref, onMounted } from 'vue';
  
  const isLoading = ref(true);
  const quote = ref('');
  const anime = ref('');
  const character = ref('');
  
  onMounted(async () => {
    try {
      const response = await fetch('https://animechan.xyz/api/random');
      const data = await response.json();
      quote.value = data.quote;
      anime.value = data.anime;
      character.value = data.character;
      isLoading.value = false;
    } catch (error) {
      console.error('Error fetching data:', error);
      isLoading.value = false;
    }
  });
  </script>
  
  <style scoped>
  /* Add styling here */
  </style>
  