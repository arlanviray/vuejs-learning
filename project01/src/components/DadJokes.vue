<script setup>
import { ref } from 'vue'
import axios from 'axios'

const props = defineProps(['projectTitle'])
const joke = ref(null)

const fetchJoke = async () => {
  try {
    const response = await axios.get('https://icanhazdadjoke.com/', {
      headers: { Accept: 'application/json' }
    })

    joke.value = response.data.joke
  } catch (error) {
    console.error('Error fetching data:', error)
  }
}
</script>

<template>
  <h1>{{ props.projectTitle }}</h1>

  <div class="dad-jokes-container">
    <button @click="fetchJoke" class="get-joke-button">
      <span v-if="joke">More Joke?</span><span v-else>Get Dad Joke</span>
    </button>
    <div v-if="joke" class="dad-joke">
      {{ joke }}
    </div>
  </div>
</template>

<style scoped>
.dad-jokes-container {
  max-width: 600px;
  margin: 0 auto;
}

.dad-jokes-title {
  font-size: 24px;
  color: #333;
  margin-bottom: 20px;
}

.get-joke-button {
  padding: 10px 15px;
  font-size: 16px;
  background-color: #3498db;
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;

  display: block;
  margin: 0 auto;
}

.get-joke-button:hover {
  background-color: #2980b9;
}

.dad-joke {
  border: 1px solid #ddd;
  border-radius: 4px;
  padding: 15px;
  margin-top: 20px;
  background-color: #f9f9f9;
  color: #333;
}
</style>
