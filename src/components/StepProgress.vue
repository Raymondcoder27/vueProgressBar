<script setup>
import { defineProps, ref, computed, defineExpose } from "vue";
import IconDone from "./icons/IconDone.vue";

const props = defineProps({
  data: Object,
});

// props.data.currentStep--;

const data = ref(props.data);

// const data = ref({ ...props.data });
// data.value.currentStep--;

const cssStyle = computed(() => {
  return {
    "--active-color": data.value.activeColor,
    "--passive-color": data.value.passiveColor,
  };
});

// const nextStep = () => {
//   if (data.value.currentStep < data.value.steps.length - 1) {
//     data.value.currentStep++;
//   }
// };

const nextStep = () => {
  if (data.value.currentStep < data.value.steps.length) {
    data.value.currentStep++;
  }
};


// const previousStep = () => {
//   if (data.value.currentStep > 0) {
//     data.value.currentStep--;
//   }
// };

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
      <!-- <li
        class="step"
        v-for="(step, index) in data.steps"
        :key="index"
        :class="
          (index == data.currentStep ? 'step-active' : '',
          index < data.currentStep ? 'step-done' : '',
          index == 0 && index == data.currentStep ? 'step-done-in-advance' : '')
        "
      > -->
      <li
        class="step"
        v-for="(step, index) in data.steps"
        :key="index"
        :class="
          (index == data.currentStep ? 'step-active' : '',
          index < data.currentStep ? 'step-done' : '',
          index == 0 && index == data.currentStep ? 'step-done-in-advance' : '')" 
          >
        <div class="step-bubble">
          <div class="step-count">{{ index + 1 }}</div>
          <!-- <IconDone /> -->
        </div>
        <div class="step-label mt-20">
          {{ step }}
        </div>
        <div class="step-line">
          <div class="line-fill"></div>
        </div>
      </li>
    </ul>
  </div>
</template>


<style scoped>
.steps-container {
  width: 100%;
  margin: 0 auto;
  margin-left: 50px;
  margin-bottom: 30px;
}

.steps-list {
  display: flex;
  list-style: none;
  justify-content: space-between;
}

.step {
  display: flex;
  align-items: center;
  flex-grow: 1;
  height: 60px;
  position: relative;
}

.step-bubble {
  width: 35px;
  height: 35px;
  border-radius: 50%;
  background-color: var(--passive-color);
  transition: all 0.3s ease;
  display: flex;
  justify-content: center;
}

.line-fill {
  width: 0;
  background-color: var(--active-color);
  height: 5px;
  transition: all 0.3s ease;
}

.step-line {
  flex-grow: 1;
  height: 5px;
  background-color: var(--passive-color);
  position: relative;
}

.step-label {
  font-weight: 500;
  font-size: 18px;
  position: absolute;
}

.step:last-child .step-line {
  display: none;
}

.step-active .step-bubble,
.step-done .step-bubble {
  background-color: var(--active-color);
  width: 60px;
  height: 60px;
}

.step-count {
  color: white;
  font-size: 1.2rem;
  font-weight: bold;
  justify-content: center;
  align-content: center;
  /* display: none; */
}

.icon-done-icon {
  fill: gray;
  width: 30px;
  height: 30px;
  display: none;  
}

.step-done .step-done-icon {
  display: block;
}

.step-active .step-count {
  font-size: 1.5rem;
  display: block;
}

.step-done .line-fill {
  width: 100%;
}

.step-done-in-advance .line-fill {
  /* background-color: var(--active-color); */
  width: 50%;
}

.step-active .step-label,
.step-done .step-label {
  font-weight: 600;
  color: var(--active-color);
  opacity: 1;
}
</style>
