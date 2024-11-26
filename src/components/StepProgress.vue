<script setup>
  import { defineProps, ref } from 'vue';

  const props = defineProps({
    data: Object,
  })

  props.data.currentStep--;

  const data = ref(props.data);
</script>


<template>
  <div class="steps-container">
    <ul class="steps-list">
      <li class="step">
        <div class="step-content" :class="data.currentStep === 0 ? data.activeColor : data.inactiveColor">
          {{ data.steps[0] }}
        </div>
      </li>
    </ul>
  </div>
</template>
