<script setup>
const props = defineProps(['projectTitle'])
</script>

<template>
  <h1>{{ props.projectTitle }}</h1>

  <div></div>
</template>

<style scoped>
.progress-container {
  max-width: 400px;
  margin: 50px auto;
}

.progress-bar {
  display: flex;
  background-color: #eee;
  border-radius: 8px;
  overflow: hidden;
}

.progress-bar div {
  flex: 1;
  text-align: center;
  padding: 15px;
  color: #fff;
  position: relative;
  z-index: 1;
}

.progress-bar div:not(:last-child) {
  border-right: 2px solid #fff;
}

.step-active {
  background-color: #af514c; /* Green for active step */
}

.controls {
  margin-top: 20px;
  text-align: center;
}

.btn {
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
  background-color: #673ab7; /* Purple for button */
  color: #fff;
  border: none;
  border-radius: 5px;
  margin: 0 5px;
}

.btn:disabled {
  background-color: #ccc;
  cursor: not-allowed;
}
</style>
