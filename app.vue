<template>
  <StepsContainer ref="StepsContainerRef" :count="count">
    <template #step1>
      <div>
        <h1>Step 1</h1>
        <button @click="next">Next</button>
    <button @click="prev">Prev</button>
      </div>
    </template>
    <template #step2>
      <h1>Step 2</h1>
    </template>
    <template #step3>
      <h1>Step 3</h1>
    </template>
    <template #step4>
      <h1>Step 3</h1>
    </template>


    
  </StepsContainer>

  
</template>



<script setup>
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