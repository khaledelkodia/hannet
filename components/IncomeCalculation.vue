<template>
  <div>
    <div class="containerInputs">
      <input
        v-model="salary"
        class="inputs"
        type="number"
        placeholder="  اكتب مرتبك  "
      />

      <input
        v-model="days"
        class="inputs"
        type="number"
        placeholder="  أيام العمل  "
      />

      <input
        v-model="hours"
        class="inputs"
        type="number"
        placeholder="  الساعات  "
      />

      <button @click="showResults" class="calc-btn">اعرف راتبك</button>
    </div>

    <div class="containerSalary">
      <div v-if="showResult" class="salary">
        {{ salary ? (salary / days).toFixed(2) : "0.00" }}
        <p class="text-lg">في اليوم</p>
      </div>

      <div v-if="showResult" class="salary">
        {{ salary ? (salary / days / hours).toFixed(2) : "0.00" }}
        <p class="text-lg">في الساعة</p>
      </div>

      <div v-if="showResult" class="salary">
        {{ salary ? (salary / days / hours / 60).toFixed(2) : "0.00" }}
        <p class="text-lg">في الدقيقة</p>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, watch } from "vue";

const salary = ref();
const days = ref();
const hours = ref();
const showResult = ref(false);

// Function to show results when button is clicked
const showResults = () => {
  if (salary.value && days.value && hours.value) {
    showResult.value = true; // Show results if inputs are filled
  } else {
    showResult.value = false; // Hide results if inputs are empty
  }
};

// Watch inputs to hide results if any field is cleared
watch([salary, days, hours], () => {
  if (!salary.value || !days.value || !hours.value) {
    showResult.value = false;
  }
});
</script>

<style scoped>
.containerSalary {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 48px;
  flex-wrap: wrap;
  direction: rtl;
}

.salary {
  width: 250px;
  height: 220px;
  background-color: var(--card-color);
  border-radius: 12px;
  padding: 20px;
  text-align: center;
  font-size: 40px;
  display: flex;
  justify-content: space-around;
  align-items: center;
  flex-direction: column;
}

.containerInputs {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 15px;
  flex-wrap: wrap;
  margin-bottom: 20px;
  direction: rtl;
}
.inputs {
  width: 200px;
  height: 60px;
  color: var(--card-color);
  border-radius: 12px;
  padding: 10px;
  text-align: center;
  font-size: 30px;
  border: none;
  -webkit-appearance: none;
  -moz-appearance: textfield;
  appearance: none;
}

.inputs::-webkit-outer-spin-button,
.inputs::-webkit-inner-spin-button {
  -webkit-appearance: none;
}

/* Button styling */
.calc-btn {
  width: 200px;
  height: 60px;
  background-color: #039be5;
  color: white;
  border: none;
  border-radius: 12px;
  font-size: 24px;
  cursor: pointer;
  text-align: center;
  transition: background-color 0.3s ease;
}

.calc-btn:hover {
  background-color: var(--card-color);
}
</style>
