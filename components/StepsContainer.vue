<template>
    <div class=" w-full h-screen flex">
        <div class="m-auto w-full vff-animate fade-to-up" >
            <transition :name="animation">
                <slot :name="currentStep"></slot>
            </transition>
        </div>

      <button @click="nextStep">Next</button>
        <button @click="prevStep">Prev</button>
    </div>
</template>
  


<script setup>

const props = defineProps({
    count: {
        type: Number,
        required: true,
    },
});

const animation = ref('slide-down');
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


onMounted(() => {
    animation.value = 'slide-up';
});

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
    transition: all 0.5s ease;
}

.slide-up-enter-from {
       opacity: 0;
        transform: translate3d(0, 90px, 0);
}

.slide-up-enter-to {
    opacity: 1;
        transform: none;
}

.slide-up-leave-active {
    transition: all 0s ease;
}

.slide-up-leave-from {
  opacity: 0;
}

.slide-up-leave-to {
    
    display: initial;
    position: absolute;
    top: -99999px;
    left: -99999px
    
}


.side-down-enter-active {
    transition: all 0.5s ease;
}

.side-down-enter-from {
        opacity: 0;
        transform: translate3d(0, -90px, 0);
}

.side-down-enter-to {
       opacity: 1;
        transform: none;
}

.side-down-leave-active {
    transition: all 0s ease;
}

.side-down-leave-from {
    transform: translateY(0);
}

.side-down-leave-to {
    display: initial;
    position: absolute;
    top: -99999px;
    left: -99999px
}




@keyframes fadeUp {
    0% {
        opacity: 0;
        transform: translate3d(0, 30px, 0);
    }
    100% {
        opacity: 1;
        transform: translate3d(0, -30px, 0);
    }
}


.fade-to-up {
    animation: fadeUp 0.6s ease forwards;
}

@keyframes flash {
    0%, 50%, 100% {
        opacity: 1;
    }
    25%, 75% {
        opacity: 0;
    }
}
         
.flash {
  animation: flash 0.5s ;
}

</style>