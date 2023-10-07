<template>
  <StepsContainer ref="StepsContainerRef" :count="count">
    <template #step1>
     <Step1 @nextStep="next"/>
    </template>
    <template #step2>
      <Step2 @nextStep="next"/>
    </template>
    <template #step3>
      <Step2 @nextStep="next"/>
    </template>
    <template #step4>
       <Step2 @nextStep="next"/>
    </template>



  </StepsContainer>
</template>



<script setup>

import Step1 from '@/components/steps/Step1.vue';
import Step2 from '@/components/steps/Step2.vue';


const count = 4; // number of steps


import StepsContainer from '@/components/StepsContainer.vue';
const StepsContainerRef = ref(null);

const next = () => {
  StepsContainerRef.value.nextStep();
}

const prev = () => {
  StepsContainerRef.value.prevStep();
}

</script>