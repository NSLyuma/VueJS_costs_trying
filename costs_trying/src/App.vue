<template>
  <div id="app">
    <header>My personal costs</header>
    <AddPaymentForm @addItem="addNewData" />
    <PaymentsDisplay :list="paymentsList" />
    <div>Total value: {{ totalValue }}</div>
  </div>
</template>

<script>
import AddPaymentForm from "./components/AddPaymentForm.vue";
import PaymentsDisplay from "./components/PaymentsDisplay.vue";
export default {
  name: "App",
  components: { PaymentsDisplay, AddPaymentForm },
  data() {
    return {
      paymentsList: [],
    };
  },
  methods: {
    fetchData() {
      return [
        {
          id: 1,
          date: "13.08.2021",
          category: "Food",
          value: 100,
        },
        {
          id: 2,
          date: "13.08.2021",
          category: "Food",
          value: 200,
        },
        {
          id: 3,
          date: "13.08.2021",
          category: "Food",
          value: 300,
        },
        {
          id: 4,
          date: "13.08.2021",
          category: "Food",
          value: 400,
        },
        {
          id: 5,
          date: "13.08.2021",
          category: "Food",
          value: 500,
        },
        {
          id: 6,
          date: "13.08.2021",
          category: "Food",
          value: 100,
        },
        {
          id: 7,
          date: "13.08.2021",
          category: "Food",
          value: 200,
        },
        {
          id: 8,
          date: "13.08.2021",
          category: "Food",
          value: 300,
        },
        {
          id: 9,
          date: "13.08.2021",
          category: "Food",
          value: 400,
        },
        {
          id: 10,
          date: "13.08.2021",
          category: "Food",
          value: 500,
        },
      ];
    },
    addNewData(newItem) {
      this.paymentsList.push(newItem);
    },
  },
  computed: {
    totalValue() {
      return this.paymentsList.reduce((acc, cur) => (acc += cur.value), 0);
    },
  },
  created() {
    this.paymentsList = this.fetchData();
  },
};
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>
