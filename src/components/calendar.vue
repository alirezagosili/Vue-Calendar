<script setup>
import Day from "@/components/day.vue";
import dayjs from "dayjs";
import Weekdays from "@/components/weekdays.vue";
import Header from "@/components/header.vue";
import { computed, ref } from "vue";

const currentDay = ref(dayjs());

const daysInMonth = computed(() => {
    return [
        ...Array(
            currentDay.value
                .startOf("month")
                .diff(currentDay.value.startOf("month").startOf("week"), "day")
        )
            .fill(currentDay.value.startOf("month").startOf("week"))
            .map((date, index) => date.add(index, "day")),
        ...Array(currentDay.value.daysInMonth())
            .fill()
            .map((_, i) => currentDay.value.startOf("month").add(i, "day")),
        ...Array(
            currentDay.value
                .endOf("month")
                .endOf("week")
                .diff(currentDay.value.endOf("month"), "day")
        )
            .fill(currentDay.value.add(1, "month").startOf("month"))
            .map((date, index) => date.add(index, "day")),
    ];
});
const goNextMonth = () => {
    currentDay.value = currentDay.value.add(1, "month");
};
const goPrevMonth = () => {
    currentDay.value = currentDay.value.subtract(1, "month");
};
</script>

<template>
    <Header :currentDay @next="goNextMonth" @prev="goPrevMonth" />

    <Weekdays />
    <div class="calendar-container">
        <Day v-for="day in daysInMonth" :key="day" :day :month="currentDay" />
    </div>
</template>

<style>
.calendar-container {
    display: flex;
    width: 100%;
    flex-wrap: wrap;
    text-align: center;
}
</style>
