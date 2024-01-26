<template>
    <div class="mt-4">
        <h4 class="fs-5">Your Transaction :</h4>
        <form id="transaction-form"
            class="form-group">

            <div id="expenses-details">
                <label for="details"
                    class="form-label"> Details </label>

                <input type="text"
                    id="details"
                    name="details"
                    class="form-control">
            </div>

            <div id="expenses-amount"
                class="mt-3">
                <label for="amount"
                    class="form-label"> Amount </label>

                <input type="number"
                    id="amount"
                    name="amount"
                    class="form-control">
            </div>
        </form>
    </div>
</template>