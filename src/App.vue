<script setup>
  import StepProgress from './components/StepProgress.vue';

  const data = {
    steps: ['Step 1', 'Step 2', 'Step 3', 'Step 4'],
    currentStep: 1,
    activeColor: 'bg-blue-500',
    inactiveColor: 'bg-gray-200',
  }
</script>

<template>
  <div>
    <StepProgress />
  </div>
</template>