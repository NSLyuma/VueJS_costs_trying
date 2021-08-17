<template>
  <div id="app">
    <header>My personal costs</header>
    <AddPaymentForm @addNewItem="addItem" />
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
      paymentsList: {},
    };
  },
  methods: {
    fetchData() {
      return {
        1: [
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
        2: [
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
        3: [],
      };
    },
    addItem(newItem) {
      //-----------
      // //массив из номеров страниц
      // let pagesArr = Object.keys(this.paymentsList);
      // //номер последней страницы
      // let lastPageNumber = pagesArr[pagesArr.length - 1];
      // //массив из объектов, которые содержатся в последней странице paymentsList
      // let lastPageData = this.paymentsList[`${Number(lastPageNumber)}`];

      // if (lastPageData.length < 5) {
      //   lastPageData.push(newItem);
      // } else {
      //   lastPageNumber++;
      //   lastPageData = this.paymentsList[`${lastPageNumber}`] = [];
      //   lastPageData.push(newItem);
      // }
      //-------------
      console.log(this.paymentsList);
      this.paymentsList[3].push(newItem);
    },
  },
  computed: {
    numberOfPages() {
      return Object.keys(this.paymentsList);
    },
    totalValue() {
      let sum = 0;
      //перебор объекта по ключам
      for (let page in this.paymentsList) {
        //вычисление суммы каждой страницы
        let preSum = this.paymentsList[page].reduce(
          (acc, cur) => (acc += cur.value),
          0
        );
        //вычисление общей суммы
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
