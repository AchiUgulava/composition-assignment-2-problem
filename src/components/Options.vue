<template>
    <header>
      <h1>Options API Expense Tracker</h1>
    </header>
    <section>
      <div>Available Funds: {{ availableFunds }}</div>
      <div>Total Expenses: {{ currentExpenses }}</div>
      <hr />
      <div>Funds left: {{ remainingFunds }}</div>
    </section>
    <section>
      <form @submit.prevent="addExpense">
        <div>
          <label for="amount">Amount</label>
          <input id="amount" type="number" v-model="enteredExpense" />
        </div>
        <button>Add Expense</button>
      </form>
    </section>
  </template>
  
  <script>
  export default {
    data() {
      return {
        availableFunds: 100,
        currentExpenses: 0,
        enteredExpense: 0,
      };
    },
    computed: {
      remainingFunds() {
        return this.availableFunds - this.currentExpenses;
      },
    },
    methods: {
      addExpense() {
        this.currentExpenses += this.enteredExpense;
      },
    },
    watch: {
      remainingFunds(val) {
        if (val < 0) {
          alert('You are broke!');
        }
      },
    },
  };
  </script>
  
  