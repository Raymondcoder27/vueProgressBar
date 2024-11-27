<script setup>
import { defineProps, ref, computed } from "vue";

const props = defineProps({
  data: {
    type: Object,
    required: true,
  },
});

// Reactive data copy
const data = ref({ ...props.data, steps: props.data.steps || [] });

// Adjust currentStep only if valid
if (data.value.currentStep > 0) {
  data.value.currentStep--;
}

const cssStyle = computed(() => ({
  "--active-color": data.value.activeColor || "#3b82f6",
  "--passive-color": data.value.passiveColor || "#d1d5db",
}));
</script>


<template>
  <div class="steps-container" :style="cssStyle">
    <ul class="steps-list">
      <li
        v-for="(step, index) in data.value.steps"
        :key="index"
        :class="{ '--stepActive': index === data.value.currentStep }"
      >
        <div class="step-bubble"></div>
        <div class="step-line">
          <div class="line-fill"></div>
        </div>
      </li>
    </ul>
  </div>
</template>
