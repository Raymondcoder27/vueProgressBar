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
      <li class="step" v-for="(step, index) in data.steps" :key="index">
      </li>
    </ul>
  </div>
</template>
