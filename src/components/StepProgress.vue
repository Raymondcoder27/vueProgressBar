<script setup>
import { defineProps, ref, computed, defineExpose } from "vue";

const props = defineProps({
  data: Object,
});

const data = ref(props.data);

const cssStyle = computed(() => {
  return {
    "--active-color": data.value.activeColor,
    "--passive-color": data.value.passiveColor,
  };
});

// Dynamically calculate the width of the line-fill
const getLineFillWidth = (index) => {
  if (index < data.value.currentStep - 1) return "100%";
  if (index === data.value.currentStep - 1) return "50%";
  return "0";
};

const nextStep = () => {
  if (data.value.currentStep < data.value.steps.length) {
    data.value.currentStep++;
  }
};

const previousStep = () => {
  if (data.value.currentStep > 1) {
    data.value.currentStep--;
  }
};

defineExpose({ nextStep, previousStep });
</script>


<template>
    <div class="steps-container" :style="cssStyle">
      <ul class="steps-list">
        <li
          class="step"
          v-for="(step, index) in data.steps"
          :key="index"
          :class="{
            'step-active': index === data.currentStep,
            'step-done': index < data.currentStep,
          }"
        >
          <div class="step-bubble">
            <div class="step-count">{{ index + 1 }}</div>
          </div>
          <div class="step-label mt-20">
            {{ step }}
          </div>
          <div class="step-line">
            <div
              class="line-fill"
              :style="{ width: getLineFillWidth(index) }"
            ></div>
          </div>
        </li>
      </ul>
    </div>
  </template>


.step {
    display: flex;
    align-items: center;
    flex-grow: 1;
    height: 60px;
    position: relative;
  }
  
  .line-fill {
    width: 0;
    background-color: var(--active-color);
    height: 5px;
    transition: width 0.3s ease-in-out;
  }
  
  .step-done .line-fill {
    width: 100%;
  }
  
  .step-active .line-fill {
    width: 50%;
  }
  