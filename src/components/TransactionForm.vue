<template>
    <div class="mt-5">
        <h4 class="fs-5">Enter Your Transaction :</h4>

        <form id="transaction-form"
            class="card card-body form-group shadow-sm rounded-3 p-4"
            @submit.prevent="onSubmit">

            <div id="expenses-details">
                <label for="details"
                    class="form-label"> Details </label>

                <input type="text"
                    id="details"
                    name="details"
                    class="form-control text-muted"
                    v-model="transactionDetails">
            </div>

            <div id="expenses-amount"
                class="my-3">
                <label for="amount"
                    class="form-label"> Amount </label>

                <input type="number"
                    id="amount"
                    name="amount"
                    class="form-control text-muted"
                    v-model="transactionAmount">

                <span class="form-text text-danger">** Use dash (-) if you wanted to add expense. By default this input
                    field will add Income</span>
            </div>

            <div id="submitButton"
                class="mt-3">
                <button class="btn btn-primary"
                    type="submit">Add Transaction</button>
            </div>

        </form>

    </div>
</template>

<script setup>
import { ref } from 'vue';
import { useToast } from 'vue-toastification';

const transactionDetails = ref('');
const transactionAmount = ref('');
const toast = useToast();

const emit = defineEmits(['transactionSubmitted']);

const onSubmit = () => {
    if (!transactionDetails.value || !transactionAmount.value) {
        toast.error('Anda perlu isi Details & Amount!');
        return;
    }

    const transactionData = {
        transactionDetails: transactionDetails.value,
        transactionAmount: parseFloat(transactionAmount.value)
    }

    emit('transactionSubmitted', transactionData);

    transactionDetails.value = '';
    transactionAmount.value = '';

    toast.success('Your transaction has been recorded!');
}
</script>

<style scoped>
.card {
    border: 2px dashed rgb(56, 142, 195)
}
</style>