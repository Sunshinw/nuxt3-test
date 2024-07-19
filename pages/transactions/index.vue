<template>
    <div>
        <header class="flex items-start justify-between">
            <div class="grow">
                <p>All Your Transaction</p>
                <h1>Transaction</h1>
            </div>
        </header>
        <DataTable :columns="columns" :data="data"/>
    </div>
</template>

<script setup lang="ts">
import {onMounted,ref,h} from "vue";
import {columns} from "./columns.ts";
const data = ref<any>([]);
function generateRandomData(numOfObjects) {
    const statuses = ['active', 'inactive', 'pending'];

    const randomData = [];

    for (let i = 0; i < numOfObjects; i++) {
        const entry = {
            id: Math.floor(Math.random() * (9999 - 1000 + 1)) + 1000, // Random ID between 1000 and 9999
            amount: (Math.random() * (1000 - 10) + 10).toFixed(2), // Random amount between 10 and 1000 with 2 decimal places
            email: `${Math.random().toString(36).substring(2, 15)}@example.com`, // Random email
            status: statuses[Math.floor(Math.random() * statuses.length)], // Random status
        };
        randomData.push(entry);
    }

    return data.value = randomData;
}

onMounted(() => {
    generateRandomData(10)
})
</script>

<style scoped>

</style>