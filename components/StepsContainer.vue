<template>
    <div class=" w-full h-screen flex">
        <div class="m-auto">
            <transition :name="animation">
                <slot :name="currentStep"></slot>
            </transition>
        </div>

      

    </div>
</template>
  


<script setup>

const props = defineProps({
    count: {
        type: Number,
        required: true,
    },
});

const animation = ref('slide-up');
const currentStep = ref('step1');
const index = ref(1);
const nextStep = () => {
    animation.value = 'slide-up';
    if (index.value < props.count) {
        index.value++;
        currentStep.value = `step${index.value}`;
    }


    
   
};

const prevStep = () => {
    animation.value = 'side-down';
    if (index.value > 1) {
        index.value--;
        currentStep.value = `step${index.value}`;
    }
    

    
};

//get slots number
const slots = ref(0);

onMounted(() => {
});




defineExpose({
    nextStep,
    prevStep,
});
</script>



<style>
.slide-up-enter-active {
    transition: all 0.3s ease;
}

.slide-up-enter-from {
    transform: translateY(100%);
}

.slide-up-enter-to {
    transform: translateY(0);
}

.slide-up-leave-active {
    transition: all 0.3s ease;
}

.slide-up-leave-from {
    transform: translateY(0);
}

.slide-up-leave-to {
    transform: translateY(-100%);
}


.side-down-enter-active {
    transition: all 0.3s ease;
}

.side-down-enter-from {
    transform: translateY(-100%);
}

.side-down-enter-to {
    transform: translateY(0);
}

.side-down-leave-active {
    transition: all 0.3s ease;
}

.side-down-leave-from {
    transform: translateY(0);
}

.side-down-leave-to {
    transform: translateY(100%);
}
</style>