<script setup>
  import StepProgress from './components/StepProgress.vue';
  import { ref } from 'vue';

  const stepProgress = ref()

  const dataSteps = {
    steps: ['Step 1', 'Step 2', 'Step 3', 'Step 4'],
    currentStep: 1,
    activeColor: '#3b82f6',
    passiveColor: '#d1d5db',
  }

</script>

<template>
    <StepProgress :data="dataSteps" ref="stepProgress" />
    <div class="">
      <button @click="stepProgress.previousStep">Previous Step</button>
      <button @click="stepProgress.nextStep">Next Step</button>

      </div>
</template>