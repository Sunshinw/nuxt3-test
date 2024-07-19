<template>
    <div>
        <highchart v-if="data.length > 0" :options="options"/>
    </div>
</template>

<script setup>
import { ref, computed, watch, onMounted } from 'vue';
const props = defineProps(["currentCategory", "data"]);

const categories = ref({
    today: [
        '00:00', '01:00', '02:00', '03:00', '04:00', '05:00', '06:00', 
        '07:00', '08:00', '09:00', '10:00', '11:00', '12:00', '13:00', 
        '14:00', '15:00', '16:00', '17:00', '18:00', '19:00', '20:00', 
        '21:00', '22:00', '23:00'
    ],
    week: ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday', 'Sunday'],
    year: [
        'January', 'February', 'March', 'April', 'May', 'June', 'July', 
        'August', 'September', 'October', 'November', 'December'
    ],
    month: []
});

const generateMonthDates = () => {
    const currentdate = new Date();
    const currentyear = currentdate.getFullYear();
    const currentmonth = currentdate.getMonth() + 1;
    const daysInMonth = new Date(currentyear, currentmonth, 0).getDate();
    const daysArray = [];

    for (let day = 1; day <= daysInMonth; day++) {
        const dayStr = day < 10 ? `0${day}` : `${day}`;
        const monthStr = currentmonth < 10 ? `0${currentmonth}` : `${currentmonth}`;
        daysArray.push(`${dayStr}-${monthStr}`);
    }

    categories.value.month = daysArray;
};

onMounted(() => {
    generateMonthDates();
});

watch(() => props.currentCategory, () => {
    options.value.xAxis.categories = categories.value[props.currentCategory];
});

const options = computed(() => ({
    chart: {
        type: 'line',
        animation: false,
    },
    title: {
        text: ''
    },
    xAxis: {
        gridLineColor: 'transparent',
        categories: categories.value[props.currentCategory]
    },
    yAxis: {
        gridLineColor: 'transparent',
        title: {
            text: ''
        }
    },
    plotOptions: {
        line: {
            marker: {
                enabled: false
            },
            dataLabels: {
                enabled: false
            },
            enableMouseTracking: true
        }
    },
    series: [{
        name: 'line',
        lineWidth: 4,
        color: {
            linearGradient: { y1: 0, y2: 0, y3: 0, y4: 0 },
            stops: [
                [0, 'rgba(252,176,69,1)'],
                [0.33, 'rgba(253,29,29,1)'],
                [0.66, 'rgba(131,58,180,1)'],
                [1, 'rgba(29,217,83,1)'],
            ]
        },
        data: props.data
    }]
}));
</script>

<style scoped>
/* Add any scoped styles if needed */
</style>
