<template>
    <div class="mt-4">
        <h4 class="fs-5">Your Balance :</h4>
        <h2 class="display-3 fw-bold"
            id="balance">RM {{ total.toLocaleString(undefined,
                {
                    minimumFractionDigits:
                        2,
                    maximumFractionDigits:
                        2
                }) }}</h2>
    </div>
</template>

<script setup>
import { defineProps } from 'vue';

const props = defineProps({
    total: {
        type: Number,
        required: true
    },
})
</script>
