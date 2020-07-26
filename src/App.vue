<template>
  <div id="app">
    <!-- <BudgetListItem :list='list' @deleteItem='onDeleteItem' /> -->
    <Forms @submitForm="onFormSubmit" />
    <TotalBalance :total="TotalBalance" />
    <BudgetList :list="list" @deleteItem="onDeleteItem" />
  </div>
</template>

<script>
import BudgetList from "@/components/BudgetList";
import TotalBalance from "@/components/TotalBalance";
import Forms from "@/components/Forms";
// import BudgetListItem from "@/components/BudgetListItem"

export default {
  name: "app",
  components: {
    BudgetList,
    TotalBalance,
    Forms
    // BudgetListItem,
  },
  data: () => ({
    list: {
      1: {
        type: "income",
        value: 100,
        comments: "Some comments",
        id: 1
      },
      2: {
        type: " outcome",
        value: -50,
        comments: "Some comments",
        id: 2
      }
    }
  }),
  computed: {
    TotalBalance() {
      return Object.values(this.list).reduce(
        (acc, item) => acc + item.value,
        0
      );
    }
  },
  methods: {
    onDeleteItem(id) {
      this.$delete(this.list, id);
    },
    onFormSubmit(data) {
      const newObj = {
        ...data,
        id: String(Math.random())
      };

      this.$set(this.list, newObj.id, newObj);
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 10px;
}
</style>
