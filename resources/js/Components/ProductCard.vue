<script setup>
import PrimaryButton from '@/Components/PrimaryButton.vue';
import { useForm } from '@inertiajs/inertia-vue3';
    const props = defineProps({
        product: {
            type: Object,
            default: null,
        }
    })

    const form =useForm({
        product: props.product,
        qty: 1
    })

    const submit = () => {
        form.post(route('cart.add'))
    }
    
</script>
<template>
<form @submit.prevent="submit">
    <div class="w-72h-80 flex flex-col shadow hover:shadow-lg rounded">
        <img class="max-h-44" :src="product.image" alt="">
        <div class="flex-1 mt-2 px-4">
            <p class="font-bold"> {{product.name}}</p>
        </div>
        <div class="px-4 pb-2 flex justify-between">
            <div class ="flex gap-2 items-center">
                <span>qty:</span>
                <input type="number" class="border border-gray-200 rounded focus:outline-none w-20">
        </div>
            <p>{{product.price}}</p>
        </div>
        <div class="px-4 pb-2 mt-4">
            <PrimaryButton type="submit" class="w-full items-center flex justify-center">Add to cart</PrimaryButton>
        </div>
    </div>
</form>
</template>