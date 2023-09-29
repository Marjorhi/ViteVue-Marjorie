<script setup>
import { ref } from 'vue';

const firstName = ref('');
const lastName = ref('');
const birthday = ref('');
const selected = ref(''); // Added selected as a ref variable for gender
const submittedFirstName = ref('');
const submittedLastName = ref('');
const submittedBirthday = ref('');
const selectedGender = ref('');
const submissionTime = ref('');

const handleSubmit = () => {
  submittedFirstName.value = firstName.value;
  submittedLastName.value = lastName.value;
  submittedBirthday.value = birthday.value;
  selectedGender.value = selected.value;

  // Get the current date and time
  const currentTime = new Date();
  const formattedTime = `${currentTime.toLocaleDateString()} ${currentTime.toLocaleTimeString()}`;
  submissionTime.value = formattedTime;
};
</script>
  
 <template>
  <div id="app">
     <!-- First Name -->
  <div>
    <p>First Name</p>
    <input v-model="firstName" required>
    <!-- Display error message if the field is empty -->
    <p class="error" v-if="!firstName">First Name is required</p>
  </div>


  <!-- Last Name -->
  <div>
    <p>Last Name</p>
    <input v-model="lastName" required>
    <!-- Display error message if the field is empty -->
    <p class="error" v-if="!lastName">Last Name is required</p>
  </div>


  <!-- Birthday -->
  <div>
    <p>Birthday</p>
    <input type="date" v-model="birthday" required>
    <p class="error" v-if="!birthday">Birthday is required</p>
  </div>


  <!-- Gender -->
  <div>
    <p>Gender</p>
    <select v-model="selected" required>
      <option disabled value="">Please select one</option>
      <option value="female">Female</option>
      <option value="male">Male</option>
      <option value="other">Prefer not to say</option>
    </select>
    <p class="error" v-if="!selected">Gender is required</p>
  </div>

    <button @click="handleSubmit">Submit</button>

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
.error {
  color: red;
  font-size: 8px;
  margin-top: 5px;
}
.p {
  font: bold;
}
</style>

