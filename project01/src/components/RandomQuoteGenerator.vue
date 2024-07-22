<script setup>
import { ref, onMounted } from 'vue'

const props = defineProps(['projectTitle'])
const quotes = ref([
  {
    text: 'The only way to do great work is to love what you do.',
    author: 'Steve Jobs'
  },
  {
    text: "Believe you can and you're halfway there.",
    author: 'Theodore Roosevelt'
  },
  {
    text: "Life is what happens when you're busy making other plans.",
    author: 'John Lennon'
  },
  {
    text: 'To be, or not to be, that is the question.',
    author: 'William Shakespeare'
  },
  {
    text: 'The only thing we have to fear is fear itself.',
    author: 'Franklin D. Roosevelt'
  },
  {
    text: 'It does not matter how slowly you go as long as you do not stop.',
    author: 'Confucius'
  },
  {
    text: 'What we think, we become.',
    author: 'Buddha'
  },
  {
    text: 'The purpose of our lives is to be happy.',
    author: 'Dalai Lama'
  }
])

const currentQuote = ref({ text: '', author: '' })

const getRandomQuote = () => {
  const randomIndex = Math.floor(Math.random() * quotes.value.length)
  currentQuote.value = quotes.value[randomIndex]
}

onMounted(getRandomQuote)
</script>

<template>
  <h1>{{ props.projectTitle }}</h1>

  <div class="quote-generator">
    <blockquote class="quote-container">
      <p>{{ currentQuote.text }}</p>
      <cite>- {{ currentQuote.author }} -</cite>
    </blockquote>

    <button class="quote-button" @click="getRandomQuote">Get Random Quote</button>
  </div>
</template>

<style scoped>
.quote-generator {
  max-width: 400px;
  margin: 50px auto;
  padding: 20px;
  text-align: center;
  border: 1px solid #ccc;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.app-title {
  font-size: 24px;
  margin-bottom: 20px;
  color: #333;
}

.quote-container {
  background-color: #f9f9f9;
  padding: 20px;
  border-radius: 8px;
  border: 1px solid #ddd;
  margin-bottom: 20px;
}

p {
  font-size: 18px;
  margin-bottom: 10px;
}

cite {
  font-style: normal;
  color: #777;
}

.quote-button {
  padding: 10px 20px;
  font-size: 16px;
  background-color: #3498db;
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.quote-button:hover {
  background-color: #2980b9;
}
</style>
