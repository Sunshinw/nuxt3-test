<template>
    <div>
    <header class="flex items-center gap-2 p-4 hover:scale-[101%] transition cursor-pointer"> 
        <Logo/>
        <p class="font-bold">Nuxt-Finance</p>
    </header>    
    <div class="px-4 grow">
        <div class="grid gap-4">
            <div v-for='(item, index) in items' :key='index' class="flex items-center gap-2 px-2 py-1 transition cursor-pointer hover:bg-neutral-100">
            <Icon size="20" :name="item.icon" color="black"/> 
            <span>{{ item.title }}</span>
        </div>
        </div>
    </div>

    </div>
</template>

<script setup>
const items = ref([
    {
        title: "Overview",
        path: "/overview",
        icon: "material-symbols:overview-key-rounded"
    }, {
        title: "Transactions",
        path: "/transactions",
        icon: "majesticons:money-line"
    }, {
        title: "Account",
        path: "/account",
        icon: "mdi:account"
    }, {
        title: "Contacts",
        path: "/contacts",
        icon: "material-symbols:contacts"
    }, {
        title: "Settings",
        path: "/settings",
        icon: "material-symbols:settings"
    },
    
])
</script>

<style scoped>

</style>