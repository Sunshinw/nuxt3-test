<template>
    <div class="grid gap-4 w-full">
        <header class="flex items-start justify-between">
            <div class="grow">
                <p>Welcome ...</p>
                <h1>Dashboard</h1>
            </div>
            <ProductNew/>
        </header>
        <main class="grid gap-4">
            <Tabs default-value="Today" @click="setCategory">
                <TabsList class="w-[100%]">
                    <TabsTrigger v-for='(item, index) in list' :key='index' :value="item.title">
                        {{ item.title }}
                    </TabsTrigger>
                </TabsList>
                <TabsContent class="w-[100%]" v-for='(item, index) in list' :key='index' :value="item.title">
                    <Chart v-if="data.length > 0" :currentCategory="currentCategory" :data="data"/>
                </TabsContent>
            </Tabs>
        </main>
        <footer>
            <div class="grid gap-4 lg:grid-cols-3">
                <Card v-for='(item, index) in cards' :key='index' :card="item">

                </Card>
            </div>
        </footer>
    </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import { Tabs, TabsContent, TabsList, TabsTrigger } from '@/components/ui/tabs';
import Chart from '@/components/Chart.vue';  // Ensure the correct path to Chart.vue

const loading = ref(false);
let data = ref([]);
const list = [
    { title: "Today", component: resolveComponent("TabsToday") },
    { title: "Week", component: resolveComponent("TabsToday") },
    { title: "Month", component: "<div>Month</div>" },
    { title: "Year", component: "<div>Year</div>" }
];
let currentCategory = ref('today');

const generateRandomData = (number = 24) => {
    let values = [];
    for (let i = 0; i < number; i++) {
        values.push(Math.floor(Math.random() * 100));
    }
    data.value = values;
    return values;
};

const setCategory = (e) => {
    let v = e.target.innerText.toLowerCase();
    currentCategory.value = v;
    switch (v) {
        case 'today':
            generateRandomData(24);
            break;
        case 'week':
            generateRandomData(7);
            break;
        case 'month':
            generateRandomData(31);
            break;
        case 'year':
            generateRandomData(12);
            break;
    }
    console.log(v);
};

const cards = [
    {
        title: "Sales",
        progression: 12,
        amount: 84.44,
        label: "View Sales",
        description: "Sales of March 2024",
        icon: "mingcute:calendar-3-fill"
    },
    {
        title: "Refund",
        progression: 12,
        amount: 84.44,
        label: "View Refund",
        description: "Payouts of March 2024",
        icon: "ri:refund-2-fill"
    },
    {
        title: "Payouts",
        progression: 12,
        amount: 84.44,
        label: "View Payouts",
        description: "Payouts of March 2024",
        icon: "fluent-mdl2:money"
    }
]

onMounted(() => {
    generateRandomData();
});
</script>

<style scoped>
/* Add any scoped styles if needed */
</style>
