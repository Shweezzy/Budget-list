<template>
  <div class="total-value">
    <div v-if="total == 0">Total balance: {{ total }}</div>
    <div v-else-if="total > 0" :style="{ color: 'green' }">
      Total balance: {{ total }}
    </div>
    <div v-else-if="total" :style="{ color: 'red' }">
      Total balance: {{ total }}
    </div>
  </div>
</template>

<script>
export default {
  name: "TotalBalance",
  props: {
    total: {
      type: Number,
      default: 0
    }
  },
  data: () => ({
    color: "black"
  })
};
</script>

<style scoped>
.total-value {
  font-size: 26px;
  text-transform: uppercase;
  opacity: 0.7;
}
</style>
