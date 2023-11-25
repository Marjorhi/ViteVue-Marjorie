<script setup>
import { ref, computed } from 'vue';

const firstName = ref('');
const lastName = ref('');
const birthday = ref('');
const selected = ref(''); // Added selected as a ref variable for gender
const submittedFirstName = ref('');
const submittedLastName = ref('');
const submittedBirthday = ref('');
const selectedGender = ref('');
const submissionTime = ref('');

const isSubmitDisabled = computed(() => {
  return !firstName.value || !lastName.value || !birthday.value || !selected.value;
});

const handleSubmit = () => {
  if (!isSubmitDisabled.value) {
    submittedFirstName.value = firstName.value;
    submittedLastName.value = lastName.value;
    submittedBirthday.value = birthday.value;
    selectedGender.value = selected.value;

    // Get the current date and time
    const currentTime = new Date();
    const formattedTime = `${currentTime.toLocaleDateString()} ${currentTime.toLocaleTimeString()}`;
    submissionTime.value = formattedTime;
  }
};

const handleClear = () => {
  // Clear all form fields and reset submitted information
  firstName.value = '';
  lastName.value = '';
  birthday.value = '';
  selected.value = '';
  submittedFirstName.value = '';
  submittedLastName.value = '';
  submittedBirthday.value = '';
  selectedGender.value = '';
  submissionTime.value = '';
};
</script>

<template>
  <div id="app">
    <!-- First Name -->
    <div>
      <p>First Name</p>
      <input v-model="firstName" required>
      <!-- Display error message if the field is empty -->
      <p class="error" v-if="!firstName">Required!</p>
    </div>

    <!-- Last Name -->
    <div>
      <p>Last Name</p>
      <input v-model="lastName" required>
      <!-- Display error message if the field is empty -->
      <p class="error" v-if="!lastName">Required!</p>
    </div>

    <!-- Birthday -->
    <div>
      <p>Birthday</p>
      <input type="date" v-model="birthday" required>
      <p class="error" v-if="!birthday">Required!</p>
    </div>

    <!-- Gender -->
    <div>
      <p>Gender</p>
      <select v-model="selected" required>
        <option disabled value="">Please select one</option>
        <option value="Female">Female</option>
        <option value="Male">Male</option>
        <option value="Other">Prefer not to say</option>
      </select>
      <p class="error" v-if="!selected">Required!</p>
    </div>

    <button @click="handleSubmit" :disabled="isSubmitDisabled">Submit</button>
    <button @click="handleClear">Clear</button>

    <!-- Display submitted information and creation time conditionally -->
    <div v-if="submittedFirstName || submittedLastName || submittedBirthday || selectedGender || submissionTime">
      <p class="p">{{ submittedFirstName }} {{ submittedLastName }}</p>
      <p class="p">{{ submittedBirthday }}</p>
      <p class="p">{{ selectedGender }}</p>
      <p class="p">Created at: {{ submissionTime }}</p>
    </div>
  </div>
</template>

  
<style scoped>
  #app {
    max-width: 400px;
    margin: 0 auto;
    font-family: Arial, sans-serif;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
    background-color: #fff;
  }

  div > * {
    margin-bottom: 10px;
  }

  input,
  select {
    width: 100%;
    padding: 8px;
    font-size: 14px;
    border: 1px solid #ccc;
    border-radius: 4px;
    box-sizing: border-box;
  }

  button {
    padding: 8px 15px;
    background-color: #007bff;
    color: #fff;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    font-size: 14px;
    margin-right: 10px;
  }

  button:disabled {
    background-color: #ccc;
    cursor: not-allowed;
  }

  .error {
    color: red;
    font-size: 12px;
    margin-top: 2px;
  }

  .p {
    font-weight: bold;
    margin-bottom: 5px;
  }
</style>
