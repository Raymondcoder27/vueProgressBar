<script setup>
import StepProgress from "./components/StepProgress.vue";
import { ref } from "vue";

const stepProgress = ref();

const dataSteps = {
  steps: ["Step 1", "Step 2", "Step 3", "Step 4"],
  currentStep: 1,
  activeColor: "#3b82f6",
  passiveColor: "#d1d5db",
};
</script>

<template>
  <div class="mt-5">
    <p class="text-center font-bold text-gray-600">Fill the form please</p>
  <StepProgress :data="dataSteps" ref="stepProgress" />
  <div class="text-center justify-evenly">
    <button @click="stepProgress.previousStep" class="bg-blue-500 text-white rounded-md p-1 mr-2 mt-3 text-sm font-semibold">Previous Step</button>
    <button @click="stepProgress.nextStep" class="bg-blue-500 text-white rounded-md p-1 mt-3 text-sm font-semibold">Next Step</button>
  </div>

</div>
</template>