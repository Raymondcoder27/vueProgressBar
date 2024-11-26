<script setup>
  import StepProgress from './components/StepProgress.vue';

  const data = {
    steps: ['Step 1', 'Step 2', 'Step 3', 'Step 4'],
  }
</script>

<template>
  <div>
    <StepProgress />
  </div>
</template>