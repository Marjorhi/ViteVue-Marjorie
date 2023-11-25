<template>
  <div>
    <button @click="addCount" class="button">Add Count</button>
    <div v-if="counts.length === 0" class="message">No counts yet.</div>
    <div v-else v-for="(c, index) in counts" :key="index" class="count-container">
      Count is: {{ c }}
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

// reactive state
const counts = ref([0])

// functions that mutate state and trigger updates
function addCount() {
  counts.value.push(counts.value[counts.value.length - 1] + 1)
}
</script>

<style>
.button {
  background-color: #4CAF50;
  color: white;
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
  border: none;
  border-radius: 4px;
  margin-bottom: 10px;
}

.message {
  font-size: 18px;
  color: #777;
  margin-top: 10px;
}

.count-container {
  margin-top: 10px;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 4px;
}
</style>
