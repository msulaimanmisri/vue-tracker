<template>
    <div class="mt-5">
        <h4 class="fs-5">History</h4>

        <div class="row mt-3">
            <div class="col">
                <div v-for="transaction in transactions"
                    :key="transaction.id"
                    class="card card-body shadow-sm border-0 rounded-3 mb-2 position-relative">
                    <button class="position-absolute border-0 top-0 start-100 translate-middle badge rounded-5 bg-danger"
                        id="deleteButton"
                        @click="deleteTransaction(transaction.id)">
                        Delete
                    </button>

                    <span class="text-form text-muted fst-italic">
                        <span :class="transaction.amount < 0 ? 'text-danger' : 'text-success'">
                            {{ transaction.amount < 0
                                ? '-'
                                : '+'
                            }}
                                {{
                                    transaction.text
                                }}
                                </span>
                                <h4 class="mt-2">{{ transaction.amount < 0
                                    ? 'RM '
                                    +
                                    Math.abs(transaction.amount).toLocaleString(undefined,
                                        {
                                            minimumFractionDigits:
                                                2,
                                            maximumFractionDigits:
                                                2
                                        })
                                    : 'RM '
                                    +
                                    transaction.amount.toLocaleString(undefined,
                                        {
                                            minimumFractionDigits:
                                                2,
                                            maximumFractionDigits:
                                                2
                                        })
                                }}</h4>
                        </span>
                </div>
            </div>
        </div>
    </div>
</template>


<script setup>
// Props
import { defineProps } from 'vue';

const emit = defineEmits([
    'transactionDeleted'
]);

const props = defineProps({
    transactions: {
        type: Array,
        required: true
    },
})

const confirmDelete = () => {
    return confirm('Pasti ke nak delete?');
}

const deleteTransaction = (id) => {
    if (confirmDelete()) {
        emit('transactionDeleted', id);
    };
}


</script>


<style scoped>
#deleteButton {
    opacity: 0;
    transition: opacity 0.3s ease;
}

.card:hover #deleteButton {
    opacity: 1;
}
</style>