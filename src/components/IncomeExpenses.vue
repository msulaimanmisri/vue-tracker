<template>
    <div class="row my-4">
        <div class="col">
            <div class="card card-body border-0 rounded-3 shadow-sm">
                <span class="text-muted mb-3">Income</span>
                <h5 class="text-success">+ MYR {{ income }}</h5>
            </div>
        </div>

        <div class="col">
            <div class="card card-body border-0 rounded-3 shadow-sm">
                <span class="text-muted mb-3">Expense</span>
                <h5 class="text-danger">- MYR {{ expenses }}</h5>
            </div>
        </div>
    </div>
</template>

<script setup>
import { defineProps } from 'vue';

const props = defineProps({
    income: {
        type: Number,
        required: true
    },
    expenses: {
        type: Number,
        required: true
    }
});
</script>