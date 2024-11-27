<script setup>
  import StepProgress from './components/StepProgress.vue';

  const dataSteps = {
    steps: ['Step 1', 'Step 2', 'Step 3', 'Step 4'],
    currentStep: 2,
    activeColor: '#3b82f6',
    passiveColor: '#d1d5db',
  }

</script>

<template>
    <StepProgress :data="dataSteps" />
</template>