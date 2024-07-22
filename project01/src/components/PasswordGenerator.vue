<script setup>
import { ref } from 'vue'

const props = defineProps(['projectTitle'])
const passwordLength = ref(12)
const includeUppercase = ref(true)
const includeNumbers = ref(true)
const includeSymbols = ref(true)
const generatedPasswordResult = ref('')

const generatePassword = () => {
  const lowercaseChars = 'abcdefghijklmnopqrstuvwxyz'
  const uppercaseChars = includeUppercase.value ? lowercaseChars.toUpperCase() : ''
  const numberChars = includeNumbers.value ? '0123456789' : ''
  const symbolChars = includeSymbols.value ? '!@#$%^&*()_+[]{}|;:,.<>?/~`' : ''

  const allChars = lowercaseChars + uppercaseChars + numberChars + symbolChars

  let password = ''
  for (let i = 0; i < passwordLength.value; i++) {
    const randomIndex = Math.floor(Math.random() * allChars.length)
    password += allChars[randomIndex]
  }

  generatedPasswordResult.value = password
}
</script>

<template>
  <h1>{{ props.projectTitle }}</h1>

  <div class="password-generator-container">
    <div class="group-input">
      <label for="length">Password Length:</label>
      <input type="number" id="length" v-model="passwordLength" min="4" max="32" />
    </div>
    <div class="group-input">
      <label for="includeUppercase">Include Uppercase:</label>
      <input type="checkbox" id="includeUppercase" v-model="includeUppercase" />
    </div>
    <div class="group-input">
      <label for="includeNumbers">Include Numbers:</label>
      <input type="checkbox" id="includeNumbers" v-model="includeNumbers" />
    </div>
    <div class="group-input">
      <label for="includeSymbols">Include Symbols:</label>
      <input type="checkbox" id="includeSymbols" v-model="includeSymbols" />
    </div>

    <button @click="generatePassword" class="generate-button">Generate Password</button>

    <div v-if="generatedPasswordResult" class="generated-password">
      <strong>Your Password:</strong> {{ generatedPasswordResult }}
    </div>
  </div>
</template>

<style scoped>
.password-generator-container {
  max-width: 400px;
  margin: 50px auto;
}

.group-input {
  display: flex;
  gap: 10px;
  margin-bottom: 15px;
}

.group-input label {
  width: 150px;
}

input {
  padding: 4px 8px;
}

.generate-button {
  margin-top: 20px;
  padding: 10px 15px;
  font-size: 16px;
  background-color: #3498db;
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.generate-button:hover {
  background-color: #2980b9;
}

.generated-password {
  margin-top: 10px;
  padding: 15px;
  border: 1px solid #ddd;
  border-radius: 4px;
  background-color: #f9f9f9;
  color: #333;
}
</style>
