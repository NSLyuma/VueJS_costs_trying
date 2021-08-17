<template>
  <div>
    <input type="date" v-model="date" />
    <input type="text" placeholder="Category" v-model="category" />
    <input type="text" placeholder="Value" v-model="value" />
    <button @click="addNewData">Add new cost</button>
  </div>
</template>

<script>
export default {
  name: "AddPaymentForm",
  data() {
    return {
      id: "",
      date: "",
      category: "",
      value: "",
    };
  },
  methods: {
    addNewData() {
      const { category, value } = this;
      const data = {
        id: "",
        date: this.date || this.getCurrentDate,
        category,
        value,
      };
      this.$emit("addNewItem", data);
    },
  },
  computed: {
    getCurrentDate() {
      const today = new Date();
      const d = today.getDate();
      const m = today.getMonth() + 1;
      const y = today.getFullYear();
      return `${d}.${m}.${y}`;
    },
  },
};
</script>