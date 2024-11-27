<script setup>
import { defineProps, ref, computed } from "vue";

const props = defineProps({
  data: Object,
});

props.data.currentStep--;

const data = ref(props.data);

// const data = ref({ ...props.data });
// data.value.currentStep--;


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
      <li class="step" v-for="(step, index) in data.steps" :key="index" :class="(index == data.currentStep )? '--stepActive' : ''">
        <!-- <li v-for="(step, index) in data.value.steps" :key="index" :class="{ '--stepActive': index === data.value.currentStep }"> -->

        <div class="step-bubble"></div>
        <div class="step-line">
          <div class="line-fill"></div>
        </div>
      </li>
    </ul>
  </div>
</template>
<!-- 
<style scoped>
  .steps-container{
    width: 100%;
    margin: 0 auto;
  }

  .steps-list{
    display: flex;
    list-style: none;
  }

  .step:last-child{
    max-width: 60px;
  }
  .step{
    display: flex;
    align-items: center;
    max-width: 100%;
    position: relative;
    flex-grow: 1;
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
    position: absolute;
    top: 50%;
    left: 0;
    transform: translate(-50%);
    z-index: -10;
  }

  .step:last-child .step-line{
    display: none;
  }
</style> -->



<style scoped>
.steps-container {
  width: 100%;
  margin: 0 auto;
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

.step-line {
  flex-grow: 1;
  height: 5px;
  background-color: var(--passive-color);
  position: relative;
}

.step:last-child .step-line {
  display: none;
}
</style>
