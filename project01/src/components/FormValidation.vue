<script setup>
import { ref, computed } from 'vue'

const props = defineProps(['projectTitle'])
const formData = ref({
  name: '',
  email: '',
  password: ''
})
const formMessage = ref('')
const formSuccess = ref(false)

const isInit = ref(true)
const isNameValid = computed(() => formData.value.name.trim() !== '')
const isEmailValid = computed(() => /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(formData.value.email))
const isPasswordValid = computed(() => formData.value.password.trim().length >= 8)

const submitForm = () => {
  isInit.value = false
  const isFormValid = computed(
    () => isNameValid.value && isEmailValid.value && isPasswordValid.value
  )

  if (isFormValid.value) {
    formSuccess.value = true
    formMessage.value = `<b>Form submitted successfully!</b><br>${formData.value.name}<br>${formData.value.email}<br>${formData.value.password}`
  } else {
    formMessage.value = '<b>Form is invalid!</b><br>Please check the fields.'
  }
}
</script>

<template>
  <h1>{{ props.projectTitle }}</h1>

  <div class="custom-form">
    <div v-if="!formSuccess">
      <form @submit.prevent>
        <div class="form-group">
          <label for="name">Name:</label>
          <input v-model="formData.name" type="text" id="name" />
          <span v-if="!isInit && !isNameValid" class="error">Name is required</span>
        </div>

        <div class="form-group">
          <label for="email">Email:</label>
          <input v-model="formData.email" type="email" id="email" />
          <span v-if="!isInit && !isEmailValid" class="error"
            >Please enter a valid email address</span
          >
        </div>

        <div class="form-group">
          <label for="password">Password:</label>
          <input v-model="formData.password" type="password" id="password" />
          <span v-if="!isInit && !isPasswordValid" class="error"
            >Password must be at least 8 characters</span
          >
        </div>

        <button type="submit" class="submit-button" @click="submitForm">Submit</button>
      </form>
    </div>
    <div v-else v-html="formMessage" class="form-message"></div>
  </div>
</template>

<style scoped>
.custom-form {
  max-width: 400px;
  margin: 0 auto;
}

.form-group {
  margin-bottom: 20px;
}

.form-message {
  text-align: center;
}

label {
  display: block;
  font-weight: bold;
  margin-bottom: 5px;
}

input {
  width: 100%;
  padding: 10px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.error {
  color: #e74c3c;
  font-size: 14px;
  margin-top: 5px;
}

.submit-button {
  padding: 10px 15px;
  font-size: 16px;
  background-color: #3498db;
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.submit-button:disabled {
  background-color: #bdc3c7;
  cursor: not-allowed;
}
</style>
