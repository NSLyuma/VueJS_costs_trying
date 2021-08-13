<template>
  <div>
    <div v-for="(page, i) in list" :key="i">
      {{ i }}:
      <div v-for="item in page" :key="item.id">
        {{ item.id }}. {{ item.date }} {{ item.category }}
        {{ item.value }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "PaymentsDisplay",
  props: {
    list: {
      type: Object,
      default: () => {},
    },
  },
};
</script>