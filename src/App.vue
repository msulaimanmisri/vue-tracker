<template>
  <div class="container my-5">
    <div class="col-10 col-md-6 mx-auto">
      <Header />
      <RemainingBalance :total="total" />
      <IncomeExpenses />
      <addTransaction />
      <TransactionList :transactions="transactions" />
    </div>
  </div>
</template>

<script setup>
import Header from './components/Header.vue';
import RemainingBalance from './components/RemainingBalance.vue';
import IncomeExpenses from './components/IncomeExpenses.vue';
import AddTransaction from './components/AddTransaction.vue';
import TransactionList from './components/TransactionList.vue';

import { ref, computed } from 'vue';

const transactions = ref([
  { id: 1, text: 'Beli Nasi Abe', amount: -20.00 },
  { id: 2, text: 'Beli Kopi Latte', amount: -10.50 },
  { id: 2, text: 'Elaun Kelas Design', amount: 150.00 },
]);

const total = computed(() => {
  return transactions.value.reduce((accumulator, transaction) => {
    return accumulator + transaction.amount
  }, 0);
})
</script>
