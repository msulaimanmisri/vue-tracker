<template>
  <div class="container my-5">
    <div class="col-10 col-md-6 mx-auto">
      <Header />
      <RemainingBalance :total="total" />
      <IncomeExpenses :income="+income"
        :expenses="+expenses" />
      <TransactionForm @transactionSubmitted="handleTransactionSumbitted" />
      <TransactionList :transactions="transactions"
        @transactionDeleted="handleTransactionDeleted" />
    </div>
  </div>
</template>

<script setup>
import Header from './components/Header.vue';
import RemainingBalance from './components/RemainingBalance.vue';
import IncomeExpenses from './components/IncomeExpenses.vue';
import TransactionForm from './components/TransactionForm.vue';
import TransactionList from './components/TransactionList.vue';
import { useToast } from 'vue-toastification';
import { ref, computed } from 'vue';

const toast = useToast();

const transactions = ref([
  { id: 1, text: 'Elaun Kelas Design', amount: 950.00 },
  { id: 2, text: 'Beli Nasi Abe', amount: -30.00 },
  { id: 3, text: 'Beli Kopi Latte', amount: -10.50 },
]);

// Dapatkan total kesemua duit keluar-masuk
const total = computed(() => {
  return transactions.value.reduce((accumulator, transaction) => {
    return accumulator + transaction.amount
  }, 0);
});

// Dapatkan total income
const income = computed(() => {
  return transactions.value.
    filter((transaction) => transaction.amount > 0)
    .reduce((accumulator, transaction) => {
      return accumulator + transaction.amount
    }, 0).toFixed(2);
});

// Dapatkan total expenses
const expenses = computed(() => {
  return transactions.value.
    filter((transaction) => transaction.amount < 0)
    .reduce((accumulator, transaction) => {
      return accumulator + transaction.amount
    }, 0).toFixed(2).replace(/^-/, '');;
});

// Add transaction
const handleTransactionSumbitted = (transactionData) => {
  transactions.value.push({
    id: generateUniqueId(),
    text: transactionData.transactionDetails,
    amount: transactionData.transactionAmount
  });

  console.log(generateUniqueId());
}

// Generate Unique ID
const generateUniqueId = () => {
  return Math.floor(Math.random() * 10000000);
}

// Handle transaction delete
const handleTransactionDeleted = (id) => {
  transactions.value = transactions.value.filter((transaction) => transaction.id !== id);
  toast.success('Transaction has been deleted!');
}
</script>
