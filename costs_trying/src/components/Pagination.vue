<template>
  <div class="pages-box">
    <button @click="onClick(currentPage - 1)">&#60;</button>
    <div v-for="page in numberOfPages" :key="page">
      <div class="page" @click="onClick(page)">{{ page }}</div>
    </div>
    <button @click="onClick(currentPage + 1)">&#62;</button>
  </div>
</template>

<script>
export default {
  name: "Pagination",
  props: {
    listLength: Number,
    currentPage: Number,
    numberOfItems: Number,
  },
  methods: {
    onClick(page) {
      if (page < 1 || page > this.numberOfPages) return;
      else {
        this.$emit("onClick", page);
      }
    },
  },
  computed: {
    numberOfPages() {
      return Math.ceil(this.listLength / this.numberOfItems);
    },
  },
};
</script>

<style scoped>
.pages-box {
  display: flex;
}

.page {
  margin-right: 10px;
  margin-left: 10px;
  border: 1px solid black;
  padding: 5px;
  cursor: pointer;
}
</style>