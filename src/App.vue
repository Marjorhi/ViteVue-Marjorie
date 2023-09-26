<script setup>
import { ref } from 'vue';

const firstName = ref('');
const lastName = ref('');
const submittedFirstName = ref('');
const submittedLastName = ref('');

const handleSubmit = () => {
  submittedFirstName.value = firstName.value;
  submittedLastName.value = lastName.value;
};
</script>

<template>
  <div>
    <p>First Name</p>
    <input v-model="firstName">
  </div>
  <div>
    <p>Last Name</p>
    <input v-model="lastName">
  </div>
  <button @click="handleSubmit">Submit</button>

  

  <!-- Display the submitted names -->
  <p>{{ submittedFirstName }} {{ submittedLastName }}</p>
</template>
