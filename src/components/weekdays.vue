<script setup>
const daysOfWeek = ['Sun', 'Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat'];

</script>
<template>
    <div class="day-names-container">
        <span class="day-name" v-for="dayName in daysOfWeek" :key="dayName"> {{ dayName }} </span>
    </div>
</template>
<style scoped>
.day-names-container {
    background-color: darkslategray;
    color: white;
    display: flex;
    width: 100%;
    gap:1rem;
    justify-content: space-between;
    text-align: center;
}
.day-name{
    padding: 0.5rem;
    width: calc(100% / 7);
    padding: 0.5rem;
    flex-basis: calc(100% / 7);
    flex-grow: 0;
    flex-shrink: 1;

}
</style>