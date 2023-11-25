<template>
  <div>
    <button @click="addCount" class="button">Click to Generate Quote</button>
    <div v-if="counts.length === 0" class="message">No quotes yet.</div>
    <div v-else v-for="(c, index) in counts" :key="index" class="count-container">
      {{ c }} : "{{ generateQuote() }}"
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

// Quotes array
const quotes = [
  "Success is not final, failure is not fatal: It is the courage to continue that counts. - Winston Churchill",
  "The only way to do great work is to love what you do. - Steve Jobs",
  "Believe you can and you're halfway there. - Theodore Roosevelt",
  "We cannot solve problems with the kind of thinking we employed when we came up with them. Albert Einstein",
  "Learn as if you will live forever, live like you will die tomorrow. — Mahatma Gandhi",
  "When you change your thoughts, remember to also change your world. —Norman Vincent Peale",
  "Nature has given us all the pieces required to achieve exceptional wellness and health, but has left it to us to put these pieces together. —Diane McLaren"
]

// Reactive state
const counts = ref([0])

// Function to generate a random quote
function generateQuote() {
  const randomIndex = Math.floor(Math.random() * quotes.length)
  return quotes[randomIndex]
}

// Function that adds count and generates a quote
function addCount() {
  counts.value.push(counts.value[counts.value.length - 1] + 1)
}
</script>


<style scoped>
.button {
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 4px;
  padding: 8px 16px;
  font-size: 14px;
  cursor: pointer;
}

.message {
  color: #777;
  font-style: italic;
  margin-top: 10px;
}

.count-container {
  margin-top: 10px;
  border-bottom: 1px solid #ddd;
  padding-bottom: 10px;
}

.count {
  font-weight: bold;
}

.quote {
  color: #555;
  font-style: italic;
}
</style>

