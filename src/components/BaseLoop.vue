
<template>
  <div>
    <button @click="addCountry" class="button">Add Country</button>
    <div v-if="selectedCountries.length === 0" class="message">No countries yet.</div>
    <div v-else v-for="(country, index) in selectedCountries" :key="index" class="country">
      {{ country }}
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

// List of country names
const countryNames = [
  'Afghanistan',
'Albania',
'Algeria',
'Andorra',
'Angola',
'Antigua and Barbuda',
'Argentina',
'Armenia',
'Australia',
'Austria',
'Azerbaijan',
'The Bahamas',
'Bahrain',
'Bangladesh',
'Barbados',
'Belarus',
'Belgium',
'Belize',
'Benin',
'Bhutan',
'Bolivia',
'Bosnia and Herzegovina',
'Botswana',
'Brazil',
'Brunei',
'Bulgaria',
'Burkina Faso',
'Burundi',
]

// Reactive state
const selectedCountries = ref([])

// Function to add a random country
function addCountry() {
  const randomIndex = Math.floor(Math.random() * countryNames.length)
  selectedCountries.value.push(countryNames[randomIndex])
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
  margin-bottom: 10px;
}

.message {
  color: #777;
  font-style: italic;
}

.country {
  margin-bottom: 5px;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
}
</style>

