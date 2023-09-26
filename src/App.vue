<script setup>
import { ref } from 'vue';

const firstName = ref('');
const lastName = ref('');
const birthday = ref('');
const selected = ref(''); // Added selected as a ref variable for gender
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
  <div>
    <p>Gender</p>
    <select v-model="selected">
      <option disabled value="">Please select one</option>
      <option value="female">FEMALE</option>
      <option value="male">MALE</option>
      <option value="other">OTHER</option>
    </select>
    <p v-if="selected === 'female'"></p>
    <p v-else-if="selected === 'male'"></p>
    <p v-else></p>
  </div>
  <button @click="handleSubmit">Submit</button>

  <!-- Display the submitted information -->
  <p>{{ submittedFirstName }} {{ submittedLastName }}</p>
  <p>{{ submittedBirthday }}</p>
  <p>{{ selected }}</p>
</template>
