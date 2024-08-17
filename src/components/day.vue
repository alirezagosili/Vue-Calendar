<script setup>
import { computed } from 'vue';
import dayjs from 'dayjs';

const props = defineProps({
    day: {
        type: Object,
    },
    month:{
        type: Object,
    }
})
const isWeekend = computed(() => props.day.format('ddd') === 'Sat' || props.day.format('ddd') === 'Sun')
const isToday = computed(() => 
    dayjs().isSame(props.day, 'day')
)
const notInMonth = computed(() => !props.month.isSame(props.day, 'month'))
    


</script>


<template>
    <div class="calendar-days">
        <div :class="['day-item', { isToday, isWeekend, notInMonth}]">
            {{ day.format("D") }}
        </div>
    </div>
</template>


<style>
.calendar-days{
    width: calc(100% / 7);
    padding: 0.5rem;
    flex-basis: calc(100% / 7);
    flex-grow: 0;
    flex-shrink: 1;
}
.isToday {
    background-color: aqua;
    color: white;
}
.isWeekend {
    
    color: red;
}
.day-item {
    border: 1px solid black;
    border-radius: 100px;
}
.notInMonth {
    opacity: 0.5;
}
</style>