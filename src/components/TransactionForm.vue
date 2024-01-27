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
                    class="form-control">
            </div>

            <div id="expenses-amount"
                class="my-3">
                <label for="amount"
                    class="form-label"> Amount </label>

                <input type="number"
                    id="amount"
                    name="amount"
                    class="form-control">
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

const onSubmit = () => {
    console.log('send');
}
</script>

<style scoped>
.card {
    border: 2px dashed rgb(56, 142, 195)
}
</style>