<template>
  <div id="app">
    <header>My personal costs</header>
    <PaymentsDisplay :list="paymentsList" />
    <div>Total value: {{ totalValue }}</div>
  </div>
</template>

<script>
import PaymentsDisplay from "./components/PaymentsDisplay.vue";
export default {
  name: "App",
  components: { PaymentsDisplay },
  data() {
    return {
      paymentsList: {},
    };
  },
  methods: {
    fetchData() {
      return {
        page1: [
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
        ],
        page2: [
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
        ],
      };
    },
  },
  computed: {
    numberOfPages() {
      return Object.keys(this.paymentsList);
    },
    totalValue() {
      let sum = 0;
      for (let page in this.paymentsList) {
        //перебор объекта по ключам
        let preSum = this.paymentsList[page].reduce(
          //вычисление суммы каждой страницы
          (acc, cur) => (acc += cur.value),
          0
        );
        sum += preSum;
      }
      return sum;
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
