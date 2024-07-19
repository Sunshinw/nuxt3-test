<script setup lang="ts">
import {
  AlertDialog,
  AlertDialogAction,
  AlertDialogCancel,
  AlertDialogContent,
  AlertDialogDescription,
  AlertDialogFooter,
  AlertDialogHeader,
  AlertDialogTitle,
  AlertDialogTrigger,
} from '@/components/ui/alert-dialog'

const {loading, open} = useHelpers();
const createProduct = async () => {
    try {
        loading.value = true
    } catch (error) {
        
    } finally{
        loading.value = false
        open.value = false
    }
}
</script>

<template>
  <AlertDialog :open="open">
    <AlertDialogTrigger>
        <Button @click="open = true ">
            Add a new product
        </Button>
    </AlertDialogTrigger>
    <AlertDialogContent>
      <AlertDialogHeader>
        <AlertDialogTitle> Create a new product</AlertDialogTitle>
        <Input placeholder=""/>
      </AlertDialogHeader>
      <AlertDialogFooter>
        <AlertDialogCancel @click="open = false">Cancel</AlertDialogCancel>
        <AlertDialogAction @click="createProduct()">Create</AlertDialogAction>
      </AlertDialogFooter>
    </AlertDialogContent>
  </AlertDialog>
</template>