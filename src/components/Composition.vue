<script setup>
import { ref, computed, watch } from 'vue';
const balance = ref({
    availableFunds: 100,
    currentExpenses: 0,
    enteredExpense: 0,
});
const remainingFunds = computed(() => {
     return balance.value.availableFunds - balance.value.currentExpenses 
});
const addExpense = () => {
    balance.value.currentExpenses += balance.value.enteredExpense;
};
watch(remainingFunds,()=>{
    remainingFunds.value<0&&alert('you are broke!');
})
</script>

<template>
    <header>
        <h1>Composition API Expense Tracker</h1>
    </header>
    <section>
        <div>Available Funds: {{ balance.availableFunds }}</div>
        <div>Total Expenses: {{ balance.currentExpenses }}</div>
        <hr />
        <div>Funds left: {{ remainingFunds }}</div>
    </section>
    <section>
        <form @submit.prevent="addExpense">
            <div>
                <label for="amount">Amount</label>
                <input id="amount" type="number" v-model="balance.enteredExpense" />
            </div>
            <button>Add Expense</button>
        </form>
    </section>
</template>
  
