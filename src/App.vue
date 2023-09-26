<script setup>
import { ref } from 'vue';


const text = ref('');
const submittedName = ref('');

const handleSubmit = () => {
  submittedName.value = text.value;
};
</script>

<template>
  <p>First Name</p>
  <input v-model="text">
  <button @click="handleSubmit">Submit</button>
  
  <!-- Display the submitted name -->
  <p> {{ submittedName }}</p>
</template>