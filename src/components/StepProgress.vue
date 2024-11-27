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
    "--passive-color": data.value.passiveColor,
  };
});
</script>


<template>
  <div class="steps-container" :style="cssStyle">
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

<style scoped>
  .steps-container{
    width: 95%;
    margin: 0 auto;
  }

  .steps-list{
    display: flex;
    list-style: none;
  }
  .step{
    display: flex;
    align-items: center;
    flex-grow: 1;
    max-width: 100%;
    position: absolute;
    height: 60px;
  }

  .step-bubble{
    width: 35px;
    height: 35px;
    border-radius: 50%;
    background-color: var(--passive-color);
    transition:all 0.3s ease;
     display: flex;
    justify-content: center;
  }

  .step-line{
    width: 100%;
    height: 5px;
    background-color: var(--passive-color);
    top: 50%;
    left: 0;
    transform: translate(-50%)
  }
</style>