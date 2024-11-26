<script setup>
  import { defineProps, ref } from 'vue';

  const props = defineProps({
    data: Object,
  })

  props.data.currentStep--;

  const data = ref(props.data);
</script>


<template>
  <div class="item">
    <i>
      <slot name="icon"></slot>
    </i>
    <div class="details">
      <p class="bg-gray-200 rounded-lg text-lg font-bold text-black-400 text-center">
       Step Progress
      </p>
      <slot></slot>
    </div>
  </div>
</template>
