<template>
  <div class="age-calculator">
    <h2 class="title">Age Calculator</h2>
    <div class="form-container">
      <input type="date" v-model="dateOfBirth" class="date-input">
      <button @click="calculateAge" class="calculate-button">Calculate</button>
    </div>
    <p v-if="age" class="result">Your age is: {{ age }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      dateOfBirth: '',
      age: null
    };
  },
  methods: {
    calculateAge() {
      const today = new Date();
      const birthDate = new Date(this.dateOfBirth);
      const ageDate = new Date(today - birthDate);

      const years = ageDate.getUTCFullYear() - 1970;
      const months = ageDate.getUTCMonth();
      const days = ageDate.getUTCDate() - 1;
      const hours = ageDate.getUTCHours();
      const minutes = ageDate.getUTCMinutes();
      const seconds = ageDate.getUTCSeconds();

      this.age = `${years} years, ${months} months, ${days} days, ${hours} hours, ${minutes} minutes, ${seconds} seconds`;
    }
  }
};
</script>

<style scoped>
.age-calculator {
  max-width: 400px;
  margin: 0 auto;
  text-align: center;
  padding: 20px;
  background-color: #f2f2f2;
  border-radius: 10px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

.title {
  font-size: 24px;
  margin-bottom: 20px;
}

.form-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 20px;
}

.date-input {
  padding: 10px;
  border: none;
  border-radius: 5px;
  margin-bottom: 10px;
  width: 100%;
}

.calculate-button {
  padding: 10px 20px;
  background-color: #34495E;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  width: 100%;
}

.result {
  font-size: 18px;
  margin-top: 20px;
  padding: 10px;
  background-color: #41B883;
  color: white;
  border-radius: 5px;
  line-height: 1.4;
}
</style>
