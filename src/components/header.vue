<script setup>
import { computed } from 'vue';

const props = defineProps ({
    currentDay:{
        type: Object
    }
})

const emits = defineEmits (["next","prev"])

const monthName = computed(() => {
    return props.currentDay.format("MMMM");
});

const goNextMonth = () => {
    emits("next")
};
const goPrevMonth = () => {
    emits("prev")
};
</script>
<template>
    <div class="header">
        <button @click="goPrevMonth"><</button>
        <div>{{ monthName }}</div>
        <button @click="goNextMonth">></button>
    </div>
</template>
<style>
.header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 10px;
}
</style>