<script setup>
import { ref } from 'vue';

const firstName = ref('');
const lastName = ref('');
const birthday = ref('');
const submittedFirstName = ref('');
const submittedLastName = ref('');
const submittedBirthday = ref('');

const handleSubmit = () => {
  submittedFirstName.value = firstName.value;
  submittedLastName.value = lastName.value;
  submittedBirthday.value = birthday.value;
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
  <div>
    <p>Birthday</p>
    <input type="date" v-model="birthday">
  </div>
  <button @click="handleSubmit">Submit</button>

  <!-- Display the submitted names -->
  <p>{{ submittedFirstName }} {{ submittedLastName }}</p>
  <p>{{ submittedBirthday }}</p>
</template>
