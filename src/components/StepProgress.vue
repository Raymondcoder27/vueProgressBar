<script setup>
import { defineProps, ref, computed } from "vue";

const props = defineProps({
  data: Object,
});

props.data.currentStep--;

const data = ref(props.data);

const cssStyle = computed(() => {
  return {
    "--active-color": data.value.activeColor,
    "--passive-color": data.value.inactiveColor,
  };
});
</script>


<template>
  <div class="steps-container">
    <ul class="steps-list">
      <li class="step" v-for="(step, index) in data.steps" :key="index">
        <div class="step-bubble"></div>
        <div class="step-line">
          <div class="line-fill"></div>
        </div>
      </li>
    </ul>
  </div>
</template>
