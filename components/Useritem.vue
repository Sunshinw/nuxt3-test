<template>
    <div class="p-2 m-2 gap-3 border rounded flex item-center justify-start cursor-pointer hover:bg-neutral-200 transition">
        <div class="rounded-full w-10 h-10 bg-green-400 flex items-center justify-center font-sans text-[15px] text-white">{{ name[0] }}</div>
        <div>
            <p class="mb-0 font-bold text-black leading-1">{{ name }}</p>
            <p class="m-0">{{description}}</p>
        </div>
    </div>
    
</template>

<script setup>
const loading = ref(false)
const name = ref("xxxxxxxx xxxxxxxx")
const description = ref("xxxxxxxx xxxxxxxx")
</script>

