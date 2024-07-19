<template>
    <Card>
        <CardHeader class="px-4 pt-4 pb-4">
            <div class="flex justify-between items-center">
                <p> {{ card.title }}</p>
                <Badge class="bg-green-300"> {{ "+" + card.progression + "%" }}</Badge>
            </div>
        </CardHeader>
        <CardContent class="flex justify-end items-center px-4 pt-0 pb-2 border-b">
            <div class="text-[48px] font-[800]">
                <span class="text-neutral-300">$</span>
                <span>{{ card.amount }}</span>
            </div>
        </CardContent>
        <CardFooter class="flex gap-2 item-senter justify-between px-2 py-2">
            
            <Icon size="25" :name="card.icon" color="black"/>
            <p class="grow text-xs">{{ card.description }}</p>
            <Button varient="outline">
                {{ card.label }}
            </Button>
        </CardFooter>
    </Card>
</template>

<script setup lang="ts">
import { Card, CardContent, CardDescription, CardFooter, CardHeader, CardTitle, } from '@/components/ui/card';
import { Badge } from '@/components/ui/badge'
const props = defineProps(["card"]);
</script>
