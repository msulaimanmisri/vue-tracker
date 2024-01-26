<template>
  <div class="container my-5">
    <div class="col-6 mx-auto">
      <Header />
      <Hero />
      <IncomeExpenses />
      <addTransaction />
      <TransactionList :transactions="transactions" />
    </div>
  </div>
</template>

<script setup>
import Header from './components/Header.vue';
import Hero from './components/Hero.vue';
import IncomeExpenses from './components/IncomeExpenses.vue';
import AddTransaction from './components/AddTransaction.vue';
import TransactionList from './components/TransactionList.vue';

import { ref } from 'vue';

const transactions = ref([
  { id: 1, text: 'Beli Nasi Abe', amount: -20.00 },
  { id: 2, text: 'Beli Kopi Latte', amount: -12.50 },
  { id: 2, text: 'Elaun Kelas Design', amount: 950 },
]);
</script>
